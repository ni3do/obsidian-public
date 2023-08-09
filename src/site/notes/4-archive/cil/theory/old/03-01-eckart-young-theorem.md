---
{"dg-publish":true,"permalink":"/4-archive/cil/theory/old/03-01-eckart-young-theorem/","tags":["eth/cil/theory"],"created":"","updated":""}
---

# Eckart Young Theorem
>[!tip] By pruning the singular values below $\sigma_k$ in the [[3-ressources/math/linear-algebra/singular-value-decomposition\|SVD]] representation, we get an optimal rank $k$ approximation of a matrix
>
* Is fundamental to many low-rank approximation problems
* This means that approximations for any $k$ can directly be read-off the SVD
## Formal definition:
>[!tip] Given $A \in \mathbb{R}^{n \times m}$ with SVD $A = U \Sigma V^T$. Then for all $1 \leq k \leq \min{n,m}$:
>$$
>\begin{align}
>A_k &:= U \text{diag}(\sigma_1, \dots, \sigma_k) V^T\\
>	&\in \arg\min\{||A-B||_F: \text{rank}(B) \leq k\}
>\end{align}
>$$

## Corollary
The squared error of low rank approximations can be expressed as:
$$
||A-A_k||_F^2 = \sum_{i=k+1}^{\text{rank}(A)}\sigma_i^2$$
Proof:
$$
A - A_k = U \text{diag}(0, \dots, 0, \dots, \sigma_{k+1}, \dots, \sigma_{\min\{n,m\}})V^T$$
