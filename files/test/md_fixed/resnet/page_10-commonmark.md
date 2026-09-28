

A Object Detection Baselines

In this section we introduce our detection method based on the baseline
Faster R-CNN *\[32\]* system. The models are initialized by the ImageNet
classification models, and then fine-tuned on the object detection data.
We have experimented with ResNet-50/101 at the time of the ILSVRC & COCO
2015 detection competitions.

Unlike VGG-16 used in *\[32\]*, our ResNet has no hidden fc layers. We
adopt the idea of “Networks on Conv feature maps” (NoC) *\[33\]* to
address this issue. We compute the full-image shared conv feature maps
using those layers whose strides on the image are no greater than 16
pixels (i.e., conv1, conv2_x, conv3_x, and conv4_x, totally 91 conv
layers in ResNet-101; Table 1). We consider these layers as analogous to
the 13 conv layers in VGG-16, and by doing so, both ResNet and VGG-16
have conv feature maps of the same total stride (16 pixels). These
layers are shared by a region proposal network (RPN, generating 300
proposals) *\[32\]* and a Fast R-CNN detection network *\[7\]*. RoI
pooling *\[7\]* is performed before conv5_1. On this RoI-pooled feature,
all layers of conv5_x and up are adopted for each region, playing the
roles of VGG-16’s fc layers. The final classification layer is replaced
by two sibling layers (classification and box regression *\[7\]*).

For the usage of BN layers, after pre-training, we compute the BN
statistics (means and variances) for each layer on the ImageNet training
set. Then the BN layers are fixed during fine-tuning for object
detection. As such, the BN layers become linear activations with
constant offsets and scales, and BN statistics are not updated by
fine-tuning. We fix the BN layers mainly for reducing memory consumption
in Faster R-CNN training.

PASCAL VOC

Following *\[7, 32\]*, for the PASCAL VOC 2007 test set, we use the 5k
trainval images in VOC 2007 and 16k trainval images in VOC 2012 for
training (“07+12”). For the PASCAL VOC 2012 test set, we use the 10k
trainval+test images in VOC 2007 and 16k trainval images in VOC 2012 for
training (“07++12”). The hyper-parameters for training Faster R-CNN are
the same as in *\[32\]*. Table 7 shows the results. ResNet-101 improves
the mAP by $\>$3% over VGG-16. This gain is solely because of the
improved features learned by ResNet.

MS COCO

The MS COCO dataset *\[26\]* involves 80 object categories. We evaluate
the PASCAL VOC metric (mAP @ IoU = 0.5) and the standard COCO metric
(mAP @ IoU = .5:.05:.95). We use the 80k images on the train set for
training and the 40k images on the val set for evaluation. Our detection
system for COCO is similar to that for PASCAL VOC. We train the COCO
models with an 8-GPU implementation, and thus the RPN step has a
mini-batch size of 8 images (i.e., 1 per GPU) and the Fast R-CNN step
has a mini-batch size of 16 images. The RPN step and Fast R-CNN step are
both trained for 240k iterations with a learning rate of 0.001 and then
for 80k iterations with 0.0001.

Table 8 shows the results on the MS COCO validation set. ResNet-101 has
a 6% increase of mAP@\[.5, .95\] over VGG-16, which is a 28% relative
improvement, solely contributed by the features learned by the better
network. Remarkably, the mAP@\[.5, .95\]’s absolute increase (6.0%) is
nearly as big as mAP@.5’s (6.9%). This suggests that a deeper network
can improve both recognition and localization.

## Appendix B Object Detection Improvements … page 10

For completeness, we report the improvements made for the competitions.
These improvements are based on deep features and thus should benefit
from residual learning.

MS COCO

Box refinement. Our box refinement partially follows the iterative
localization in *\[6\]*. In Faster R-CNN, the final output is a
regressed box that is different from its proposal box. So for inference,
we pool a new feature from the regressed box and obtain a new
classification score and a new regressed box. We combine these 300 new
predictions with the original 300 predictions. Non-maximum suppression
(NMS) is applied on the union set of predicted boxes using an IoU
threshold of 0.3 *\[8\]*, followed by box voting *\[6\]*. Box refinement
improves mAP by about 2 points (Table 9).

Global context. We combine global context in the Fast R-CNN step. Given
the full-image conv feature map, we pool a feature by global Spatial
Pyramid Pooling *\[12\]* (with a “single-level” pyramid) which can be
implemented as “RoI” pooling using the entire image’s bounding box as
the RoI. This pooled feature is fed into the post-RoI layers to obtain a
global context feature. This global feature is concatenated with the
original per-region feature, followed by the sibling classification and
box regression layers. This new structure is trained end-to-end. Global
context improves mAP@.5 by about 1 point (Table 9).

Multi-scale testing. In the above, all results are obtained by
single-scale training/testing as in *\[32\]*, where the image’s shorter
side is *s* = 600 pixels. Multi-scale training/testing has been
developed in *\[12, 7\]* by selecting a scale from a feature pyramid,
and in *\[33\]* by using maxout layers. In our current implementation,
we have performed multi-scale testing following *\[33\]*; we have not
performed multi-scale training because of limited time. In addition, we
have performed multi-scale testing only for the Fast R-CNN step (but not
yet for the RPN step). With a trained model, we compute conv feature
maps on an image pyramid, where the image’s shorter sides are
*s* ∈ {200, 400, 600, 800, 1000}.
