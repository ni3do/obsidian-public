---
{"dg-publish":true,"permalink":"/4-archive/cil/theory/old/02-08-gradient-dynamics/","tags":["eth/cil/theory"],"created":"","updated":""}
---

## Gradient Flow
>[!question] Can we gain analytic insights into the gradient dynamics?
>> [!tip] Use ODEs to study the gradient flow = gradient dynamics in the limit of small step sizes

Assume $u = v$, balanced initialization and they evolve identically.
We look at $x = uv = u^2$:
$$
\begin{align}
\frac{du}{dt} &= -v(uv -a) \\
\frac{dx}{dt} &= \frac{du^2}{dt} = -2uv(uv-a) = -2x(x-a)
\end{align}
$$
This ODE can be solved, yields:
$$
x(t) = \frac{ae^{2at}}{e^{2at}-1+(a/c)} = a + \frac{ac - a^2}{ce^{2at} + a - c}$$
![4-archive/cil/theory/old/assets/ode-solution.png](/img/user/4-archive/cil/theory/old/assets/ode-solution.png)