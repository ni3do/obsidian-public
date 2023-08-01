---
{"dg-publish":true,"permalink":"/3-ressources/math/linear-algebra/cil-shrink-operator/","tags":["math/linear-algebra, eth/cil/theory"],"created":"","updated":""}
---

# Shrink Operator
- [[3-ressources/math/linear-algebra/norms/nuclear-norm\|Nuclear norm minimization]] abstracted into an operator
- shrinks each singular value by $\tau$, clips to $0$
### Definition
$$\text{shrink}_{\tau}(A) := \arg\min_{B} \frac{1}{2}\lvert \lvert A-B \rvert  \rvert_{F}^2 + \tau \lvert \lvert B \rvert  \rvert_{*} = U \text{diag}(\sigma_{i}-\tau)_{+}V^T $$

