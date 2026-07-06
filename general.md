# Delta-Phi Comparison: Feireisl vs TW

This is based on the adaptive RK4 4.5PN scan you provided.  
The table compares the absolute phase errors $|\Delta\phi_{Feireisl}|$ and $|\Delta\phi_{TW}|$, along with the relative error magnitude
$\left|\phi_{QLT}/\phi_{method} - 1\right|$.

## Results

| $\varepsilon$ | $|\Delta\phi_{Feireisl}|$ | $|\Delta\phi_{TW}|$ | rel. err. Feireisl | rel. err. TW | Better |
|---:|---:|---:|---:|---:|:---|
| 1.000000 | $2.52 \times 10^3$ | $2.52 \times 10^3$ | 6298.3% | 6298.3% | Feireisl |
| 0.500000 | $4.33 \times 10^4$ | $4.33 \times 10^4$ | 180.72% | 180.72% | Feireisl |
| 0.250000 | $7.78 \times 10^5$ | $7.78 \times 10^5$ | 27.53% | 27.53% | Feireisl |
| 0.125000 | $8.17 \times 10^6$ | $8.17 \times 10^6$ | 11.19% | 11.19% | Feireisl |
| 0.062500 | $6.53 \times 10^7$ | $6.53 \times 10^7$ | 3.06% | 3.06% | TW |
| 0.031250 | $5.22 \times 10^8$ | $5.22 \times 10^8$ | 0.783% | 0.783% | TW |
| 0.015625 | $3.63 \times 10^8$ | $3.63 \times 10^8$ | 0.0307% | 0.0307% | Feireisl |

## Short takeaway

Feireisl and TW are extremely close at every epsilon value. The winner changes only by a very small margin, and the differences are tiny compared with the overall scale of the phase errors.
