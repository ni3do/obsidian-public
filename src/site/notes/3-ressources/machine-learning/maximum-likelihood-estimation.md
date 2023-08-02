---
{"dg-publish":true,"permalink":"/3-ressources/machine-learning/maximum-likelihood-estimation/","tags":["math/machine-learning, eth/cil/theory"],"created":"","updated":""}
---

# Maximum Likelihood Estimation
- uses likelihood function as an objective
- probability distribution thought of as a function of parameters while keeping observed outcomes fixed
- more convenient to work with log likelihood
- suggests to chose the model parameters which maximize the probability of the observed data.

### Definition
![3-ressources/assets/cil-log-likelihood.png](/img/user/3-ressources/assets/cil-log-likelihood.png)
Optimization problem find the **maximum likelihood estimate (MLE)**:
$$\theta^{\text{MLE}} = \arg\max_{\boldsymbol{\theta}} l(\boldsymbol{\theta};\{x_{1}, \dots, x_{s}\})$$
### Computation
Use [[0-inbox/expectation-maximization-algorightm\|expectation-maximization-algorightm]]
