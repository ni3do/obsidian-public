---
{"dg-publish":true,"permalink":"/4-archive/cil/theory/old/03-04-svd-with-imputation/","tags":["eth/cil/theory"],"created":"","updated":""}
---

# SVD with Imputation
Naive strategy:
	1. estimate values for missing matrix elements (e.g. row or column mean)
	2. impute them to create a complete matrix
	3. run [[3-ressources/math/linear-algebra/singular-value-decomposition\|SVD]] to compute low rank approximation

>[!warning] This is not a good idea

If we have an incomplete observation, [[3-ressources/math/linear-algebra/singular-value-decomposition\|SVD]] is in general not applicable directly to compute low-rank approximations.
