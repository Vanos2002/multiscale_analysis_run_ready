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


## Description of each file

gauss_collocation.cpp - Comparison of the Feireisl-TW convergence to QLT for a respective epsilon value, the integration is performed via the implicit Gauss collocation method, implemented in C++

gauss_collocation_faster.cpp - Fix of the "gauss_collocation.cpp" using the orbit-averaged QLT, the results of this work for the implicit Gauss collocation method were obtained via this file, implemented in C++

rk4_adaptive.cpp - Comparison of the Feireisl-TW convergence to QLT for a respective epsilon value, the integration is performed via the explicit Runge Kutta 4th order adaptive method, implemented in C++

rk4_faster.cpp - Fix of the "rk4_adaptive.cpp" using the orbit-averaged QLT, the results of this work for the explicit Runge Kutta 4th order adaptive method were obtained via this file, implemented in C++

gauss_collocation_faster_output.md - copied output of the file "gauss_collocation_faster.cpp", note the output did not finish entirely

rk4_faster_output.md - copied output of the file "rk4_faster.cpp", note the output did not finish entirely

no_average_output.md - copied output of the file "rk4_adaptive.cpp" for comparison with rk4_faster_output.md, note the output did not finish entirely

summary.md - description of the fixes that were implemented to the files "gauss_collocation.cpp" and "rk4_adaptive.cpp" to form "gauss_collocation_faster.cpp" and "rk4_faster.cpp"
