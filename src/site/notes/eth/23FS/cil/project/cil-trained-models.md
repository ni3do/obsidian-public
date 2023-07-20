---
{"dg-publish":true,"permalink":"/eth/23-fs/cil/project/cil-trained-models/","tags":["cil-project"],"created":"","updated":""}
---

![[model_plot.png \| 500]] 
| File                                                                                                                      | model-name    | encoder-name     | epochs | dice-loss | trained-by |
| ------------------------------------------------------------------------------------------------------------------------- | ------------- | ---------------- | ------ | --------- | ---------- |
| [[eth/23FS/cil/project/trained-models/DeepLabV3Plus-efficientnet-b7-imagenet\|DeepLabV3Plus-efficientnet-b7-imagenet]] | DeepLabV3Plus | efficientnet-b7  | 30     | 0.174434  | stkramer   |
| [[eth/23FS/cil/project/trained-models/DeepLabV3Plus-efficinetnet-b5-imagenet\|DeepLabV3Plus-efficinetnet-b5-imagenet]] | DeepLabV3Plus | efficinet-net-b5 | 30     | 0.1706    | stkramer   |
| [[eth/23FS/cil/project/trained-models/DeepLabV3Plus-resnet34-imagenet\|DeepLabV3Plus-resnet34-imagenet]]               | DeepLabV3Plus | resnet34         | 40     | 0.184872  | stkramer   |
| [[eth/23FS/cil/project/trained-models/FPN-resnet34-imagenet\|FPN-resnet34-imagenet]]                                   | FPN           | resnet34         | 40     | 0.191541  | stkramer   |
| [[eth/23FS/cil/project/trained-models/FPN-resnet50-imagenet\|FPN-resnet50-imagenet]]                                   | FPN           | resnet50         | 40     | 0.186897  | siwachte   |
| [[eth/23FS/cil/project/trained-models/Linknet-efficientnet-b5-imagenet\|Linknet-efficientnet-b5-imagenet]]             | Linknet       | efficientnet-b5  | 30     | 0.178627  | siwachte   |
| [[eth/23FS/cil/project/trained-models/Linknet-resnet34-imagenet\|Linknet-resnet34-imagenet]]                           | Linknet       | resnet34         | 40     | 0.188096  | siwachte   |
| [[eth/23FS/cil/project/trained-models/Linknet-resnet50-imagenet\|Linknet-resnet50-imagenet]]                           | Linknet       | resnet50         | 40     | 0.189461  | siwachte   |
| [[eth/23FS/cil/project/trained-models/UnetPlusPlus-efficientnet-b5-imagenet\|UnetPlusPlus-efficientnet-b5-imagenet]]   | UnetPlusPlus  | efficientnet-b5  | 40     | 0.164649  | stkramer   |
| [[eth/23FS/cil/project/trained-models/UnetPlusPlus-efficientnet-b7-imagenet\|UnetPlusPlus-efficientnet-b7-imagenet]]   | UnetPlusPlus  | efficientnet-b7  | 30     | 0.169151  | siwachte   |
| [[eth/23FS/cil/project/trained-models/UnetPlusPlus-resnet101-imagenet\|UnetPlusPlus-resnet101-imagenet]]               | UnetPlusPlus  | resnet101        | 40     | 0.183924  | stkramer   |
| [[eth/23FS/cil/project/trained-models/UnetPlusPlus-resnet34-imagenet\|UnetPlusPlus-resnet34-imagenet]]                 | UnetPlusPlus  | resnet34         | 40     | 0.1911    | siwachte   |
| [[eth/23FS/cil/project/trained-models/UnetPlusPlus-resnet50-imagenet\|UnetPlusPlus-resnet50-imagenet]]                 | UnetPlusPlus  | resnet50         | 40     | 0.183857  | siwachte   |

{ .block-language-dataview}

| model name    | encoder name    | encoder weights | account  | epochs | DiceLoss |
| ------------- | --------------- | --------------- | -------- | ------ | -------- |
| UnetPlusPlus  | resnet34        | imagenet        | siwachte | 40     | 0.1911   |
| UnetPlusPlus  | resnet50        | imagenet        | siwachte | 40     | running  |
| UnetPlusPLus  | resnet101       | imagenet        | stkramer | 40     | running  |
| UnetPlusPLus  | efficientnet-b5 | imagenet        | stkramer | 40     | inqueue  |
| Linknet       | resnet34        | imagenet        | siwachte | 40     | 0.1880   |
| Linknet       | resnet50        | imagenet        | siwachte | 40     | inqueue  |
| FPN           | resnet34        | imagenet        | stkramer | 40     | 0.1915   |
| FPN           | resnet50        | imagenet        | siwachte | 40     | inqueue  |
| DeepLabV3Plus | resnet34        | imagenet        | stkramer | 40     | 0.1848   |
| DeepLabV3Plus | resnet101       | imagenet        | stkramer | 40     | inqueue  |
