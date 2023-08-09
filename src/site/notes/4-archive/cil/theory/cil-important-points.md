---
{"dg-publish":true,"permalink":"/4-archive/cil/theory/cil-important-points/","tags":["eth/cil/theory"],"created":"","updated":""}
---

# CIL Important Points
eigenvalues of $X^TX$ are singular values of $X$ squared
- Norms:
	- Nuclear Norm:
		- is convex envelope of rank function
		  $\lvert\lvert A \rvert\rvert_{*} = \sum_{i=1}^{\text{rank}(A)} \sigma_{i}$
	- Frobenius Norm
	- l2 norm
		$\lvert\lvert A \rvert\rvert_{2} = \sum_{j=1}^n \lvert\lvert a_{j} \rvert\rvert_{2}$
		$\lvert\lvert A \rvert\rvert_{2} = \sigma_{1}$
- 

## General
- sample variance: $\frac{1}{N} \sum_{i=0}^N (x_{i} - \mu)^2$
- Reconstruction Error: $\frac{1}{N}\lvert\lvert P - \hat{P} \rvert\rvert_{F}^2$
- $\cos^2(x) + \sin^2(x) = 1$
- For centered data, $x$, the reconstruction loss of a projection matrix is $\frac{1}{2} (\text{Var}(x) - \text{Var}(Px))$
	- $\text{Var}(Px) = \text{trace}(PE[xx^T])$
- Normalize data $X$ with variance $1$: $Z = \frac{X - \boldsymbol{E}[X]}{\text{Var}[X]}$

---
## Latent Variable Models
- conditional independence assumption
	- $p(w | d, z) = p(w | z)$
	- prob of a word is only dependent on the topic and not on the document
- K-means:
	- deterministic assignments to clusters
	- clusters are spherical
- GMM:
	- probabilistic assignments to clusters
	- clusters are ellipsoid
- Adam:
	- $g_{i}^k = \beta g_{i}^{k-1} + (1-\beta) d_{i} l(\Theta^k)$
	- $h_{i}^k = \alpha h_{i}^{k-1} + (1-\alpha) (d_{i} l(\Theta^k))^2$
	- $\Rightarrow$ $\Theta_{i}^{k+1} = \Theta_{i}^k - \eta_{i}^k g_{i}^k$, with $\eta_{i}^k = \frac{\eta}{\sqrt{h_{i}^k} + \delta}$
---
## Linalg Stuff
 -  If $f1(x), f2(x), . . . , fk(x)$ are convex functions defined on a convex set $C \subset R^n$, then $f (x) = f1(x) + f2(x) + · · · + fk(x)$ is convex on C.
 - Furthermore, if at least one of the functions $fi(x), i = 1, 2, . . . , k$ is strictly convex on C, then f (x) is strictly convex on C.
