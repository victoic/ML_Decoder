# ML-Decoder: Scalable and Versatile Classification Head

<!---
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/imagenet-21k-pretraining-for-the-masses/multi-label-classification-on-ms-coco)](https://paperswithcode.com/sota/multi-label-classification-on-ms-coco?p=imagenet-21k-pretraining-for-the-masses)<br>
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/asymmetric-loss-for-multi-label/multi-label-classification-on-nus-wide)](https://paperswithcode.com/sota/multi-label-classification-on-nus-wide?p=asymmetric-loss-for-multi-label)<br>
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/imagenet-21k-pretraining-for-the-masses/multi-label-classification-on-pascal-voc-2007)](https://paperswithcode.com/sota/multi-label-classification-on-pascal-voc-2007?p=imagenet-21k-pretraining-for-the-masses)<br>
-->
<br> [Paper](https://arxiv.org/abs/2009.14119) |

Official PyTorch Implementation

>  Tal Ridnik, Gilad Sharir, Avi Ben-Cohen, Emanuel Ben-Baruch, Asaf Noy
> <br/> DAMO Academy, Alibaba
> Group

**Abstract**

In this paper, we introduce ML-Decoder, a new attention-based classification head.  ML-Decoder predicts the existence of class labels via queries, and enables better utilization of spatial data compared to global average pooling.
By redesigning the decoder architecture, and using a novel group-decoding scheme, ML-Decoder is highly efficient, and can scale well to thousands of classes. Compared to using a larger backbone, ML-Decoder consistently provides a better speed-accuracy trade-off.
ML-Decoder is also versatile - it can be used as a drop-in replacement for various classification heads, and generalize to unseen classes when operated with word queries. Novel query augmentations further improve its generalization ability.
Using ML-Decoder, we achieve state-of-the-art results on several classification tasks:
on MS-COCO multi-label, we reach 91.1% mAP; on NUS-WIDE zero-shot, we reach 31.1% ZSL mAP; and on ImageNet single-label, we reach with vanilla ResNet50 backbone a new top score of 80.7%, without extra data or distillation. Public code will be available.

<p align="center">
 <table class="tg">
  <tr>
    <td class="tg-c3ow"><img src="./pics/main_pic.png" align="center" width="400""></td>
    <td class="tg-c3ow"><img src="./pics/ms_coco_scores.png" align="center" width="400" ></td>

  </tr>
</table>
</p>

## ML-Decoder Implementation
ML-Decoder implementation is available [here](./src/ml_decoder/ml_decoder.py).
It can be easily integrated into any backbone using this example code:
```
ml_decoder_head = MLDecoder(num_classes) # initilization
spatial_embeddings = self.backbone(x)        
logits = ml_decoder_head(spatial_embeddings)
return logits
```
## Training Code 

We will share a full reproduction code for the article results.
<br>A reproduction code for MS-COCO multi-label:
```
python train.py  \
--data=/home/datasets/coco2014/
--model_name=tresnet_l
--image_size=448
```

Reproduction code for ZSL and single-label are WIP.
## Citation
```
 TBD
```