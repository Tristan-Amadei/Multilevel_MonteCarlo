# Asian Option Pricing
Goal: estimate $$C = \mathbb{E}\left[e^{-rT} \cdot max\left(\frac{1}{k} \sum_{i=1}^kS(t_i)-K, 0 \right)\right]$$
- $t_0 = 0 < t_1 < ... < t_k = T$
- r > 0, r a known constant
- K > 0, K a known constant
- S: a process defined on [0, T]

## Comparing Monte-Carlo methods
- **_Standard Monte-Carlo_**
- **_Multi-Level Monte-Carlo_**, from the paper [Multilevel Monte Carlo Path Simulation](https://people.maths.ox.ac.uk/gilesm/files/OPRE_2008.pdf) of [Michael B. Giles](https://scholar.google.com/citations?user=Iehle6kAAAAJ&hl=en), Professor of Scientific Computing, University of Oxford
- **_Randomized Quasi-Monte-Carlo_**
- **_Multi-Level Randomized Quasi-Monte-Carlo_**
