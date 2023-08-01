---
{"dg-publish":true,"permalink":"/1-projects/cil/theory/old/03-03-svd-matrix-completion/","tags":["eth/cil/theory"],"created":"","updated":""}
---

# SVD and Matrix Completion
We generalize the simple rank 1 model to a rank $k$ approximation.
We do this by additive superposition of $k$ rank 1 matrices.
If all matrix entries are completely obeserved, the solution is constructively given by the [[3-ressources/math/linear-algebra/singular-value-decomposition\|SVD]].

$k$ principal left singular vectors, paired with the respective right singular vector form outer products:
$$
A \approx \sum_{i=1}^{k}\sigma_i u_i v_i^T$$
>[!tip] Low-rank matrix approximation is non-convex, even for the completely observed case


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3-ressources/math/linear-algebra/singular-value-decomposition/#computation-complexity" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# SVD

</div>


## Computation Complexity
>[!tip] SVD is computable in $\mathcal{O}(\min\{nm^2, mn^2\}$



</div></div>


