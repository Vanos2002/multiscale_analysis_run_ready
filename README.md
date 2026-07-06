# Relative Phi Differences (to QLT)

Formula used:

$$
\alpha_{method} = \left|\frac{\phi_{method} - \phi_{QLT}}{\phi_{QLT}}\right|
$$

The subsequent tables compare the respective relative phi difference values for a given epsilon in the Feireisl and Tucker-Will scheme. Each table also includes a column labeled "Winner" that evaluates the smaller number between Feireisl and Tucker-Will (TW) results. Below each table is a column chart plot portraying the percentage of better convergence to QLT ("Lagrange planetary equations via  compared to the second method. We approach the problem with two ode integrators: an explicit Runge-Kutta 4th order adaptive method and an implicit Gauss collocation method.

Initial parameters of the simulation + explicitly written tolerances at which the integrations were performed, are written in [init_conditions_and_run_params.md](init_conditions_and_run_params.md).

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

<img width="1500" height="825" alt="epsilon_winner_percent_plot" src="https://github.com/user-attachments/assets/792391f9-ee37-434d-b0d6-8c349d6d3a4c" />

## Implicit Gauss Collocation Integration Method

| $\epsilon$ | Feireisl | TW | Winner |
|:---:|:---:|:---:|:---:|
| 1.000000 | 9.8437081252e-01 | 9.8437081265e-01 | Feireisl |
| 0.500000 | 6.4377399480e-01 | 6.4377399489e-01 | Feireisl |
| 0.250000 | 3.7987645793e-01 | 3.7987645866e-01 | Feireisl |
| 0.125000 | 1.2603365354e-01 | 1.2603365351e-01 | TW |
| 0.062500 | 3.1610512046e-02 | 3.1610512036e-02 | TW |
| 0.031250 | 7.8880138610e-03 | 7.8880139116e-03 | Feireisl |

<img width="1500" height="825" alt="epsilon_winner_percent_plot_method2" src="https://github.com/user-attachments/assets/0baf6db1-9ebb-4f3a-9323-a7e8deb87338" />


## Description of Each File

- [gauss_collocation.cpp](gauss_collocation.cpp): Baseline comparison of Feireisl vs Tucker-Will convergence to the QLT reference at each epsilon value, integrated with the implicit Gauss collocation method (C++).

- [gauss_collocation_faster.cpp](gauss_collocation_faster.cpp): Optimized version of gauss_collocation.cpp using orbit-averaged QLT. The reported implicit Gauss collocation results were produced from this implementation (C++).

- [rk4_adaptive.cpp](rk4_adaptive.cpp): Baseline comparison of Feireisl vs Tucker-Will convergence to the QLT reference at each epsilon value, integrated with an adaptive explicit Runge-Kutta 4 method (C++).

- [rk4_faster.cpp](rk4_faster.cpp): Optimized version of rk4_adaptive.cpp using orbit-averaged QLT. The reported adaptive RK4 results were produced from this implementation (C++).

- [init_conditions_and_run_params.md](init_conditions_and_run_params.md): Initial parameters of the simulation + explicitly written tolerances at which the integrations were performed

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

## Windows Users on a Faculty Linux Cluster

If you are on Windows, use Windows only to connect to the cluster. Build and run this project on the Linux cluster nodes.

### Steps
1. Connect from Windows using SSH (Windows Terminal, PuTTY, or VS Code Remote SSH).
2. Build on the cluster with a C++ compiler supporting C++11 or newer.
3. Ensure Python 3.8+ is available on the cluster and install required packages (`matplotlib`, `numpy`).
4. For headless jobs, set `MPLBACKEND=Agg` before running.
5. Run via the scheduler (for example Slurm) or interactively, then copy outputs back to Windows (`scp` or WinSCP).

### Cluster-Side Minimums
- C++ compiler: GCC or Clang (C++11+)
- OS: Linux (POSIX environment)
- Python: 3.8+
- Python packages: `matplotlib`, `numpy`
- Optional: `gnuplot` (a `matplotlib` fallback is implemented)
