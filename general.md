# Delta-Phi Comparison: Feireisl vs TW

This summary is based on the adaptive RK4 4.5PN scan you provided.
The comparison uses the absolute phase errors
$|\Delta\phi_{Feireisl}|$ and $|\Delta\phi_{TW}|$ at each epsilon value,
and the relative ratios
$\left|\phi_{QLT} / \phi_{method} - 1\right|$.

## Results

| $\varepsilon$ | $\log_{10}(\varepsilon)$ | $|\Delta\phi_{Feireisl}|$ | $|\Delta\phi_{TW}|$ | $\left|\phi_{QLT}/\phi_{Feireisl} - 1\right|$ | $\left|\phi_{QLT}/\phi_{TW} - 1\right|$ | Closer to QLT |
|---:|---:|---:|---:|---:|---:|:---|
| 1.000000 | 0.000000 | 2.5204136538682756e+03 | 2.5204136541985422e+03 | 6.2982771521859654e+01 | 6.2982772049912725e+01 | Feireisl |
| 0.500000 | -0.301030 | 4.3277791378577371e+04 | 4.3277791383653494e+04 | 1.8072017471719137e+00 | 1.8072017477669546e+00 | Feireisl |
| 0.250000 | -0.602060 | 7.7849007760357927e+05 | 7.7849007830244140e+05 | 2.7530872100389336e-01 | 2.7530872118299998e-01 | Feireisl |
| 0.125000 | -0.903090 | 8.1650504621836841e+06 | 8.1650505389102697e+06 | 1.1192124279919535e-01 | 1.1192124373320422e-01 | Feireisl |
| 0.062500 | -1.204120 | 6.5341734785805225e+07 | 6.5341734726159096e+07 | 3.0642976992785398e-02 | 3.0642976965670532e-02 | TW |
| 0.031250 | -1.505150 | 5.2167475221127319e+08 | 5.2167475198748779e+08 | 7.8297826021261896e-03 | 7.8297825987936331e-03 | TW |
| 0.015625 | -1.806180 | 3.6254669966894531e+08 | 3.6254669987548828e+08 | 3.0704784488844172e-04 | 3.0704784506330185e-04 | Feireisl |

## Notes

- The two methods are extremely close at every epsilon shown; the absolute differences between their phase errors are tiny compared with the errors themselves.
- The winner alternates only by a very small margin in the lower-epsilon region.
- These values come from the RK4 adaptive scan excerpt you pasted, not from the Gauss collocation run.
