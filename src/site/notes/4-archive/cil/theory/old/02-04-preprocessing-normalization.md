---
{"dg-publish":true,"permalink":"/4-archive/cil/theory/old/02-04-preprocessing-normalization/","tags":["eth/cil/theory"],"created":"","updated":""}
---

# Preprocessing / Normalization
### Centering
>[!tip] make rows/columns more comparable and subtract out rating bias

Mean rating per user/item
![4-archive/cil/theory/old/assets/02-mean-row-col.png](/img/user/4-archive/cil/theory/old/assets/02-mean-row-col.png)
This lets us center the data:
![4-archive/cil/theory/old/assets/02-data-centering.png](/img/user/4-archive/cil/theory/old/assets/02-data-centering.png)
### Variance Normalization
$\mu = \textbf{E}[X]$
$\sigma^2 = \textbf{Var}[X]$
Then the noramlized scores or z-scores are:
$$Z = \frac{X - \mu}{\sigma}$$