# Asian Option Pricing
Goal: estimate $$C = \mathbb{E}\left[e^{-rT} \cdot max\left(\frac{1}{k} \sum_{i=1}^kS(t_i)-K, 0 \right)\right]$$
- $t_0 = 0 < t_1 < ... < t_k = T$
- r > 0, r a known constant
- K > 0, K a known constant
- S: a CIR stochastic process, following the stochastic differential equation $dS_t=\alpha(b-S_t)dt+\sigma\sqrt{S_t}dW_t$
- $W_t$: Bromnian motion

## Monte-Carlo methods
- **_Standard Monte-Carlo_**
- **_Multi-Level Monte-Carlo_**
- **_Randomized Quasi-Monte-Carlo_**
- **_Multi-Level Randomized Quasi-Monte-Carlo_**

## Multilevel Monte-Carlo
From the paper [Multilevel Monte Carlo Path Simulation](https://people.maths.ox.ac.uk/gilesm/files/OPRE_2008.pdf) of [Michael B. Giles](https://scholar.google.com/citations?user=Iehle6kAAAAJ&hl=en), Professor of Scientific Computing, University of Oxford. <br />
Let P denote the payoff for f(S(T)) and $\hat P_l$ denote the approximations to P using a numerical discretisation with timestep $h_l$. <br />
Then: $\mathbb{E}[\hat P_L] = \mathbb{E}[\hat P_0] + \sum\limits_{l=1}^L\mathbb{E}[\hat P_l - \hat P_{l-1}]$  <br />
Let $\hat Y_0$ be an estimator of $\mathbb{E}[\hat P_0]$ and $Y_l$ an estimator of $\mathbb{E}[\hat P_l - \hat P_{l-1}], l > 0$ <br />
The idea of Multilevel Monte-Carlo is to estimate option price as 
$$\hat Y=\sum\limits_{l=0}^{L}\hat Y_l= \sum\limits_{l=0}^{L}\frac{1}{N_l}\sum\limits_{i=1}^{N_l}(\hat P_l^{(i)} - \hat P_{l-1}^{(i)})$$ <br />
This methods keeps the absence of bias of the Standard Monte-Carlo method, while inducing a smaller variance of the estimator. <br />
As we show in this project, this variance can decrease even further by combining the Multilevel Monte-Carlo method with the Randomized Quasi Monte-Carlo.

## Comparison
  
<table>
  <tr>
    <th>ϵ</th>
    <th colspan="3">Variance</th>
    <th colspan="3">CPU Time (s)</th>
  </tr>
  <tr>
    <td></td>
    <td>MC</td>
    <td>MLMC</td>
    <td>QMLMC</td>
    <td>MC</td>
    <td>MLMC</td>
    <td>QMLMC</td>
  </tr>
  <tr>
    <td>$1.10^{-4}$</td>
    <td>$1,1.10^{-4}$</td>
    <td>$5,1.10^{-8}$</td>
    <td>$1,4.10^{-8}$</td>
    <td>8,1</td>
    <td>19110,2</td>
    <td>38678,6</td>
  </tr>
  <tr>
    <td>$1.10^{-3}$</td>
    <td>$1,2.10^{-4}$</td>
    <td>$1,2.10^{-6}$</td>
    <td>$2,6.10^{-7}$</td>
    <td>4,9</td>
    <td>16,7</td>
    <td>59,7</td>
  </tr>
  <tr>
    <td>$4.10^{-3}$</td>
    <td>$1,7.10^{-4}$</td>
    <td>$1,7.10^{-5}$</td>
    <td>$1,0.10^{-6}$</td>
    <td>3,9</td>
    <td>6,9</td>
    <td>43,1</td>
  </tr>
</table>

- MC = Standard Monte-Carlo
- MLMC = Multilevel Monte-Carlo
- QMLMC = Multi-Level Randomized Quasi-Monte-Carlo

<br />
It becomes evident that Multilevel Monte-Carlo makes it possible to greatly reduce the variance, but at the cost of much higher complexity and computational time. <br />
It is then necessary to make a compromise between CPU time and desired variance.
