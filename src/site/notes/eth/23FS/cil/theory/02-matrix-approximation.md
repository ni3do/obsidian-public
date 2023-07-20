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
