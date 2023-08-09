---
{"dg-publish":true,"permalink":"/4-archive/cil/theory/old/03-05-np-hard/","tags":["eth/cil/theory"],"created":"","updated":""}
---

# NP Hardness
Weighted [[3-ressources/math/frobenius-norm\|Forbenius norm]] problem:
$$\hat{A}_k = \arg\min \left\{\sum_{i,j} (w_{i,j} a_{ij} - b_{ij})^2\right\}, \quad \text{rank}(B) = k$$

* special case: $w_{ij} = w_{ij} \in \{0,1\}$, **?!!? maybe $w_{ij} = w_{ji}$**
This is [[3-ressources/math/np-hard\|NP-hard]] even for $k=1$

>[!tip] Low rank matrix reconstruction is NP hard and one has - in general - to resort to approximation algorithms. The completely observed case is special.

