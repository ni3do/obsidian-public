---
{"dg-publish":true,"permalink":"/3-ressources/machine-learning/probabilistic-latent-semantic-analysis/","tags":["machine-learning, nlp, eth/cil/theory"],"created":"","updated":""}
---

# Probabilistic Latent Semantic Analysis (pLSA)
- derive a low-dimensional representation of the observed variables in terms of their affinity to certain hidden variables
- assign each word occurence a topic
- document $d$, word $w$, topic $z$
### Definition
1. Define a distribution over the latent (i.e. topic) variables
	- document is characterized by a distribution over topics: $p(z | d)$
2. Define a conditional distribution of a word given a topic
	- topics are represented as distributions over words: $p(w | z)$
Use two stage sampling process:
1. Sample a topic from $p(z | d)$
2. Sample a token given the topic from $p(w | z)$

### Log-Likelihood
$$l(\theta;N) = \log p(N; \theta) = \sum_{i,j} N_{ij} \log p(w_{j}|d_{i}), \quad p(w_{j}|d_{i}) = \sum_{t=1}^k p(w_{j}|z_{t})p(z_{t}|d_{i})$$
