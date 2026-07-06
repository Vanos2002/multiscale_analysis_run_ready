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
