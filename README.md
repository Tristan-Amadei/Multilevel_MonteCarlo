# Asian Option Pricing
Goal: estimate $$C = \mathbb{E}\left[e^{-rT} \cdot max\left(\frac{1}{k} \sum_{i=1}^kS(t_i)-K, 0 \right)\right]$$
- $t_0 = 0 < t_1 < ... < t_k = T$
- r > 0
- K > 0, K a known constant
- S: a process defined on [0, T]

## Comparing Monte-Carlo methods
- Standard Monte-Carlo
- Multi-Level Monte-Carlo
- Randomized Quasi-Monte-Carlo
- Multi-Level Randomized Quasi-Monte-Carlo
