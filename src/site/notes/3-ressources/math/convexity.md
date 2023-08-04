---
{"dg-publish":true,"permalink":"/3-ressources/math/convexity/","tags":["math"],"created":"","updated":""}
---

# Convexity
>[!tip] Convexity is a very fundamental property: demarcation line in optimization between tractable and (possibly) intractable problems
**
### Definition Convex Function
A function $f$ is convex over a domain $R$, if for all $x,y \in R$ $$f(tx + (1-t)y) \leq tf(x) + (1-t)f(y), \quad \forall t \in [0;1]$$
If $f$ is differentiable, convexity is equivalent to the condition:
$$f(x) \geq f(y) + \nabla f(y) (x-y), \quad \forall x,y \in R$$
if $f$ is twice differentiable, convexity on a convex domain $R$ is equivalent to the condition:
$$\nabla^2 f(x) \succeq \mathbf{0}, \quad \forall x \in \mathbf{Int}(R)$$