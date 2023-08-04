---
{"dg-publish":true,"permalink":"/3-ressources/machine-learning/evidence-lower-bound/","tags":["machine-learning, eth/cil/theory"],"created":"","updated":""}
---

# Evidence Lower Bound
- yields approximate, often tractable objective functions

### Definition
$$l(\theta) = \sum_{t=1}^s \ln \sum_{z=1}^k \pi_{z} p(x;\theta_{z}) \geq \sum_{t=1}^s \sum_{z=1}^k q_{tz} \left[\ln \pi_{z} + \ln p(x_{t}; \theta_{z}) - \ln q_{tz} \right]$$
Where $q$ is a vector of convex weights for each sample, ($q_{tk}$ denotes the probability that sample $t$  is part of the $k$-th cluster, intuitively)

### Derive ELBO (CIL-style)
Starting with some loss function $l(\theta)$:
$$\begin{align}
l(\theta) = \sum_{t=1}^s \ln \sum_{z=1}^k \pi_{z} p(x;\theta_{z}) &= \sum_{t=1}^s \ln \sum_{z=1}^k \frac{q_{tz} \pi_{z} p(x;\theta_{z})}{q_{tz}}\\
&\geq \sum_{t=1}^s \sum_{z=1}^k q_{tz} \ln \frac{\pi_{z} p(x;\theta_{z})}{q_{tz}} \\
&= \sum_{t=1}^s \sum_{z=1}^k q_{tz} \left(\ln \pi_{z} + \ln p(x;\theta_{z}) - \ln q_{tz}\right)
\end{align}$$
Where we used [[3-ressources/math/jensen-inequality\|Jensens inequality]] with $q_{tz}$ as the positive parameters:

<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3-ressources/math/jensen-inequality/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# jensen-inequality

</div>



# Jensen Inequality
### Definition Finite Form
For real convex function $\varphi$ and positive weights $a_{i}$
$\varphi \left( \frac{\sum a_{i}x_{i}}{\sum a_{i}} \right) \leq \left( \frac{\sum a_{i} \varphi(x_{i})}{\sum a_{i}} \right)$

</div></div>
