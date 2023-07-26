---
{"dg-publish":true,"permalink":"/eth/23-fs/cil/theory/03-00-singular-value-decomposition/","tags":["eth/cil/theory"],"created":"","updated":""}
---


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/knowledge/math/singular-value-decomposition/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# SVD

</div>



# [[knowledge/math/singular-value-decomposition\| Singular Value Decomposition]]

## SVD Theorem
For each matrix $A \in \mathbb{R}^{n \times m}$, there exist orthogonal matrixes $U \in \mathbb{R^{n \times n}}$ and $V \in \mathbb{R}^{m \times m}$ such tat $A$ can be expressed as:
$
A = U\Sigma V^T, \quad \Sigma= \text{diag}(\sigma_1, \dots, \sigma_{\text{min}\{n,m\}}), \quad \sigma_i \geq \sigma_{i+1} \geq 0 \quad \forall i$
* The set of singular values is unique
* Left/right singular vectors (columns or $U$ and $V$) can have arbitrary sign

## Computation Complexity
>[!tip] SVD is computable in $\mathcal{O}(\min\{nm^2, mn^2\}$


## SVD and Frobenius norm
Let the SVD of $A \in \mathbb{R}^{n \times m}$ be given by $A ) U\Sigma V^T$, then:
$||A||_F^2 = \sum_{i=1}^{\min{n,m}}\sigma_i^2$
## SVD and Spectral norm
Let the SVD of $A \in \mathbb{R}^{n \times m}$ be given by $A ) U\Sigma V^T$, then:
$
||A||_2 := \sup\{||Ax||: ||x|| = 1\} = \sigma_1$
## Reduced SVD
One can often prune columns of $U$ or $V$ corresponding to zero elements in $\Sigma$ (or zero-padded columns/rows)
![eth/23FS/cil/theory/assets/reduced-svd.png](/img/user/eth/23FS/cil/theory/assets/reduced-svd.png)

</div></div>



<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/03-01-eckart-young-theorem/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# 03-01-eckart-young-theorem

</div>



# Eckart Young Theorem
>[!tip] By pruning the singular values below $\sigma_k$ in the [[knowledge/math/singular-value-decomposition\|SVD]] representation, we get an optimal rank $k$ approximation of a matrix
>
* Is fundamental to many low-rank approximation problems
* This means that approximations for any $k$ can directly be read-off the SVD
## Formal definition:
>[!tip] Given $A \in \mathbb{R}^{n \times m}$ with SVD $A = U \Sigma V^T$. Then for all $1 \leq k \leq \min{n,m}$:
>$
>\begin{align}
>A_k &:= U \text{diag}(\sigma_1, \dots, \sigma_k) V^T\\
>	&\in \arg\min\{||A-B||_F: \text{rank}(B) \leq k\}
>\end{align}
>$

## Corollary
The squared error of low rank approximations can be expressed as:
$
||A-A_k||_F^2 = \sum_{i=k+1}^{\text{rank}(A)}\sigma_i^2$
Proof:
$
A - A_k = U \text{diag}(0, \dots, 0, \dots, \sigma_{k+1}, \dots, \sigma_{\min\{n,m\}})V^T$


</div></div>


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/03-02-svd-pca/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# 03-02-svd-pca

</div>



# SVD and PCA
[[knowledge/math/singular-value-decomposition\|SVD]] is intimately related to [[knowledge/eigendecomposition\|eigendecomposition]]
* $A$ is square and symmetric: $U$ and $V$ have equal columns up to possible sign differences
* if $A$ is [[knowledge/math/positive-semi-definit\|positive semi-definit]], then the SVD is equal to the [[knowledge/eigendecomposition\|eigendecomposition]]
* Squares of $A$: $AA^T \in \mathbb{R}^{n \times n}$ as well as $A^TA \in \mathbb{R}^{m \times m}$: 
  $
  \begin{align}
	AA^T = U\Sigma \Sigma^T U^T = U \text{diag}(\sigma_1^2, \dots, \sigma_n^2)U^T \\
	A^TA = V^T\Sigma^T \Sigma V = V \text{diag}(\sigma_1^2, \dots, \sigma_n^2)
	\end{align}
 $
 convention: $\sigma_r = 0$ for $\min\{n,m\} < r \leq \max\{n,m\}$

>[!tip] SVD can be applied to the data matrix to identify the principal eigenvectors of the covariance matrix (PCA)


</div></div>


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/03-03-svd-matrix-completion/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# 03-03-svd-matrix-completion

</div>



# SVD and Matrix Completion
We generalize the simple rank 1 model to a rank $k$ approximation.
We do this by additive superposition of $k$ rank 1 matrices.
If all matrix entries are completely obeserved, the solution is constructively given by the [[knowledge/math/singular-value-decomposition\|SVD]].

$k$ principal left singular vectors, paired with the respective right singular vector form outer products:
$
A \approx \sum_{i=1}^{k}\sigma_i u_i v_i^T$
>[!tip] Low-rank matrix approximation is non-convex, even for the completely observed case


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/knowledge/math/singular-value-decomposition/#computation-complexity" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# SVD

</div>


## Computation Complexity
>[!tip] SVD is computable in $\mathcal{O}(\min\{nm^2, mn^2\}$



</div></div>




</div></div>

