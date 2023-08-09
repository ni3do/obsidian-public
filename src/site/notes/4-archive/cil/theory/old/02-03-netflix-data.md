---
{"dg-publish":true,"permalink":"/4-archive/cil/theory/old/02-03-netflix-data/","tags":["eth/cil/theory"],"created":"","updated":""}
---

## Netflix Data
Input: user-item preferences stored in a matrix
![4-archive/cil/theory/old/assets/02-netflix-data-vis.png](/img/user/4-archive/cil/theory/old/assets/02-netflix-data-vis.png)
Sparseness level can be very low, 1% and less

### Formal definition:
$n$ number of users (rows)
$m$ number of items (columns)
$\Omega$ observation matrix, where $w_{i j} = 1$ iff $a_{i j}$ is observed