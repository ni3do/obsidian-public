---
{"dg-publish":true,"permalink":"/3-ressources/machine-learning/maximum-likelihood-estimation/","tags":["math/machine-learning, eth/cil/theory"],"created":"","updated":""}
---

# Maximum Likelihood Estimation
- uses likelihood function as an objective
- probability distribution thought of as a function of parameters while keeping observed outcomes fixed
- more convenient to work with log likelihood
- suggests to chose the model parameters which maximize the probability of the observed data.

### Definition
Log likelihood function:
$$l(\theta;\{x_{1}, \dots, x_{s}\}) = \sum_{t=1}^s \ln p(x_{t}; \theta) = \sum_{t=1}^s \ln \sum_{z=1}^k \pi_{z} p(x_{t}; \theta_{z})$$
Where $p(x_{t}; \theta_{z})$ is the probability distribution which we chose for our clusters.
**Example for Gaussian:**
$$l(\theta;\{x_{1}, \dots, x_{s}\}) = \sum_{t=1}^s \ln p(x_{t}; \theta) = \sum_{t=1}^s \ln \sum_{z=1}^k \pi_{z} \mathcal{N}(x_{z} | \mu_{z}, \Sigma_{z})$$

Optimization problem find the **maximum likelihood estimate (MLE)**:
$$\theta^{\text{MLE}} = \arg\max_{\boldsymbol{\theta}} l(\boldsymbol{\theta};\{x_{1}, \dots, x_{s}\})$$
### Computation
Use [[3-ressources/machine-learning/expectation-maximization-algorightm\|expectation-maximization-algorightm]]
