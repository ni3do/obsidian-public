---
{"dg-publish":true,"permalink":"/3-ressources/machine-learning/reparametrization-trick/","tags":["machine-learning, eth/cil/theory"],"created":"","updated":""}
---

# Reparametrization Trick
- cant do backprop over sampling process
### VAE example with Gaussian
- Encoder gives us parameters for a distribution, Gaussian in this case, mean $\mu$ and standard deviation $\sigma$
- Decoder then wants to sample from this distribution
- Cannot do backpropagation on sampling process
- $\Rightarrow$ inject Gaussian noise $\epsilon$ (sampled from standard gaussian), multiply by $\sigma$ and add $\mu$, which is equivalent to sampling from the distribution defined by these parameters
- This lets us do backpropagation over the parameters we are training, while ignoring the smapled noise
#### Standard VAE
![3-ressources/assets/vae-visualization.png| 800](/img/user/3-ressources/assets/vae-visualization.png)

#### VAE with reparametrization trick
![[3-ressources/machine-learning/Pasted image 20230804173000.png \| 500]] 
