---
{"dg-publish":true,"permalink":"/0-inbox/glove-model/","tags":["machine-learning, eth/cil/theory"],"created":"","updated":""}
---

# Global Word Vector Model (GloVe)
- phrase word embeddings problem as matrix factorization problem
- we try to factorize the co-occurence matrix
- no need to normalize, because its doesn't degenerate because it uses two-sided objective
- not all events can have high probability, as they "compete" for probability mass
- GloVe objective with bi-linear embedding model can be thought of in terms of low-rank matrix factorization

### Log-Likelihood Function
$$l(\theta, N) = \sum_{v,w: N_{vw} > 0} f(N_{vw}) \left( \ln N_{vw} - \ln \hat{N}_{vw} \right)^2, \quad \hat{N}_{vw} = \tilde{p}(v, w; \theta)$$
