---
{"dg-publish":true,"permalink":"/3-ressources/math/linear-algebra/nuclear-norm-minimization/","tags":["math/linear-algebra, eth/cil/theory"],"created":"","updated":""}
---

# Nuclear Norm Minimization
- iterative algorithm
- applies [[3-ressources/math/linear-algebra/cil-shrink-operator\|shrink operator]] consecutively

### Definition
$$A^{0} = \boldsymbol{0}, \quad A^{t+1} = A^t + \eta_{t} \Pi_{\Omega}(A - \text{shrink}_{\tau}(A^t))$$
### Convergence
$$\text{shrink}_{\tau}(A^t) \overset{t \rightarrow \infty}{\rightarrow} A^* = \arg\min_{B} \left\{ \lvert \lvert B \rvert  \rvert_{*} + \frac{1}{2\tau} \lvert \lvert B \rvert  \rvert_{F}^2 \right\}, \quad \text{s.t.} \Pi_{\Omega}(A-B) = \boldsymbol{0} $$
