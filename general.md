# Delta-Phi Comparison: Feireisl vs TW

This summary is based on the adaptive RK4 4.5PN scan you provided.
The comparison uses the absolute phase errors
$|\Delta\phi_{Feireisl}|$ and $|\Delta\phi_{TW}|$ at each epsilon value,
and the relative ratios
$\left|\phi_{QLT} / \phi_{method} - 1\right|$.

## Absolute Delta-Phi

| $\varepsilon$ | $\log_{10}(\varepsilon)$ | $|\Delta\phi_{Feireisl}|$ | $|\Delta\phi_{TW}|$ |
|---:|---:|---:|---:|
| 1.000000 | 0.000000 | $2.52 \times 10^3$ | $2.52 \times 10^3$ |
| 0.500000 | -0.301030 | $4.33 \times 10^4$ | $4.33 \times 10^4$ |
| 0.250000 | -0.602060 | $7.78 \times 10^5$ | $7.78 \times 10^5$ |
| 0.125000 | -0.903090 | $8.17 \times 10^6$ | $8.17 \times 10^6$ |
| 0.062500 | -1.204120 | $6.53 \times 10^7$ | $6.53 \times 10^7$ |
| 0.031250 | -1.505150 | $5.22 \times 10^8$ | $5.22 \times 10^8$ |
| 0.015625 | -1.806180 | $3.63 \times 10^8$ | $3.63 \times 10^8$ |

## Relative Error Ratios

| $\varepsilon$ | $\left|\phi_{QLT}/\phi_{Feireisl} - 1\right|$ | $\left|\phi_{QLT}/\phi_{TW} - 1\right|$ |
|---:|---:|---:|
| 1.000000 | 6298.3% | 6298.3% |
| 0.500000 | 180.72% | 180.72% |
| 0.250000 | 27.53% | 27.53% |
| 0.125000 | 11.19% | 11.19% |
| 0.062500 | 3.06% | 3.06% |
| 0.031250 | 0.783% | 0.783% |
| 0.015625 | 0.0307% | 0.0307% |

## Winner Summary

| $\varepsilon$ | Better |
|---:|:---|
| 1.000000 | Feireisl |
| 0.500000 | Feireisl |
| 0.250000 | Feireisl |
| 0.125000 | Feireisl |
| 0.062500 | TW |
| 0.031250 | TW |
| 0.015625 | Feireisl |

## Notes

- The two methods are extremely close at every epsilon shown; the absolute differences between their phase errors are tiny compared with the errors themselves.
- The winner changes only by a very small margin in the lower-epsilon region.
- These values come from the RK4 adaptive scan excerpt you pasted, not from the Gauss collocation run.