- If f (x) is convex on a convex set $C \subset R^n$, and if $\alpha > 0$, then $\alpha f (x)$ is convex on C.
- If f (x) is strictly convex on a convex set $C \subset R^n$, and if $\alpha > 0$, then $\alpha f (x)$ is strictly convex on C.
- If f (x) is convex on a convex set $C \subset R^n$, and if g(y) is an increasing convex function defined on the range of f (x, then the composition g(f (x)) is convex on C.
- If f (x) is strictly convex on a convex set $C \subset R^n$, and if g(y) is a strictly increasing convex function defined on the range of f (x, then the composition g(f (x)) is strictly convex on C
- sum of two symmetric matrices is symmetric
- principal components are always normalized (they stem from an orthonormal matrix)
- symmetric matrices have orthogonal eigenvectors: $u^Tv = 0$
- Orthogonal matrixes preserve euclidean norm
- idempotence of projection: $P^2 = P$
- Self-adjoint: $\langle P(x), y\rangle = \langle x, P(y) \rangle$
	- projection over Hilbert space is orthogonal if it is self-adjoint
- $\nabla_{R} \frac{1}{2} \lvert\lvert R \rvert\rvert_{F}^2 = R$
- $\text{tr}(R^TR) = \lvert\lvert R \rvert\rvert_{F}^2$
- two linear maps $L: V \rightarrow V'$, $L': V' \rightarrow V''$:
	- $\text{rank}(L' \circ L) \leq \min\{ \text{rank}(L), \text{rank(L')}\}$
	- if $\text{im}(L) \cap \text{ker}(L') = \{0\}$, then equality holds
- $\text{rank}(AB) = \min(\text{rank}(A), \text{rank}(B))$
- $\mid \langle u, x\rangle\mid = \mid \cos(u,x) \mid \lvert\lvert x \rvert\rvert \lvert\lvert u \rvert\rvert$
- $V^T = (V^TV)^{-1}V^T$
	- for any $V: V^T = \arg\min_{w} R(W,V)$
- Spectral theorem:
	- For $\Sigma$ symmetric and positive semidefinite:
	- $\Sigma = Q \Lambda Q^T, \quad \Lambda = \text{diag}(\lambda_{1, \dots, \lambda_{n}}, \quad \lambda_{1} \geq \lambda_{n} \geq 0$
- Definitheit:
	- positive: $x^T A x > 0, \quad \forall x \neq 0$
	- positive semi: $x^TAx \geq 0, \quad \forall x \neq 0$
	- negative: $x^T A x < 0, \quad \forall x \neq 0$
	- negative semi: $x^T A x \leq 0, \quad \forall x \neq 0$
	- indefinite: else
- if $A$ is symmetric:
	- eigenvalues are real
	- positive $\iff \lambda_{i} > 0$
	- positive semi $\iff \lambda_{i} \geq 0$
	- negative $\iff \lambda_{i} < 0$
	- negative semi $\iff \lambda_{i} \leq 0$
- Convexity:
	- $f(tx + (1-t)y) \leq tf(x) + (1-t)f(y)$
	- if $f$ is differentiable:
		- $f(x) \geq f(y) + \nabla f(y)(x-y)$
	- if $f$ is twice differentiable:
		- $\nabla^2 f(x) \succeq 0$  positive semi definite
- $\lvert\lvert A \rvert\rvert_{F}^2 = \sum_{i=1}^{\min(n,m)} \sigma_{i}^2$
- $\lvert\lvert A \rvert\rvert_{2} = \sup\{\lvert\lvert Ax \rvert\rvert: \lvert\lvert x \rvert\rvert = 1\} = \sigma_{1}$
- $\text{trace}(A^T B) = \text{trace}(AB^T) = \text{trace}(B^T A) = \text{trace}(BA^T)$
- $\text{trace}(AB) = \text{trace}(BA)$
- $\text{trace}(ABC) = \text{trace}(CAB)$, but $\text{trace}(ABC) \neq \text{trace}(ACB)$
- $\text{trace}(A) = \sum_{i=1}^n \lambda_{i}$ if $A \in \mathbb{R}^{n \times n}$
- if $A = UDV^T \rightarrow \lvert\lvert A \rvert\rvert_{*} = \text{trace}(D)$
- $\mu$-strongly convex (for differentiable function $f$)
	- $f(b) \geq f(a) + \langle f(a), b-a \rangle + \frac{\mu}{2} \lvert\lvert b - a \rvert\rvert^2, \quad \forall b,a$
	- positive definite quadratic function is strongly convex with $\mu = \lambda_{\min}$
- twice differentiable:
	- $0 \prec \mu I \preceq \nabla^2 f(b) \preceq fI, \quad \forall b$
	- $f$ is $\mu$-strongly convex $\Rightarrow$ $f$ satisfies PL-condition with $\mu$
- PL-condition
	- $\frac{1}{2} \lvert\lvert \nabla f(\Theta) \rvert\rvert^2 \geq \mu(f(\Theta) - f^*), \quad \forall \Theta$
	- $l^* = \min_{\Theta} f(\Theta)$
---