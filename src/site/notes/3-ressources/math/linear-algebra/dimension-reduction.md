---
{"dg-publish":true,"permalink":"/3-ressources/math/linear-algebra/dimension-reduction/","tags":["math/linear-algebra, eth/cil/theory"],"created":"","updated":""}
---

# 1. Dimension Reduction
## 1.1.1 Motivation
* Find low dimensional representation of data, while preserving the content
## 1.2 Linear Autoencoder
The linear autoencoder is obtained by identifying F, G with linear maps
Linear encode:
$$F: x \mapsto z = Wx $$
Linear decoder:
$$G: z \mapsto \hat{x} = Vz$$
This leads to following **Risk**:
$$\mathcal{R}(W, V) = \mathcal{P := VW} = \mathbb{E}\left[ \frac{1}{2} \mid\mid x-Px\mid\mid^2 \right]$$
* linearity comes with a powerful arsenal of analytic tools
* if we compose linear maps, the resulting map is linear

### Def 1.2.1 Centering
The data is centered, if $\mathbb{E}[x] = 0$. Data can be centered by transforming $x \leftarrow x − \mathbb{E}[x]$, i.e. by subtracting the mean.
**For centered data and the squared loss: optimal affine reconstruction maps are linear.**

The weight matrices found for linear maps are non-identifiable and one needs to be careful not to over-interpret the found representation.

The reconstruction map of a linear autoencoder is of rank less or equal to m. The bottleneck layer constitutes a rank constraint.

## 1.3 Projection
#### Orthogonal Projection
For given subspace U the optimal reconstruction map P is the matrix represent- ing the orthogonal projection ΠU . The optimal linear autoencoder represents a projection.

The optimal weight matrix of the autoencoder with tied parameter matrices $V = W^T$ is orthogonal.

## 1.4 PCA
For centered data, the optimal autoencoder represents the projection P which maximizes the variance.

#### Sufficient Statistics
The optimal projection is fully determined by the covariance matrix of the data, i.e. $\mathbb{E}[xx^T]$ are sufficient statistics (together with $\mathbb{E}[x]$ used in centering).

