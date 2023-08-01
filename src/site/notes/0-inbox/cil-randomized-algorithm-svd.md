---
{"dg-publish":true,"permalink":"/0-inbox/cil-randomized-algorithm-svd/","tags":["math/linear-algebra, eth/cil/theory"],"created":"","updated":""}
---

# Randomized Algorithm for SVD
- SVD can be efficiently computed via random projections, gives control over accuracy vs. complexity trade-off
- 
### Definition
1. Generate random matrix with iid Gaussian entries
    $$R \in \mathbb{R}^{m \times 2k}$$
2. Calculate, by repeated matrix multiplications (e.g. $q=2$):
   $$Y = (AA^T)^q AR$$
3. Construct orthonormal basis for the image of $Y$ (with Gram-Schmidt)
---
### Usage
1. Compute orthogonal matrix $Q$ with few(er) columns
   $$A \approx QQ^T A$$
2. Do [[3-ressources/math/linear-algebra/singular-value-decomposition\|SVD]] on smaller matrix
   $$B := Q^T A = \tilde{U} \tilde{\Sigma} \tilde{V}^T$$
3. Extend it back to an approximate SVD for $A$
   $$A \approx{(Q \tilde{U}})\tilde{\Sigma}\tilde{V}^T $$  