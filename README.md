# Heston model simulation in python

## Stochastic volatility model by Heston
The Heston model is a useful model for simulating stochastic volatility and its effect on the potential paths an asset's price can take over the life of an option.

It is popular because it provides an easy closed-form solution for European option pricing
- no risk of negative variances
- The incorporation of the leverage effect
- This allows for more effective modeling than the Black-Scholes formula due to its restrictive assumption of constant volatility.

## Heston Model SDE
The heston model is defined by a system of SDEs, to describe the movement of asset prices, where an asset’s price and volatility follow random, Brownian motion processes (this is under real world measure $\mathbb{P}$ ):

$\large dS_t = \mu S_t dt + \sqrt{v_t}S_t dW^\mathbb{P}_{S,t}$$

$\large dv_t = \kappa(\theta – v_t)dt +\sigma \sqrt{v_t} dW^\mathbb{P}_{v,t}$$

Where the variables are:

– $\sigma$ volatility of volatility

– $\theta$ long-term price variance

– $\kappa$ rate of reversion to the long term price variance

– $dW^\mathbb{P}_{S,t}$ Brownian motion of asset price

– $dW^\mathbb{P}_{v,t}$ Brownian motion of asset’s price variance

– $\rho^\mathbb{P}$ correlation between: $`dW^\mathbb{P}_{S,t}`$ and $`dW^\mathbb{P}_{v,t}`$











#### Dynamics under risk-neutral measure $\mathbb{Q}$:

$\large dS_t = r S_t dt + \sqrt{v_t}S_t dW^\mathbb{Q}_{S,t}$

$\large dv_t = \kappa^\mathbb{Q}(\theta^\mathbb{Q} – v_t)dt +\sigma^\mathbb{Q} \sqrt{v_t} dW^\mathbb{Q}_{v,t}$


## Heston Model for Monte Carlo Simulations

As discussed, one of the nice things about the Heston model for European option prices is that there is a closed-form solution once you have the characteristic function. So, discretisation of the SDE is not required for valuing a European option, however, if you would like to value other option types with complex features using the Heston model, then you can use the following code:

### Euler Discretisation of SDEs

Great resource for explanation here: [Euler and Milstein Discretization by Fabrice Douglas Rouah](https://frouah.com/finance%20notes/Euler%20and%20Milstein%20Discretization.pdf)

$\Large S_{i+1} = S_i e^{(r-\frac{v_i}{2}) \Delta t + \sqrt{v_{i}}\Delta tW^\mathbb{Q}_{S,i+1}}$

$\large v_{i+1} = v_i + \kappa(\theta – v_t)\Delta t +\sigma \sqrt{v_i} \Delta t W^\mathbb{Q}_{v,i+1}$

