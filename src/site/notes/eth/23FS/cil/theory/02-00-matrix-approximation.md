---
{"dg-publish":true,"permalink":"/eth/23-fs/cil/theory/02-00-matrix-approximation/","tags":["eth/cil/theory"],"created":"","updated":""}
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


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/02-01-recommender-systems/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




# Recommender Systems
We analyze patterns of interest in items (products, movies) and provide personalized recommendations for users.

</div></div>


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/02-02-collaborative-filtering/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




## Collaborative Filtering
We want to exploit collective data from many users and generalize across users, and possibly across items. 
Example applications are Amazon, Netflix, online advertising, etc.

</div></div>


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/02-03-netflix-data/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




## Netflix Data
Input: user-item preferences stored in a matrix
![02-netflix-data-vis.png](/img/user/eth/23FS/cil/theory/assets/02-netflix-data-vis.png)
Sparseness level can be very low, 1% and less

### Formal definition:
$n$ number of users (rows)
$m$ number of items (columns)
$\Omega$ observation matrix, where $w_{i j} = 1$ iff $a_{i j}$ is observed

</div></div>


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/02-04-preprocessing-normalization/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# 02-04-preprocessing-normalization

</div>



# Preprocessing / Normalization
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
$Z = \frac{X - \mu}{\sigma}$

</div></div>


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/02-06-convextiy-definition/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# 02-06-convextiy-definition

</div>



## Convexity Definition
> [!tip] A set in a vector space or affine space is convex if the line segment connecting any two points in the set is also in the set

>[!tip] A function $f$ is convex over a domain $R$, if for all $x,y \in R$ $f(tx + (1-t)y) \leq tf(x) + (1-t)f(y), \quad \forall t \in [0;1]$

If $f$ is differentiable, convexity is equivalent to the condition:
$f(x) \geq f(y) + \nabla f(y) (x-y), \quad \forall x,y \in R$
if $f$ is twice differentiable, convexity on a convex domain $R$ is equivalent to the condition:
$\nabla^2 f(x) \succeq \mathbf{0}, \quad \forall x \in \mathbf{Int}(R)$

Our scalar problem is non-convex (exception: $a = 0$), as there is a saddle point at the origin.
>[!tip] Convexity is a very fundamental property: demarcation line in optimization between tractable and (possibly) intractable problems

</div></div>


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/02-07-gradients/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# 02-07-gradients

</div>



## Gradients

Vector / Matrix notation
$\nabla_u l = Rv, \quad \nabla_vl = R^Tu, \quad R := (uv^T - A) $
## Hessian Map
$ \nabla^2 l(u,v) = \left( \begin{matrix}
					||v||^2 1_{n \times n} & 2uv^T - A\\
					(2uv^T - A)^T & ||u||^2 1_{m \times m}
					\end{matrix} \right)$
At the origin:
$\nabla^2 l(0,0) = \left( \begin{matrix}
					0 & -A\\
					-A^T & 0
					\end{matrix} \right)$
This is scalar to the mulitdimensional case. The hessian at zero is not [[knowledge/math/positive-semi-definit\|positive-semi-definit ]], unless $A$ is nilpotent (has all zero eigenvalues).

This problem is non-convex for all dimensions $m,n \geq 1$


</div></div>


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/02-08-gradient-dynamics/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# 02-08-gradient-dynamics

</div>



## Gradient Flow
>[!question] Can we gain analytic insights into the gradient dynamics?
>> [!tip] Use ODEs to study the gradient flow = gradient dynamics in the limit of small step sizes

Assume $u = v$, balanced initialization and they evolve identically.
We look at $x = uv = u^2$:
$
\begin{align}
\frac{du}{dt} &= -v(uv -a) \\
\frac{dx}{dt} &= \frac{du^2}{dt} = -2uv(uv-a) = -2x(x-a)
\end{align}
$
This ODE can be solved, yields:
$
x(t) = \frac{ae^{2at}}{e^{2at}-1+(a/c)} = a + \frac{ac - a^2}{ce^{2at} + a - c}$
![eth/23FS/cil/theory/assets/ode-solution.png](/img/user/eth/23FS/cil/theory/assets/ode-solution.png)

</div></div>

<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/eth/23-fs/cil/theory/02-09-fully-observed-rank-one-model/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# 02-09-fully-observed-rank-one-model

</div>



## Fully observed Rank 1 Model
Useful identiy:
$||R||_F^2 = \text{tr}(R^TR)$
We can then rewrite the [[eth/23FS/cil/theory/02-05-rank-one-model#Squared Error?!?\|objective]]:
$l(u,v) = \frac{1}{2}||A-uv^T||_F^2$
## Optimality Conditions
Directionality of $u,v$ is purely determined by the last term:
$
(u,v) \rightarrow \max\{u^T Av\}, \quad \text{s.t.} ||u|| = ||v|| = 1$
This can be solved with [[knowledge/lagrange-multipliers \| Lagrange multipliers]]:
$
\mathcal{L} = u^T Av - \lambda u \cdot u - \mu v \cdot v$
First order optimality condition:
$
\nabla_u \mathcal{L} = Av - 2\lambda u \overset{!}= 0 \Rightarrow u = \frac{Av}{||Av||}$


</div></div>

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

$<div class="markdown-embed-title">

# 02-10-eigenvector-equations

</div>


# Eigenvector Equations
By putting both [[eth/23FS/cil/theory/02-09-fully-observed-rank-one-model#Optimality Conditions\|optimality conditions]] together we get the *eigenvector equations*:
$u \propto (AA^T)u, \quad v \propto (A^TA)v$
$u$  should be proportional to the principal eigenvector of $AA^T$
$v$  should be proportional to the principal eigenvector of $A^TA$
Power iterations can be used for computation.

The generalization of this results in the [[eth/23FS/cil/theory/03-00-singular-value-decomposition\| Singular Value Decomposition]]


</div></div>
