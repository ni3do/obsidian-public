---
{"dg-publish":true,"permalink":"/3-ressources/math/linear-algebra/singular-value-decomposition/","tags":["math"],"created":"","updated":""}
---

# [[3-ressources/math/linear-algebra/singular-value-decomposition\| Singular Value Decomposition]]

## SVD Theorem
For each matrix $A \in \mathbb{R}^{n \times m}$, there exist orthogonal matrixes $U \in \mathbb{R^{n \times n}}$ and $V \in \mathbb{R}^{m \times m}$ such tat $A$ can be expressed as:
$$
A = U\Sigma V^T, \quad \Sigma= \text{diag}(\sigma_1, \dots, \sigma_{\text{min}\{n,m\}}), \quad \sigma_i \geq \sigma_{i+1} \geq 0 \quad \forall i$$
* The set of singular values is unique
* Left/right singular vectors (columns or $U$ and $V$) can have arbitrary sign

## Computation Complexity
>[!tip] SVD is computable in $\mathcal{O}(\min\{nm^2, mn^2\}$


## SVD and Frobenius norm
Let the SVD of $A \in \mathbb{R}^{n \times m}$ be given by $A ) U\Sigma V^T$, then:
$$||A||_F^2 = \sum_{i=1}^{\min{n,m}}\sigma_i^2$$
## SVD and Spectral norm
Let the SVD of $A \in \mathbb{R}^{n \times m}$ be given by $A ) U\Sigma V^T$, then:
$$
||A||_2 := \sup\{||Ax||: ||x|| = 1\} = \sigma_1$$
## Reduced SVD
One can often prune columns of $U$ or $V$ corresponding to zero elements in $\Sigma$ (or zero-padded columns/rows)
![4-archive/cil/theory/old/assets/reduced-svd.png](/img/user/4-archive/cil/theory/old/assets/reduced-svd.png)