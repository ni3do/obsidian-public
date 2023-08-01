---
{"dg-publish":true,"permalink":"/1-projects/cil/theory/old/02-06-convextiy-definition/","tags":["eth/cil/theory"],"created":"","updated":""}
---

## Convexity Definition
> [!tip] A set in a vector space or affine space is convex if the line segment connecting any two points in the set is also in the set

>[!tip] A function $f$ is convex over a domain $R$, if for all $x,y \in R$ $$f(tx + (1-t)y) \leq tf(x) + (1-t)f(y), \quad \forall t \in [0;1]$$

If $f$ is differentiable, convexity is equivalent to the condition:
$$f(x) \geq f(y) + \nabla f(y) (x-y), \quad \forall x,y \in R$$
if $f$ is twice differentiable, convexity on a convex domain $R$ is equivalent to the condition:
$$\nabla^2 f(x) \succeq \mathbf{0}, \quad \forall x \in \mathbf{Int}(R)$$

Our scalar problem is non-convex (exception: $a = 0$), as there is a saddle point at the origin.
>[!tip] Convexity is a very fundamental property: demarcation line in optimization between tractable and (possibly) intractable problems