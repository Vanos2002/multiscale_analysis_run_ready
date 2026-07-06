## Run Configuration:

This file summarizes the active main-run setup for both executables: [gauss_collocation_faster.cpp](gauss_collocation_faster.cpp) and [rk4_faster.cpp](rk4_faster.cpp)

## Shared Physics Setup

Both files use the same baseline parameters and scan target:

- PhysicalParams: G = 1.0, M = 1.0, eta = 0.25, phi = 0.0, eps = 1.0 (eps overwritten per scan point)
- PN truncation: max_PN_order = 5 (4.5PN)
- Initial state: p_init = 50.0, alpha_init = 0.1, beta_init = 0.1
- Stop condition: p_final = 20.0
- Base tolerance: 1e-9
- Epsilon scan: [1.0, 0.5, 0.25, 0.125, 0.0625, 0.03125, 0.015625, 0.0078125, 0.00390625]

Run goal in both files:

- For each epsilon, integrate QLT, Feireisl, and TW in phi until p reaches p_final.
- Record stopping phases phi_QLT, phi_Feireisl, phi_TW.
- Compute phase errors against QLT:
  - Delta phi Feireisl = phi_QLT - phi_Feireisl
  - Delta phi TW = phi_QLT - phi_TW

## Tolerance Policy (Used in Both)

Default scan controls:

- phi_min_step = 1e-10
- phi_max_step_default = 1e8
- max_steps_default = 5e7

Effective per-epsilon overrides:

| Epsilon condition | local_tolerance | local_phi_max_step | local_max_steps |
|---|---:|---:|---:|
| eps > 0.0625 | 1e-9 | 1e8 | 5e7 |
| eps <= 0.0625 | 3e-7 | 1e9 | 1e8 |
| eps <= 0.03125 | 1e-6 | 1e10 | 3e8 |
| eps <= 0.015625 | 1e-5 | 2e10 | 5e9 |
| eps <= 0.0078125 | 3e-5 | 5e12 | 1e10 |
| eps <= 0.00390625 | 1e-4 | 1e13 | 2e10 |

Note: local_tolerance is computed as max(base_tolerance, threshold), so the table values are the effective tolerances for this run.

## Model Treatment (Both Files)

- QLT is integrated directly in physical variables.
- Feireisl and TW are integrated in tilde variables and mapped back to physical p for stopping/diagnostics.
