---
{"dg-publish":true,"permalink":"/eth/23-fs/cil/theory/03-00-singular-value-decomposition/","tags":["eth/cil/theory"],"created":"","updated":""}
---

# [[knowledge/singular-value-decomposition\| Singular Value Decomposition]]

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
![eth/23FS/cil/theory/assets/reduced-svd.png](/img/user/eth/23FS/cil/theory/assets/reduced-svd.png)


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/03-01-eckart-young-theorem/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# 03-01-eckart-young-theorem

</div>



# Eckart Young Theorem
>[!tip] By pruning the singular values below $\sigma_k$ in the SVD representation, we get an optimal rank $k$ approximation of a matrix
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

