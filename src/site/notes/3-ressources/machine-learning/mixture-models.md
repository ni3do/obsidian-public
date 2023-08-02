---
{"dg-publish":true,"permalink":"/3-ressources/machine-learning/mixture-models/","tags":["computer-science/machine-learning eth/cil/theory"],"created":"","updated":""}
---

# Mixture Models
- probabilistic clustering models that associate a categorical variable with each pattern
- associate a categorical (random) variable $Z_t$ with a pattern in the data
- model to represent a subpopulation within a population, without 
### Definition
![3-ressources/assets/cil-categorical-mixture-model.png](/img/user/3-ressources/assets/cil-categorical-mixture-model.png)
$\pi = (\pi_{1}, \dots, \pi_{k})$ a priori probability that a random point belongs to class
Define a class conditional distribution $p(\boldsymbol{x}|z)$  for each class:
$$p(\boldsymbol{x}, z) = \pi_{z} p(x | z), \quad p(x) = \sum_{z=1}^k p(x,z) = \sum_{z=1}^k \pi_{z} p(x|z)$$
Mixture distributions are convex combinations of class-specific distributions
Class conditional distributions will be independently parametrized with $\theta_{z}$
**Total model parameter** vector that we have to fit:
$$\boldsymbol{\theta} = (\boldsymbol{\pi}, \theta_{1}, \dots, \theta_{k})$$
**Posteriors** are then calculated:
$$\mathbb{P}(Z = z| \boldsymbol{x;\theta}) = \frac{\pi_{z}p(\boldsymbol{x;\theta_{z}})}{\sum_{\zeta=1}^k \pi_{\zeta} p(\boldsymbol{x;\theta_{\zeta}})}$$
Posterior latent class probabilities represent a probabilistic clustering.