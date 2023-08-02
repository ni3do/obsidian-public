---
{"dg-publish":true,"permalink":"/3-ressources/machine-learning/expectation-maximization-algorightm/","tags":["math/machine-learning, eth/cil/theory"],"created":"","updated":""}
---

# Expectation Maximization Algorithm
- use [[0-inbox/jensen-inequality\|Jensen's Inequality]] to lower bound a concave function

### Definition
#### E-Step
- goal is to maximize the lower bound with respect to the posterior probabilities of the latent variables
Use [[3-ressources/math/lagrange-multipliers\|lagrange multipliers]] decoupled for each point:
$$\mathcal{L} = \sum_{z=1}^k q_{z} \left[ \ln p_{z} + \ln \pi_{z} - \ln q_{z} \right] - \lambda \left( \sum_{z} q_{z} - 1\right)$$
$\lambda$ is introduced to keep $q$ normalized.
Deriving the **first order optimality condition**:
$$\ln p_{z} + \ln \pi_{z} - \ln q_{z} \overset{!}{=} \lambda + 1 \iff q_{z} \overset{!}{=} e^{\lambda + 1} \pi_{z} p_{z} \iff q_{z} \overset{!}{=} \frac{\pi_{z} p_{z}}{\sum_{\zeta} \pi_{\zeta} p_{\zeta}}$$
#### M-Step
**Maximize lower bound w.r.t. the parameters of $p$ with the current guess of $q$**

$$\pi_{z} = \frac{1}{s} \sum_{t=1}^s q_{tz}$$
$$\theta_{z} \overset{\max}{\rightarrow} \sum_{t=1}^s \ln p(x_{t}; \theta_{z})$$
