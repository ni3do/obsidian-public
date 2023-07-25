---
{"dg-publish":true,"permalink":"/eth/23-fs/cil/project/cil-results/","tags":["eth/cil/project"],"created":"","updated":""}
---

# CIL Project Results
## Model Comparison
![eth/23FS/cil/project/assets/model-comparison-10.png](/img/user/eth/23FS/cil/project/assets/model-comparison-10.png)
Visualization of different models that we first evaluated for 10 epochs on the wachterberg-street25 dataset. Most performed similarly.

## Encoder Comparison

![encoder-comparison-unetpp-30.png](/img/user/eth/23FS/cil/project/assets/encoder-comparison-unetpp-30.png)
Next we compared different encoders. We chose the UnetPlusPlus model as our base model, because it is one of the most established ones and performed the best in our model comparison. Both efficientNet encoders achieve best performance.

## Model Encoder Comparison

![model-encoder-comparison-30.png](/img/user/eth/23FS/cil/project/assets/model-encoder-comparison-30.png)
We further did tests on some chosen combinations of models and encoders, but did not achieve better results than UnetPlusPlus with efficientNet-b5.
# Dataset
The next step was to enlarge the Dataset. We did this in multiple steps, which gave us three differente sized datasets, where each bigger one incorporates the smaller ones. The number specifies the amount of images in thousands:
* wachterberg-street25
* wachterberg-street65
* wachterberg-street90
## Final Models
### !!Not finished!!

![eth/23FS/cil/project/assets/final-models.png](/img/user/eth/23FS/cil/project/assets/final-models.png)

Current data on final models. These are trained on the wachterberg-street65 and wachterberg-street90 datasets. 
## Submission
To create our submission we use test time augmentation.
### !!TODO!!!
this is still a todo