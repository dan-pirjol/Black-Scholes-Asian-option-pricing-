# Black-Scholes-Asian-option-pricing-
Asian option pricer using the Asian implied volatility in the Black-Scholes model, including subleading $O(T)$ corrections 

This repository includes Mathematica codes used for generating the plots in the paper [arXiv:2407.05142[q-fin.MF]](https://arxiv.org/abs/2407.05142). 

The Asian option price with strike $K$ and maturity $T$ is computed from the Black-Scholes formula (as if were an European option) with the forward price $F(T) = S_0 \frac{e^{(r-q)T}-1}{(r-q)}$ and a special implied volatility $\Sigma_A(K,T)$ - the *Asian implied volatility*.

The Asian implied volatility is expanded in maturity $$\Sigma_A(K,T) = \Sigma_{A,0}(K) + T \Sigma_{A,1}(K) + O(T^2)$$

The zero-th order term $\Sigma_{A,0}(K)$ is known exactly from [Pirjol, Zhu (2015)](https://arxiv.org/abs/1609.07559). For $K$ sufficiently close to the spot price it is well approximated by the series expansion in log-moneyness $x = \log(K/F(T))$ as

$$\Sigma_{A,0}(K) = \frac{\sigma}{\sqrt3} \Big( 1 +\frac15 x - \frac{1}{84} x^2 - \frac{17}{10500} x^3 + O(x^4)\Big) $$


The $O(T)$ term is also expanded in log-moneyness as

$$\Sigma_{A,1}(K) = \Sigma_{A,1}(ATM) + s_{A,1} x + \kappa_{A,1} x^2 + O(x^3)$$

The first three coefficients $\Sigma_{A,1}(ATM), s_{A,1}, \kappa_{A,1}$ are given in the paper: 

$$\Sigma_{A,1}(ATM)=\sigma^2 (-\frac{61}{9450} (\sigma^2 T)+\frac{1}{12} (rT) ), s_{A,1} = -\frac{34}{23625} \sigma^2(\sigma^2 T), \kappa_{A,1} = \sigma^2( \frac{1657}{4158000}(\sigma^2 T) - \frac{5}{2016} (rT))$$

## **Example**

Suppose we would like to price an Asian option in the Black-Scholes model with parameters $S_0=2, \sigma=0.1, r=0.02, q=0$. The Asian option has strike $K=2.0$ and maturity $T=1$ year.
The forward of the Asian option is $F(T) = 2.02013$, so the log-moneyness is $x=\log(2.0/2.02013) = -0.01$. The Asian option is slightly in-the-money.

The zero-th order Asian implied volatility is  $\Sigma_{A,0}(2.0) = 0.057677$. Adding also the subleading $O(T)$ corrections this becomes $0.057817$. Substituting into the Black-Scholes formula we get

$$C_A = e^{-rT} C_{BS}(K=2.0, T=1; F(T) = 2.02013,\Sigma_A=0.057817) = 0.0559859$$

where the undiscounted Black-Scholes call price is

$$C_{BS}(K,T;F,\sigma) = F N(d_1) - K N(d_2),\quad d_{1,2}=\frac{1}{\sigma\sqrt{T}}(\log(K/F) \pm \frac12 \sigma^2 T)$$


