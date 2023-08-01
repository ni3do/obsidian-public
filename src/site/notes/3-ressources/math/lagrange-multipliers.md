---
{"dg-publish":true,"permalink":"/3-ressources/math/lagrange-multipliers/","tags":["math/linear-algebra, eth/cil/theory"],"created":"","updated":""}
---

# Lagrange Multipliers
- strategy to find local maxima and minima of a function
- subject to a set of constraints

### Definition
Want the maximum or minimum of function $f(x)$ subject to the equality constraint $g(x) = 0$
$$\mathcal{L}(x, \lambda) := f(x) + \lambda g(x)$$
Now partial derivatives set to $0$:
$$\frac{\partial \mathcal{L}}{\partial x} \overset{!}{=} 0, \quad \frac{\partial \mathcal{L}}{\partial \lambda} \overset{!}{=} 0$$
The solution is always a saddle point of the initial Lagrangian function $\mathcal{L}(x, \lambda)$
