---
{"dg-publish":true,"permalink":"/eth/23-fs/cil/theory/03-00-singular-value-decomposition/","tags":["eth/cil/theory"],"created":"","updated":""}
---

# [[knowledge/singular-value-decomposition\| Singular Value Decomposition]]

## SVD Theorem
For each matrix $A \in \mathbb{R}^{n \times m}$, there exist orthogonal matrixes $U \in \mathbb{R^{n \times n}}$ and $V \in \mathbb{R}^{m \times m}$ such tat $A$ can be expressed as:
$$
A = U\Sigma V^T, \quad \Sigma= \text{diag}(\sigma_1, \dots, \sigma_{\text{min}\{n,m\}}), \quad \sigma_i \geq \sigma_{i+1} \geq 0 \quad \forall i$$
