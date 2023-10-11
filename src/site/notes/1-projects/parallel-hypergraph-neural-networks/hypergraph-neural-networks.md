---
{"dg-publish":true,"permalink":"/1-projects/parallel-hypergraph-neural-networks/hypergraph-neural-networks/","tags":["eth/hpc"],"created":"","updated":""}
---

# [Hypergraph Neural Networks Paper](https://arxiv.org/abs/1809.09401)
- Hypergraph neural networks framework
- encodes high-order data correlation in a hypergraph structure

- hypergraphs are employed in many computer vision tasks such as classification and retrieval tasks
- Learning methods suffer from high computation complexity and storage costs

## HGNN Proposal
- representation learning using hypergraph structure
- efficient by using hyperedge convolution operations
- good with multi-modal data


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/1-projects/parallel-hypergraph-neural-networks/hypergraph-definition/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

$<div class="markdown-embed-title">

# hypergraph-definition

</div>



# Hypergraph
A hypergraph is defined as:
- $\mathcal{G} = (\mathcal{V}, \mathcal{E}, \boldsymbol{W})$
- vertex set $\mathcal{V}$
- hyperedge set $\mathcal{E}$
- weight matrix $\boldsymbol{W}$, each hyperedge is assigned with a weight
- incidence matrix $\boldsymbol{H}$ defines $\mathcal{G}$, dimensions $\lvert \mathcal{V} \rvert \times \lvert \mathcal{E} \rvert$ 
$h(v, e) = \begin{cases}
1, &\text{if } v \in e\\ \\
0, &\text{if } v \notin e
\end{cases}$
- weight function for vertex $v$ is $d(v) = \sum_{e \in \mathcal{E}} w(e) h(v, e)$
- weight function for edge $e$ is $d(e) = \sum_{v \in \mathcal{V}} h(v, e)$
- $D_{e}$ and $D_{v}$ diagonal matrices of edge and vertex degrees

</div></div>

## Node Classification on Hypergraphs

## Related Work
