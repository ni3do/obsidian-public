---
{"dg-publish":true,"permalink":"/4-archive/cil/theory/old/01-00-dimension-reduction/","tags":["eth/cil/theory"],"created":"","updated":""}
---

# Dimension Reduction
## Principal Component Analysis
Principal Component Analysis (PCA) is a dimensionality reduction technique in machine learning. It aims to find a new set of orthogonal variables, called principal components, that capture the maximum amount of variance in the original data. By projecting the data onto these components, PCA helps simplify and interpret complex datasets, enabling efficient analysis and visualization.
## Auto-Encoder Example
We want two functions, an encoder and a decoder:
$$F: \mathbb{R}^n \rightarrow \mathbb{R}^m, \quad\quad G: \mathbb{R}^m \rightarrow \mathbb{R}^n$$
To reconstruct we compose the two:
$$G \circ F: \mathbb{R}^n \rightarrow \mathbb{R}^m$$
We define a loss function:
$$l: \mathbb{R}^n \times \mathbb{R}^n \rightarrow \mathbb{R}$$
Quadratic loss:
$$l(x, \hat{x}) = \frac{1}{2}\|x - \hat{x}\|^2$$
