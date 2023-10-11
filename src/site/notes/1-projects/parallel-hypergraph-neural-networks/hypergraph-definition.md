---
{"dg-publish":true,"permalink":"/1-projects/parallel-hypergraph-neural-networks/hypergraph-definition/","tags":["eth/hpc"],"created":"","updated":""}
---

# Hypergraph
A hypergraph is defined as:
- $\mathcal{G} = (\mathcal{V}, \mathcal{E}, \boldsymbol{W})$
- vertex set $\mathcal{V}$
- hyperedge set $\mathcal{E}$
- weight matrix $\boldsymbol{W}$, each hyperedge is assigned with a weight
- incidence matrix $\boldsymbol{H}$ defines $\mathcal{G}$, dimensions $\lvert \mathcal{V} \rvert \times \lvert \mathcal{E} \rvert$ 
$$h(v, e) = \begin{cases}
1, &\text{if } v \in e\\ \\
0, &\text{if } v \notin e
\end{cases}$$
- weight function for vertex $v$ is $d(v) = \sum_{e \in \mathcal{E}} w(e) h(v, e)$
- weight function for edge $e$ is $d(e) = \sum_{v \in \mathcal{V}} h(v, e)$
- $D_{e}$ and $D_{v}$ diagonal matrices of edge and vertex degrees