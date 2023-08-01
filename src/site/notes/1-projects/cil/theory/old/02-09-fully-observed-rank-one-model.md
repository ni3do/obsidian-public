---
{"dg-publish":true,"permalink":"/1-projects/cil/theory/old/02-09-fully-observed-rank-one-model/","tags":["eth/cil/theory"],"created":"","updated":""}
---

## Fully observed Rank 1 Model
Useful identiy:
$$||R||_F^2 = \text{tr}(R^TR)$$
We can then rewrite the [[1-projects/cil/theory/old/02-05-rank-one-model#Squared Error?!?\|objective]]:
$$l(u,v) = \frac{1}{2}||A-uv^T||_F^2$$
## Optimality Conditions
Directionality of $u,v$ is purely determined by the last term:
$$
(u,v) \rightarrow \max\{u^T Av\}, \quad \text{s.t.} ||u|| = ||v|| = 1$$
This can be solved with [[3-ressources/math/lagrange-multipliers\| Lagrange multipliers]]:
$$
\mathcal{L} = u^T Av - \lambda u \cdot u - \mu v \cdot v$$
First order optimality condition:
$$
\nabla_u \mathcal{L} = Av - 2\lambda u \overset{!}= 0 \Rightarrow u = \frac{Av}{||Av||}$$
