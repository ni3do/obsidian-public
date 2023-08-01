---
{"dg-publish":true,"permalink":"/0-inbox/cil-reconstruction-theorem/","tags":["math/linear-algebra, eth/cil/theory"],"created":"","updated":""}
---

# Reconstruction Theorem
- with more than critical number of observations [[3-ressources/math/linear-algebra/nuclear-norm-minimization\|nuclear-norm-minimization]] can recover correct matrix with high probability

### Definition
Let $A \in \mathbb{R}^{n \times n}$ be a rank $k$ matrix that is incoherent with some $\mu \geq 1$ and for which $S$ samples have been observed at random. Then there is a universal constant $C$ such that if $S \geq C \mu^2 nk(\log n)^6$, then with probability at least $1-n^{-3}$, $A$ fulfills:
$$A = \arg\min_{B} \lvert \lvert B \rvert  \rvert_{*}, \quad \text{subject to } \Pi_{\Omega}(B) = \Pi_{\Omega}(A)$$
