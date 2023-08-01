---
{"dg-publish":true,"permalink":"/1-projects/cil/theory/old/03-02-svd-pca/","tags":["eth/cil/theory"],"created":"","updated":""}
---

# SVD and PCA
[[3-ressources/math/linear-algebra/singular-value-decomposition\|SVD]] is intimately related to [[3-ressources/math/eigendecomposition\|eigendecomposition]]
* $A$ is square and symmetric: $U$ and $V$ have equal columns up to possible sign differences
* if $A$ is [[3-ressources/math/positive-semi-definit\|positive semi-definit]], then the SVD is equal to the [[3-ressources/math/eigendecomposition\|eigendecomposition]]
* Squares of $A$: $AA^T \in \mathbb{R}^{n \times n}$ as well as $A^TA \in \mathbb{R}^{m \times m}$: 
$$
\begin{align}
AA^T = U\Sigma \Sigma^T U^T = U \text{diag}(\sigma_1^2, \dots, \sigma_n^2)U^T \\
A^TA = V^T\Sigma^T \Sigma V = V \text{diag}(\sigma_1^2, \dots, \sigma_n^2)
\end{align}
$$
 convention: $\sigma_r = 0$ for $\min\{n,m\} < r \leq \max\{n,m\}$

>[!tip] SVD can be applied to the data matrix to identify the principal eigenvectors of the covariance matrix (PCA)

