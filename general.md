# Statistical Analysis of the Orbital Phase Difference (Δφ)

## Overview

This document summarizes the numerical comparison between the Adaptive RK4 integrator and the Gauss–Collocation method for computing the orbital phase evolution of the inspiral equations. The objective is to investigate how the accumulated phase difference

$begin:math:display$
\\Delta\\phi\=\\phi\_\{\\mathrm\{numerical\}\}\-\\phi\_\{\\mathrm\{reference\}\}
$end:math:display$

depends on the perturbation parameter

$begin:math:display$
\\varepsilon\\in\\left\\\{1\,\\frac12\,\\frac14\,\\frac18\,\\frac1\{16\}\,\\frac1\{32\}\\right\\\}\.
$end:math:display$

Only simulations that successfully reached the final orbital parameter $begin:math:text$p\=20$end:math:text$ are included in the statistical analysis. Simulations terminated due to reaching the maximum number of integration steps are excluded.

---

# Numerical Configuration

| Parameter | Value |
|-----------|------:|
| Integrator | Adaptive RK4 |
| PN Order | 4.5 PN |
| Initial p | 50 |
| Final p | 20 |
| Initial tolerance | $begin:math:text$10\^\{\-9\}$end:math:text$ |
| Variable tolerance | Enabled for small ε |
| Comparison method | Gauss–Collocation |

---

# Successful Simulations

| ε | Δφ (RK4) |
|---:|---------:|
|1|2.520413654×10³|
|1/2|4.327779138×10⁴|
|1/4|-7.784900776×10⁵|
|1/8|-8.165050462×10⁶|
|1/16|-6.534173479×10⁷|
|1/32|-5.216747522×10⁸|

For statistical quantities, the absolute phase difference

$begin:math:display$
\|\\Delta\\phi\|
$end:math:display$

is used.

---

# Absolute Phase Error

| ε | $begin:math:text$\|\\Delta\\phi\|$end:math:text$ |
|---:|----------------:|
|1|2.520×10³|
|1/2|4.328×10⁴|
|1/4|7.785×10⁵|
|1/8|8.165×10⁶|
|1/16|6.534×10⁷|
|1/32|5.217×10⁸|

---

# Descriptive Statistics

The following quantities should be computed for both the Adaptive RK4 and the Gauss–Collocation methods.

| Statistic | RK4 | Gauss |
|-----------|----:|------:|
|Number of successful runs|6|6|
|Mean|...|...|
|Median|...|...|
|Standard deviation|...|...|
|Minimum|...|...|
|Maximum|...|...|
|Range|...|...|
|Geometric mean|...|...|
|Coefficient of variation|...|...|

---

# Error Growth

The increase in phase error between consecutive ε values is

| Transition | Growth Factor |
|-----------|--------------:|
|1 → 1/2|17.17|
|1/2 → 1/4|17.99|
|1/4 → 1/8|10.49|
|1/8 → 1/16|8.00|
|1/16 → 1/32|7.98|

The rapid increase indicates that the accumulated phase error becomes increasingly sensitive as ε decreases.

---

# Convergence Analysis

To quantify the dependence on ε, fit the model

$begin:math:display$
\|\\Delta\\phi\|
\=
C\\varepsilon\^\{\-p\}
$end:math:display$

using least-squares regression in logarithmic coordinates,

$begin:math:display$
\\log\|\\Delta\\phi\|
\=
\\log C
\-
p\\log\\varepsilon\.
$end:math:display$

The resulting regression parameters should be reported as

| Method | Exponent $begin:math:text$p$end:math:text$ | Constant $begin:math:text$C$end:math:text$ | $begin:math:text$R\^2$end:math:text$ |
|---------|---------------:|---------------:|--------:|
|Adaptive RK4|...|...|...|
|Gauss–Collocation|...|...|...|

---

# Comparison with Gauss–Collocation

For each ε, compute the relative improvement

$begin:math:display$
R\=
\\frac\{\|\\Delta\\phi\_\{\\mathrm\{RK4\}\}\|\}
\{\|\\Delta\\phi\_\{\\mathrm\{Gauss\}\}\|\}\.
$end:math:display$

| ε | RK4 | Gauss | Improvement Factor |
|---:|----:|------:|------------------:|
|1|...|...|...|
|1/2|...|...|...|
|1/4|...|...|...|
|1/8|...|...|...|
|1/16|...|...|...|
|1/32|...|...|...|

Summary statistics:

- Mean improvement factor
- Median improvement factor
- Maximum improvement factor

---

# Integration Success Rate

| ε | RK4 | Gauss |
|---:|:--:|:----:|
|1|✓|✓|
|1/2|✓|✓|
|1/4|✓|✓|
|1/8|✓|✓|
|1/16|✓|✓|
|1/32|✓|✓|
|1/64|✗|✗|
|1/128|Not completed|Not completed|

The simulations with ε ≤ 1/64 exceeded the prescribed maximum number of integration steps before reaching the target value $begin:math:text$p\=20$end:math:text$. Consequently, no reliable phase difference can be reported for these cases.

---

# Recommended Figures

The following figures are recommended for inclusion:

1. Δφ versus ε (log-log scale)
2. Absolute phase error versus ε
3. Relative improvement factor (RK4/Gauss)
4. Log-log regression fit
5. Histogram of phase errors
6. Boxplot comparing both integrators

---

# Conclusions

The numerical experiments demonstrate a strong dependence of the accumulated orbital phase difference on the perturbation parameter ε. As ε decreases, the accumulated phase error increases by several orders of magnitude, eventually preventing the integration from reaching the prescribed final orbital parameter within the allowed computational budget.

A quantitative comparison between the Adaptive RK4 and Gauss–Collocation methods should be based on the descriptive statistics, convergence analysis, and relative improvement factors presented above. These metrics provide a comprehensive assessment of the accuracy, robustness, and computational performance of both numerical integration schemes.
