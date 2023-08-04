---
{"dg-publish":true,"permalink":"/0-inbox/activation-functions/","tags":["machine-learning, eth/cil/theory"],"created":"","updated":""}
---

# Activation Functions
## Rectified Linear Unit (ReLU)
### Definition
$$\begin{align}
f(x) &= \max(0, x) \\
f'(x) &= \begin{cases}
0 \text{ for } x \leq 0 \\
1 \text{ for } x > 0
\end{cases}
\end{align}$$


## Sigmoid Activation Function
### Definition
$$\begin{align}
\sigma(x) &= \frac{1}{1 + e^{-x}} = \frac{e^x}{e^x + 1} \\
\sigma'(x) &= \sigma(x) (1 - \sigma(x))
\end{align}$$
## Hyperbolic Tangent Function
### Definition
$$\begin{align}
\tanh(x) &= \frac{e^x - e^{-x}}{e^x + e^{-x}} \\
\tanh'(x) &= 1 - \tanh^2(x)
\end{align}$$
