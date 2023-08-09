---
{"dg-publish":true,"permalink":"/4-archive/cil/theory/old/02-07-gradients/","tags":["eth/cil/theory"],"created":"","updated":""}
---

## Gradients

Vector / Matrix notation
$$\nabla_u l = Rv, \quad \nabla_vl = R^Tu, \quad R := (uv^T - A) $$
## Hessian Map
$$ \nabla^2 l(u,v) = \left( \begin{matrix}
					||v||^2 1_{n \times n} & 2uv^T - A\\
					(2uv^T - A)^T & ||u||^2 1_{m \times m}
					\end{matrix} \right)$$
At the origin:
$$\nabla^2 l(0,0) = \left( \begin{matrix}
					0 & -A\\
					-A^T & 0
					\end{matrix} \right)$$
This is scalar to the mulitdimensional case. The hessian at zero is not [[3-ressources/math/positive-semi-definit\|positive-semi-definit ]], unless $A$ is nilpotent (has all zero eigenvalues).

This problem is non-convex for all dimensions $m,n \geq 1$
