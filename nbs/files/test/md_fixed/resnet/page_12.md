| LOC <br> method | LOC <br> network | testing | LOC error <br> on GT CLS | classification <br> network | top-5 LOC error <br> on predicted CLS |
| :--: | :--: | :--: | :--: | :--: | :--: |
| VGG’s [41] | VGG-16 | 1-crop | 33.1 [41] |  |  |
| RPN | ResNet-101 | 1-crop | 13.3 |  |  |
| RPN | ResNet-101 | dense | 11.7 |  |  |
| RPN | ResNet-101 | dense |  | ResNet-101 | 14.4 |
| RPN+RCNN | ResNet-101 | dense |  | ResNet-101 | 10.6 |
| RPN+RCNN | ensemble | dense |  | ensemble | 8.9 |

Table 13. Localization error (\%) on the ImageNet validation. In the column of "LOC error on GT class" ([41]), the ground truth class is used. In the "testing" column, "1-crop" denotes testing on a center crop of $224 \times 224$ pixels, "dense" denotes dense (fully convolutional) and multi-scale testing.
$58.8 \% \mathrm{mAP}$ and our ensemble of 3 models has $62.1 \% \mathrm{mAP}$ on the DET test set (Table 12). This result won the 1st place in the ImageNet detection task in ILSVRC 2015, surpassing the second place by $\mathbf{8 . 5}$ points (absolute).

## Appendix C. ImageNet Localization .... page 12

The ImageNet Localization (LOC) task [36] requires to classify and localize the objects. Following [40, 41], we assume that the image-level classifiers are first adopted for predicting the class labels of an image, and the localization algorithm only accounts for predicting bounding boxes based on the predicted classes. We adopt the "per-class regression" (PCR) strategy [40, 41], learning a bounding box regressor for each class. We pre-train the networks for ImageNet classification and then fine-tune them for localization. We train networks on the provided 1000-class ImageNet training set.

Our localization algorithm is based on the RPN framework of [32] with a few modifications. Unlike the way in [32] that is category-agnostic, our RPN for localization is designed in a per-class form. This RPN ends with two sibling $1 \times 1$ convolutional layers for binary classification (cls) and box regression (reg), as in [32]. The cls and reg layers are both in a per-class from, in contrast to [32]. Specifically, the cls layer has a 1000-d output, and each dimension is binary logistic regression for predicting being or not being an object class; the reg layer has a $1000 \times 4-\mathrm{d}$ output consisting of box regressors for 1000 classes. As in [32], our bounding box regression is with reference to multiple translation-invariant "anchor" boxes at each position.

As in our ImageNet classification training (Sec. 3.4), we randomly sample $224 \times 224$ crops for data augmentation. We use a mini-batch size of 256 images for fine-tuning. To avoid negative samples being dominate, 8 anchors are randomly sampled for each image, where the sampled positive and negative anchors have a ratio of 1:1 [32]. For testing, the network is applied on the image fully-convolutionally.

Table 13 compares the localization results. Following [41], we first perform "oracle" testing using the ground truth class as the classification prediction. VGG's paper [41] re-

| method | top-5 localization err |  |
| :--: | :--: | :--: |
|  | val | test |
| OverFeat [40] (ILSVRC'13) | 30.0 | 29.9 |
| GoogLeNet [44] (ILSVRC'14) | - | 26.7 |
| VGG [41] (ILSVRC'14) | 26.9 | 25.3 |
| ours (ILSVRC'15) | 8.9 | 9.0 |

Table 14. Comparisons of localization error (\%) on the ImageNet dataset with state-of-the-art methods.
ports a center-crop error of $33.1 \%$ (Table 13) using ground truth classes. Under the same setting, our RPN method using ResNet-101 net significantly reduces the center-crop error to $13.3 \%$. This comparison demonstrates the excellent performance of our framework. With dense (fully convolutional) and multi-scale testing, our ResNet-101 has an error of $11.7 \%$ using ground truth classes. Using ResNet-101 for predicting classes ( $4.6 \%$ top-5 classification error, Table 4), the top-5 localization error is $14.4 \%$.

The above results are only based on the proposal network (RPN) in Faster R-CNN [32]. One may use the detection network (Fast R-CNN [7]) in Faster R-CNN to improve the results. But we notice that on this dataset, one image usually contains a single dominate object, and the proposal regions highly overlap with each other and thus have very similar RoI-pooled features. As a result, the image-centric training of Fast R-CNN [7] generates samples of small variations, which may not be desired for stochastic training. Motivated by this, in our current experiment we use the original RCNN [8] that is RoI-centric, in place of Fast R-CNN.

Our R-CNN implementation is as follows. We apply the per-class RPN trained as above on the training images to predict bounding boxes for the ground truth class. These predicted boxes play a role of class-dependent proposals. For each training image, the highest scored 200 proposals are extracted as training samples to train an R-CNN classifier. The image region is cropped from a proposal, warped to $224 \times 224$ pixels, and fed into the classification network as in R-CNN [8]. The outputs of this network consist of two sibling fc layers for $c l s$ and reg, also in a per-class form. This R-CNN network is fine-tuned on the training set using a mini-batch size of 256 in the RoI-centric fashion. For testing, the RPN generates the highest scored 200 proposals for each predicted class, and the R-CNN network is used to update these proposals' scores and box positions.

This method reduces the top-5 localization error to $10.6 \%$ (Table 13). This is our single-model result on the validation set. Using an ensemble of networks for both classification and localization, we achieve a top-5 localization error of $9.0 \%$ on the test set. This number significantly outperforms the ILSVRC 14 results (Table 14), showing a $64 \%$ relative reduction of error. This result won the 1st place in the ImageNet localization task in ILSVRC 2015.