---
{"dg-publish":true,"permalink":"/0-inbox/pooling-layer/","tags":["machine-learning, eth/cil/theory"],"created":"","updated":""}
---

# Pooling Layer
- slide 2D filter over each channel and summarize features within the covered region
- reduces dimensions of the feature maps
- max-pooling
- average-pooling

### Definition max-pooling
$$z_{i}(u,v) = \max_{(\delta u, \delta v) \in \nabla} x_{i, (u+\delta u, v + \delta v)}$$