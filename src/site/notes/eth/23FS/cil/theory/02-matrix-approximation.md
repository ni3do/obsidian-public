---
{"dg-publish":true,"permalink":"/eth/23-fs/cil/theory/02-matrix-approximation/","tags":["eth,cil-theory"],"created":"","updated":""}
---

# Matrix Approximation
Goal: Matrix Completion
Assume we have a sparse matrix $A$
> [!question] Can we fill in the missing entries and reconstruct the matrix?

> [!question] What makes a matrix a matrix (and not just a vector)?
> > [!todo] The identity of columns and rows!

So our minimal assumption must be that entries within the same row or the same column are not independent.

We do this via **conditional independence**:
![02-conditional-independence-def.png](/img/user/eth/23FS/cil/theory/assets/02-conditional-independence-def.png)

## Recommender Systems
We analyze patterns of interest in items (products, movies) and provide personalized recommendations for users.
## Collaborative Filtering
We want to exploit collective data from many users and generalize across users, and possibly across items. 
Example applications are Amazon, Netflix, online advertising, etc.

## Netflix Data
Input: user-item preferences stored in a matrix
![02-netflix-data-vis.png](/img/user/eth/23FS/cil/theory/assets/02-netflix-data-vis.png)
Sparseness level can be very low, 1% and less

### Formal definition:
$n$ number of users (rows)
$m$ number of items (columns)
$\Omega$ observation matrix, where $w_{i j} = 1$ iff $a_{i j}$ is observed

## Preprocessing / Normalization
### Centering
>[!tip] make rows/columns more comparable and subtract out rating bias

Mean rating per user/item
![02-mean-row-col.png](/img/user/eth/23FS/cil/theory/assets/02-mean-row-col.png)
This lets us center the data:
![02-data-centering.png](/img/user/eth/23FS/cil/theory/assets/02-data-centering.png)
### Variance Normalization
$\mu = \textbf{E}[X]$
$\sigma^2 = \textbf{Var}[X]$
Then the noramlized scores or z-scores are:
$$Z = \frac{X - \mu}{\sigma}$$
## Rank 1 Model
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

![02-gradient-field.png| 500](/img/user/eth/23FS/cil/theory/assets/02-gradient-field.png)

Minimas: **hyperbola with two branches** (red lines)
Use gradient descent.
#### Saddle point
Origin is a saddle point:
![[02-origin-saddle-point.png \| 600]]

#### Characteristic Polynomial
$$det(\lambda\mathbf{I} - \nabla^2l(0,0) = \lambda^2 -a^2 = (\lambda - a)(\lambda + a)$$
The Hessian is indefinite at (0,0) as it has eigenvalues $\pm a$
## Convexity Definition
> [!tip] A set in a vector space or affine space is convex if the line segment connecting any two points in the set is also in the set

>[!tip] A function $f$ is convex over a domain $R$, if for all $x,y \in R$ $$f(tx + (1-t)y) \leq tf(x) + (1-t)f(y), \quad \forall t \in [0;1]$$

If $f$ is differentiable, convexity is equivalent to the condition:
$$f(x) \geq f(y) + \nabla f(y) (x-y), \quad \forall x,y \in R$$
if $f$ is twice differentiable, convexity on a convex domain $R$ is equivalent to the condition:
$$\nabla^2 f(x) \succeq \mathbf{0}, \quad \forall x \in \mathbf{Int}(R)$$

Our scalar problem is non-convex (exception: $a = 0$), as there is a saddle point at the origin.
>[!tip] Convexity is a very fundamental property: demarcation line in optimization between tractable and (possibly) intractable problems

## Gradients

