---
{"dg-publish":true,"permalink":"/3-ressources/machine-learning/evidence-lower-bound/","tags":["machine-learning, eth/cil/theory"],"created":"","updated":""}
---

# Evidence Lower Bound
- yields approximate, often tractable objective functions

### Definition
$$l(\theta) = \sum_{t=1}^s \ln \sum_{z=1}^k \pi_{z} p(x;\theta_{z}) \geq \sum_{t=1}^s \sum_{z=1}^k q_{tz} \left[\ln \pi_{z} + \ln p(x_{t}; \theta_{z}) - \ln q_{tz} \right]$$
Where $q$ is a vector of convex weights for each sample, ($q_{tk}$ denotes the probability that sample $t$  is part of the $k$-th cluster, intuitively)

