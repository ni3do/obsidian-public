---
{"dg-publish":true,"permalink":"/4-archive/cil/theory/old/02-05-rank-one-model/","tags":["eth/cil/theory"],"created":"","updated":""}
---


# Rank 1 Model
>[!question] What is the simplest - yet interesting - matrix model that couples entires in each row and each column?
>> [!todo] The outer product model

Bi-linear model:
$$\begin{align}
A &\approx \mathbf{uv}^T, \quad u \in \mathbb{R}^n, v \in \mathbb{R}^m \\
a_{i j} &\approx u_i v_j
\end{align}$$
Non-identifiability: scalar $\alpha \neq 0$: $\mathbf{u} \leftarrow \alpha \mathbf{u}, \mathbf{v} \leftarrow \mathbf{(1/\alpha)\mathbf{v}}$
### Squared Error?!?
> [!danger] What is Hadamard Product?

$\mathbf{uv}^T$ is a **rank 1** matrix:
* can be represented as an outer product of two verctors
* every pair of vectors defines a rank 1 matrix via their outer product

### Scalar Problem
$$l(u,v) = \frac{1}{2}(a - uv)^2, \quad u,v \in \mathbb{R}$$
This induces following gradient field:

![4-archive/cil/theory/old/assets/02-gradient-field.png| 500](/img/user/4-archive/cil/theory/old/assets/02-gradient-field.png)

Minimas: **hyperbola with two branches** (red lines)
Use gradient descent.
#### Saddle point
Origin is a saddle point:
![4-archive/cil/theory/old/assets/02-origin-saddle-point.png| 600](/img/user/4-archive/cil/theory/old/assets/02-origin-saddle-point.png)

#### Characteristic Polynomial
$$det(\lambda\mathbf{I} - \nabla^2l(0,0) = \lambda^2 -a^2 = (\lambda - a)(\lambda + a)$$
The Hessian is indefinite at (0,0) as it has eigenvalues $\pm a$