---
{"dg-publish":true,"permalink":"/eth/23-fs/cil/theory/03-04-svd-with-imputation/","tags":["eth/cil/theory"],"created":"","updated":""}
---

# SVD with Imputation
Naive strategy:
	1. estimate values for missing matrix elements (e.g. row or column mean)
	2. impute them to create a complete matrix
	3. run [[knowledge/math/singular-value-decomposition\|SVD]] to compute low rank approximation

>[!warning] This is not a good idea

If we have an incomplete observation, [[knowledge/math/singular-value-decomposition\|SVD]] is in general not applicable directly to compute low-rank approximations.
