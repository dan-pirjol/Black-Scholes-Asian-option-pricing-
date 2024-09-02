# Black-Scholes-Asian-option-pricing-
Asian option pricer using the subleading Asian implied volatility in the Black-Scholes model

This repository includes Mathematica codes used for generating the plots in the paper xxx. 
This paper gives a method for pricing Asian options in the Black-Scholes model from an implied volatility  of an Asian option $\Sigma_A(K,T)$, whcih is computed to subleading order in $O(T)$.
This implied volatility is expanded in maturity $$\Sigma_A(A,T;S_0) + \Sigma_{A,0}(K;S_0) + T \Sigma_{A,1}(K;S_0) + O(T^2)$$
The zero-th order term is known exactly from Pirjol, Zhu (2015). The $O(T)$ term is given here in an expansion in log-moneyness. The coefficients of the first 3 terms in this expansion are


