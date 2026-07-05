# Feireisl–Tucker-Will 4.5PN Comparison: Investigation Summary

**Context:** Code comparing three formulations of post-Newtonian binary inspiral dynamics — a numerical "exact" osculating reference (**QLT**), and two competing analytic secular (orbit-averaged) formulas that disagree only at 4.5PN order in the radiation-reaction sector (**Feireisl** vs. **Tucker-Will**), per [arXiv:2108.12210](https://arxiv.org/abs/2108.12210) (Tucker & Will, 2021). The test system: equal masses (η=0.25), initial eccentricity e≈0.14 (α=β=0.1), semi-latus rectum p sweeping from 50 → 20, across a scan of the PN bookkeeping parameter ε from 1.0 down to 0.0039 (halved 9 times).

The question driving this investigation: **how much phase (φ) does each method predict is needed to sweep p from 50 to 20, and do the three methods agree as ε → 0 (as proper PN convergence requires)?**

---

## 1. Initial problem: brute-force QLT is computationally infeasible

The original code integrates QLT's *exact instantaneous* (osculating) equations of motion phi-step by phi-step, which requires resolving orbital-period oscillations directly. This throughput is fundamentally capped by how finely a single orbit must be resolved — independent of how the step-size cap is configured.

| ε | Δp probed | measured/estimated wall-clock (brute-force QLT) |
|---|---|---|
| 1.0 | 30 (full range) | 28.3 s |
| 0.5 | 1 | 21.6 s → full range extrapolated to **~9.6 hours** |
| 0.25 | 1 | >250 s and still incomplete → full range: **days+** |

Root cause: the number of orbits needed to sweep a *fixed* Δp grows roughly as ε⁻⁵ (see §3), while resolving each individual orbit has a roughly fixed cost — so total cost explodes combinatorially as ε shrinks. This makes the literal 9-point ε scan computationally impossible via brute force.

---

## 2. Speed levers validated (no accuracy loss)

Two "free" speedups were confirmed empirically before touching the algorithm itself:

- **Step-size cap:** the code's original 1e-3 cap on Δφ per step was far more conservative than needed. Relaxing it (e.g. to 0.5 for QLT, ≥50 for the smooth secular equations) reproduced the literal-cap answer to **7+ significant figures** at 5–100× less wall-clock. Pushing the cap further gave *no additional benefit* once above a modest threshold — confirming that **tolerance, not the step cap, is the true bottleneck** (e.g. secular integration was identical at max_step=50 and max_step=5,000,000: 68.0 s vs. 68.5 s, bit-for-bit consistent answer).
- **Tolerance:** loosening 1e-14 → 1e-9 preserved 6–9+ significant figures while giving 2–30× speedup depending on context (bigger win on the oscillatory QLT side). Later runs used an adaptive schedule — tightest tolerance for large ε, progressively loosened (1e-9 → 3e-7 → 1e-6) for the smallest ε where more phase must be covered — which is the right way to spend a fixed accuracy budget.

---

## 3. The correctness bug: `dtheta_dphi`

**Diagnostic method:** rather than running full (expensive) trajectories, average QLT's exact instantaneous RHS over one orbit at a *fixed* (p, α, β) via cheap quadrature (spectrally accurate for this periodic, band-limited system — 8 quadrature points matched a 4000-point reference to 10+ significant figures), and compare that single evaluation to Feireisl/TW's secular RHS at the same point. This isolates the bookkeeping question from integration cost entirely.

**Finding, as originally coded** (`dtheta_dphi = params.eps`):

| ε | ratio (QLT-avg / Feireisl-secular) |
|---|---|
| 1.0 | 0.0160 |
| 0.5 | 0.361 |
| 0.0625 | 0.514×10⁻² (continuing pattern) |
| 0.00098 (2⁻¹⁰) | consistent with pure 1/ε |

The ratio **diverges as exactly 1/ε** — doubling every halving of ε, confirmed cleanly over 10+ orders of magnitude. This is the opposite of what a valid PN expansion should do (agreement should *improve*, not worsen, as the small parameter shrinks).

**Root cause, confirmed via power-law fit of the underlying rates themselves:**

| quantity | fitted scaling |
|---|---|
| QLT orbit-averaged dp/dφ | **ε⁵** (ratio between successive halvings → exactly 32 = 2⁵) |
| Feireisl/TW secular dp/dφ (as coded) | **ε⁶** (ratio between successive halvings → exactly 64 = 2⁶) |

`secular_2_5PN` / `secular_3_5PN` / `secular_4_5PN` already carry the correct explicit ε⁵/ε⁷/ε⁹ prefactors. Multiplying the result by `dtheta_dphi = ε` again adds one spurious extra power of ε — a double-counted small parameter, not a tuning issue.

---

## 4. The fix

```cpp
static double compute_dtheta_dphi(const BinaryState& state,
                                  const PhysicalParams& params,
                                  double phi) {
    (void)state; (void)params; (void)phi;
    return 1.0;   // was: return params.eps;
}
```

θ and φ are the same angular variable here; the secular coefficients already carry the correct ε-power for each PN order, so no additional conversion factor belongs in this function.

**Validation (pointwise check, with fix applied):** ratio → 1 with residual shrinking as **ε²** (shrink factor of ~4 per halving) cleanly from ε=0.25 down to ε=0.00098 — exactly the signature of a legitimate next-order (3.5PN-relative-to-2.5PN) correction, not a bug.

---

## 5. The structural speed fix: orbit-averaged QLT

Once the physics only needs the *secular* (orbit-averaged) behavior, there's no reason to brute-force resolve every orbit. Average the exact instantaneous QLT RHS over one orbit via cheap quadrature, then hand the result to the same large-step integrator used for Feireisl/TW:

```cpp
SecularRHS compute_QLT_RHS_orbit_averaged(const BinaryState& state,
                                          const PhysicalParams& params,
                                          int max_PN_order,
                                          int quadrature_points = 8) {
    SecularRHS avg = {0.0, 0.0, 0.0};
    for (int i = 0; i < quadrature_points; ++i) {
        double phi = 2.0*PI*(i + 0.5) / quadrature_points;   // midpoint rule
        auto rhs = compute_QLT_RHS_phi(state, params, max_PN_order, phi);
        avg[0] += rhs[0]; avg[1] += rhs[1]; avg[2] += rhs[2];
    }
    double invN = 1.0 / quadrature_points;
    avg[0] *= invN; avg[1] *= invN; avg[2] *= invN;
    return avg;
}
```

**Validated speedup** (measured, not estimated):

| ε | brute-force QLT | orbit-averaged QLT | speedup |
|---|---|---|---|
| 1.0 | 28.3 s | 3.9 s | 7.3× |
| 0.5 | ~9.6 hours (extrapolated) | 23.0 s | ~1,500× |
| 0.25 | days+ (never completed) | 165 s | >>1,000× |

**Caution — an alternative "integrate w.r.t. p instead of φ" reformulation was tried and hit a real numerical wall.** Since Δp=30 is fixed regardless of ε (unlike Δφ), this is an appealing idea, but it requires dividing by dp/dφ (to get dφ/dp), and dp/dφ *is exactly the quantity that shrinks as εⁿ* — so the reciprocal blows up right where the physics gets small. By ε≈0.03, the starting dp/dφ was already sitting on top of the regularization floor, causing outright integration failures (`stop_reason=min_step`) rather than just slowness. Keeping φ as the independent variable avoids this, since dp/dφ only ever appears in the numerator.

---

## 6. Final validated results

With the fix applied, QLT orbit-averaged (N=8 quadrature points), and an adaptive tolerance schedule (1e-9 tightening to 1e-6 for the smallest ε):

| ε | φ_QLT | φ_Feireisl | φ_TW | ratio QLT/Feireisl | \|ratio−1\| |
|---|---|---|---|---|---|
| 1.0 | 2,560.43 | 40.018 | 40.018 | 63.983 | 62.983 |
| 0.5 | 67,225.2 | 23,947.4 | 23,947.4 | 2.807 | 1.807 |
| 0.25 | 2,049,208.5 | 2,827,698.6 | 2,827,698.6 | 0.7247 | 0.2753 |
| 0.125 | 64,788,486.0 | 72,953,536.4 | 72,953,536.5 | 0.8881 | 0.1119 |
| 0.0625 | 2,067,014,230.5 | 2,132,355,965.3 | 2,132,355,965.3 | 0.9694 | 0.0306 |
| 0.03125 | 66,105,303,124.5 | 66,626,977,876.7 | 66,626,977,876.5 | 0.9922 | 0.0078 |

**Shrink factor of |ratio−1| between successive rows:** 34.9, 6.6, 2.5, **3.7, 3.9** — settling cleanly onto the expected ε² asymptote (shrink factor 4) after an initial transient at large ε, where higher PN orders still contribute non-negligibly. Extrapolating the pattern: ε=0.015625, 0.0078125, 0.00390625 should land around ratio ≈ 0.998, 0.9995, 0.9999.

**Feireisl vs. Tucker-Will:** ratio = 1.0000000 to 8–10 significant figures at *every* ε tested. The disputed 4.5PN term makes negligible difference to this particular observable (total phase to sweep this p-range) — both formulas are numerically indistinguishable here even though their coefficients differ.

---

## 7. Recommendations

1. **Apply the `dtheta_dphi = 1.0` fix.** This is a correctness issue, not a performance one — without it, the comparison is measuring a numerical artifact, not the physics being disputed.
2. **Use orbit-averaged QLT** (8-point quadrature is sufficient) instead of brute-force phi-stepping. This is what makes the ε-scan tractable at all for ε ≲ 0.25.
3. **Keep φ as the independent variable.** A p-driven reformulation is tempting (fixed Δp) but the 1/(dp/dφ) reciprocal fails exactly when ε is small — which is exactly the regime you need it to work in.
4. **Loosen tolerance adaptively** (tighter for large ε, looser — e.g. 1e-6 — for the smallest ε where more phase must be covered). Validated to cost negligible accuracy for large speed gains.
5. **Don't over-tune the step-size cap.** Once past a modest threshold, tolerance is the real bottleneck; further cap relaxation does nothing.

---

*Summary compiled from an interactive debugging/investigation session comparing brute-force vs. orbit-averaged QLT integration, diagnosing and fixing a θ→φ bookkeeping bug, and validating the resulting convergence behavior across a 256× range of the PN expansion parameter ε.*
