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


## Description of Each File

- [gauss_collocation.cpp](gauss_collocation.cpp): Baseline comparison of Feireisl vs Tucker-Will convergence to the QLT reference at each epsilon value, integrated with the implicit Gauss collocation method (C++).

- [gauss_collocation_faster.cpp](gauss_collocation_faster.cpp): Optimized version of gauss_collocation.cpp using orbit-averaged QLT. The reported implicit Gauss collocation results were produced from this implementation (C++).

- [rk4_adaptive.cpp](rk4_adaptive.cpp): Baseline comparison of Feireisl vs Tucker-Will convergence to the QLT reference at each epsilon value, integrated with an adaptive explicit Runge-Kutta 4 method (C++).

- [rk4_faster.cpp](rk4_faster.cpp): Optimized version of rk4_adaptive.cpp using orbit-averaged QLT. The reported adaptive RK4 results were produced from this implementation (C++).

- [gauss_collocation_faster_output.md](gauss_collocation_faster_output.md): Captured output from gauss_collocation_faster.cpp. The run did not complete all scan points.

- [rk4_faster_output.md](rk4_faster_output.md): Captured output from rk4_faster.cpp. The run did not complete all scan points.

- [no_average_output.md](no_average_output.md): Captured output from rk4_adaptive.cpp, used as a non-orbit-averaged reference for comparison against rk4_faster_output.md. The run did not complete all scan points.

- [summary.md](summary.md): Summary of the changes applied to gauss_collocation.cpp and rk4_adaptive.cpp to produce gauss_collocation_faster.cpp and rk4_faster.cpp.

## Requirements for code compliation/run

### C++ (required)
- Compiler: Clang or GCC
- Minimum language standard: C++11
- Platform: POSIX-compatible OS (macOS/Linux), due to use of `unistd.h` and `sys/wait.h`

### Python (required for plotting)
- Python: 3.8+ (recommended)
- Required packages:
  - `matplotlib`
  - `numpy`

### Optional dependency
- `gnuplot` (used when available for one plotting path; `matplotlib` fallback is implemented)

### Notes
- Core numerical integration runs entirely in C++.
- Python dependencies are needed only for plot generation.
