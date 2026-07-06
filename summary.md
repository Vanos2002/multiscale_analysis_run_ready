# Feireisl-Tucker-Will 4.5PN Comparison: Investigation Summary

## Context

This analysis compares three formulations of post-Newtonian binary inspiral dynamics:

- QLT: numerical osculating reference solution
- Feireisl: analytic secular (orbit-averaged) model
- Tucker-Will: analytic secular model

The two analytic models differ only in the 4.5PN radiation-reaction sector (Tucker and Will, 2021, [arXiv:2108.12210](https://arxiv.org/abs/2108.12210)).

Test configuration:

- Equal masses with $\eta = 0.25$
- Initial $(\alpha,\beta) = (0.1,0.1)$, so $e \approx 0.14$
- Semi-latus rectum range: $p: 50 \rightarrow 20$
- PN bookkeeping parameter scan: $\epsilon = 1.0$ down to $\epsilon = 0.0039$ by repeated halving

Primary observable: total phase $\phi$ required to evolve from $p=50$ to $p=20$.

## 1. Initial Limitation: Direct QLT Integration Cost

Direct integration of instantaneous QLT equations requires explicit resolution of orbital-scale oscillations. Runtime increases rapidly as $\epsilon$ decreases.

| $\epsilon$ | $\Delta p$ evaluated | brute-force QLT wall-clock |
|---:|---:|---:|
| 1.0 | 30 | 28.3 s |
| 0.5 | 1 | 21.6 s (full-range extrapolation: ~9.6 h) |
| 0.25 | 1 | >250 s (incomplete; full-range extrapolation: days+) |

The dominant scaling is consistent with an $\epsilon^{-5}$ growth in orbit count for fixed $\Delta p$, with near-constant per-orbit numerical cost.

## 2. Runtime Controls Verified Before Model Changes

Two controls were validated independently of any physics change:

- Step-size cap: relaxing very conservative $\Delta\phi$ caps produced the same solution (to 7+ significant figures) with substantial runtime reduction.
- Tolerance: loosening from $10^{-14}$ to $10^{-9}$ preserved solution accuracy at the relevant scale while reducing runtime significantly.

An adaptive tolerance schedule ($10^{-9}\rightarrow 3\times10^{-7}\rightarrow10^{-6}$ toward smaller $\epsilon$) provided efficient cost allocation.

## 3. Consistency Error in $\mathrm{d}\theta/\mathrm{d}\phi$

A pointwise diagnostic was used: orbit-average the instantaneous QLT RHS at fixed state and compare directly against analytic secular RHS at the same point.

With the original implementation (`dtheta_dphi = eps`), the QLT/secular ratio scaled as $1/\epsilon$, i.e., divergence as $\epsilon \to 0$.

Measured scaling of underlying rates:

| quantity | fitted scaling |
|---|---|
| orbit-averaged QLT $\mathrm{d}p/\mathrm{d}\phi$ | $\epsilon^5$ |
| secular $\mathrm{d}p/\mathrm{d}\phi$ (as coded) | $\epsilon^6$ |

Interpretation: an extra factor of $\epsilon$ was introduced by multiplying secular terms that already carried the correct PN-order $\epsilon$ prefactors.

## 4. Corrective Change

Applied change:

```cpp
static double compute_dtheta_dphi(const BinaryState& state,
                                  const PhysicalParams& params,
                                  double phi) {
    (void)state; (void)params; (void)phi;
    return 1.0;   // was: return params.eps;
}
```

With this correction, pointwise ratio residuals contract as $\epsilon^2$, consistent with expected next-order behavior.

## 5. Structural Acceleration: Orbit-Averaged QLT

To target secular behavior directly, QLT RHS was orbit-averaged (midpoint quadrature, $N=8$) and integrated with the same large-step framework used for Feireisl/TW.

```cpp
SecularRHS compute_QLT_RHS_orbit_averaged(const BinaryState& state,
                                          const PhysicalParams& params,
                                          int max_PN_order,
                                          int quadrature_points = 8) {
    SecularRHS avg = {0.0, 0.0, 0.0};
    for (int i = 0; i < quadrature_points; ++i) {
        double phi = 2.0*PI*(i + 0.5) / quadrature_points;
        auto rhs = compute_QLT_RHS_phi(state, params, max_PN_order, phi);
        avg[0] += rhs[0]; avg[1] += rhs[1]; avg[2] += rhs[2];
    }
    double invN = 1.0 / quadrature_points;
    avg[0] *= invN; avg[1] *= invN; avg[2] *= invN;
    return avg;
}
```

Observed runtime impact:

| $\epsilon$ | brute-force QLT | orbit-averaged QLT | speedup |
|---:|---:|---:|---:|
| 1.0 | 28.3 s | 3.9 s | 7.3x |
| 0.5 | ~9.6 h (extrapolated) | 23.0 s | ~1500x |
| 0.25 | incomplete (days-scale extrapolated) | 165 s | >1000x |

A $p$-driven reformulation was also tested and rejected for this regime due to instability from division by small $\mathrm{d}p/\mathrm{d}\phi$.

## 6. Final Numerical Behavior

Using corrected bookkeeping, orbit-averaged QLT, and adaptive tolerances:

# Relative Phi Differences (to QLT)

Formula used:

$$
\alpha_{method} = \left|\frac{\phi_{method} - \phi_{QLT}}{\phi_{QLT}}\right|
$$

## Explicit RK4 Adaptive Integration Method

| $\epsilon$ | Feireisl | TW | Winner |
|:---:|:---:|:---:|:---:|
| 1.000000 | 9.8437079270e-01 | 9.8437079282e-01 | Feireisl |
| 0.500000 | 6.4377337646e-01 | 6.4377337653e-01 | Feireisl |
| 0.250000 | 3.7989793583e-01 | 3.7989793617e-01 | Feireisl |
| 0.125000 | 1.2602625825e-01 | 1.2602625943e-01 | Feireisl |
| 0.062500 | 3.1611652121e-02 | 3.1611652093e-02 | TW |
| 0.031250 | 7.8915718944e-03 | 7.8915718911e-03 | TW |
| 0.015625 | 1.9913630387e-03 | 1.9913630605e-03 | Feireisl |

## Implicit Gauss Collocation Integration Method

| $\epsilon$ | Feireisl | TW | Winner |
|:---:|:---:|:---:|:---:|
| 1.000000 | 9.8437081252e-01 | 9.8437081265e-01 | Feireisl |
| 0.500000 | 6.4377399480e-01 | 6.4377399489e-01 | Feireisl |
| 0.250000 | 3.7987645793e-01 | 3.7987645866e-01 | Feireisl |
| 0.125000 | 1.2603365354e-01 | 1.2603365351e-01 | TW |
| 0.062500 | 3.1610512046e-02 | 3.1610512036e-02 | TW |
| 0.031250 | 7.8880138610e-03 | 7.8880139116e-03 | Feireisl |

## Conclusion

The observed non-convergence originated from a bookkeeping inconsistency in $\mathrm{d}\theta/\mathrm{d}\phi$, not from the disputed 4.5PN physics term. After correction and secularized QLT evaluation, convergence behavior is consistent with PN expectations, and Feireisl/TW differences are negligible for the tested metric.
