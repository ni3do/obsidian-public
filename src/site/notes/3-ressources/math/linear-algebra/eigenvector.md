---
{"dg-publish":true,"permalink":"/3-ressources/math/linear-algebra/eigenvector/","tags":["math/linear-algebra, eth/cil/theory"],"created":"","updated":""}
---

# Eigenvector
An eigenvector is a non-zero vector $u$ that changes at most by a constant factor when the linear transform (multiply with matrix) is applied to it. The factor that it changes by is denoted with $\lambda$ and is called the [[3-ressources/math/linear-algebra/eigenvalue\|eigenvalue]].
$$Au = \lambda u$$
## How to find Eigenvectors?
1. First find the eigenvalues by solving the [[3-ressources/math/linear-algebra/characteristic-polynomial\|characteristic-polynomial]] set to 0
2. Find basic solutions by solving $(\lambda I-A)X = 0$