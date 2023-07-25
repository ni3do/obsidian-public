---
{"dg-publish":true,"permalink":"/eth/23-fs/cil/theory/02-04-preprocessing-normalization/","tags":["eth/cil/theory"],"created":"","updated":""}
---

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
$$Z = \frac{X - \mu}{\sigma}$$