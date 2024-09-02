# Black-Scholes-Asian-option-pricing-
Asian option pricer using the Asian implied volatility in the Black-Scholes model, including subleading $O(T)$ corrections 

This repository includes Mathematica codes used for generating the plots in the paper [arXiv:2407.05142[q-fin.MF]](https://arxiv.org/abs/2407.05142). 

The Asian option price with strike $K$ and maturity $T$ is computed from the Black-Scholes formula (as if were an European option) with the forward price $F(T) = S_0 \frac{e^{(r-q)T}-1}{(r-q)}$ and a special implied volatility $\Sigma_A(K,T)$ - the *Asian implied volatility*.

The Asian implied volatility is expanded in maturity $$\Sigma_A(K,T) = \Sigma_{A,0}(K) + T \Sigma_{A,1}(K) + O(T^2)$$

The zero-th order term $\Sigma_{A,0}(K)$ is known exactly from [Pirjol, Zhu (2015)](https://arxiv.org/abs/1609.07559). 
The $O(T)$ term is given here in an expansion in log-moneyness $x = \log(K/F(T))$ as

$$\Sigma_{A,1}(K) = \Sigma_{A,1}(F(T)) + s_A x + \kappa_A x^2 + O(x^3)$$

## **Example**

Suppose we would like to price an Asian option in the Black-Scholes model with parameters $S_0=2, \sigma=0.1, r=0.02, q=0$. The Asian option has strike $K=2.0$ and maturity $T=1$ year.




