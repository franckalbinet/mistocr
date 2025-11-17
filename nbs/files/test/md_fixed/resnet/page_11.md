| training data | COCO train | COCO trainval |
| :-- | :--: | :--: |
| test data | COCO val | COCO test-dev |
| mAP | @. 5 | @[.5, .95] | @. 5 | @[.5, .95] |
| baseline Faster R-CNN (VGG-16) | 41.5 | 21.2 |  |
| baseline Faster R-CNN (ResNet-101) | 48.4 | 27.2 |  |
| +box refinement | 49.9 | 29.9 |  |
| +context | 51.1 | 30.0 | 53.3 | 32.2 |
| +multi-scale testing | 53.8 | 32.5 | $\mathbf{5 5 . 7}$ | $\mathbf{3 4 . 9}$ |
| ensemble |  |  | $\mathbf{5 9 . 0}$ | $\mathbf{3 7 . 4}$ |

Table 9. Object detection improvements on MS COCO using Faster R-CNN and ResNet-101.

| system | net | data | mAP | area | bike | bird | boat | bottle | bus | car | cat | chair | cow | table | dog | horse | mbike | person | plant | sheep | sofa | train | tv |
| :-- | :--: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: |
| baseline | VGG-16 | $07+12$ | 73.2 | 76.5 | 79.0 | 70.9 | 65.5 | 52.1 | 83.1 | 84.7 | 86.4 | 52.0 | 81.9 | 65.7 | 84.8 | 84.6 | 77.5 | 76.7 | 38.8 | 73.6 | 73.9 | 83.0 | 72.6 |
| baseline | ResNet-101 | $07+12$ | 76.4 | 79.8 | 80.7 | 76.2 | 68.3 | 55.9 | 85.1 | 85.3 | $\mathbf{8 9 . 8}$ | 56.7 | 87.8 | 69.4 | 88.3 | 88.9 | 80.9 | 78.4 | 41.7 | 78.6 | 79.8 | 85.3 | 72.0 |
| baseline+++ | ResNet-101 | COCO+07+12 | $\mathbf{8 5 . 6}$ | $\mathbf{9 0 . 0}$ | $\mathbf{8 9 . 6}$ | $\mathbf{8 7 . 8}$ | $\mathbf{8 0 . 8}$ | $\mathbf{7 6 . 1}$ | $\mathbf{8 9 . 9}$ | $\mathbf{8 9 . 9}$ | 89.6 | $\mathbf{7 5 . 5}$ | $\mathbf{9 0 . 0}$ | $\mathbf{8 0 . 7}$ | $\mathbf{8 9 . 6}$ | $\mathbf{9 0 . 3}$ | $\mathbf{8 9 . 1}$ | $\mathbf{8 8 . 7}$ | $\mathbf{6 5 . 4}$ | $\mathbf{8 8 . 1}$ | $\mathbf{8 5 . 6}$ | $\mathbf{8 9 . 0}$ | $\mathbf{8 6 . 8}$ |

Table 10. Detection results on the PASCAL VOC 2007 test set. The baseline is the Faster R-CNN system. The system "baseline+++" include box refinement, context, and multi-scale testing in Table 9.

| system | net | data | mAP | area | bike | bird | boat | bottle | bus | car | cat | chair | cow | table | dog | horse | mbike | person | plant | sheep | sofa | train | tv |
| :-- | :--: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: | --: |
| baseline | VGG-16 | $07++12$ | 70.4 | 84.9 | 79.8 | 74.3 | 53.9 | 49.8 | 77.5 | 75.9 | 88.5 | 45.6 | 77.1 | 55.3 | 86.9 | 81.7 | 80.9 | 79.6 | 40.1 | 72.6 | 60.9 | 81.2 | 61.5 |
| baseline | ResNet-101 | $07++12$ | 73.8 | 86.5 | 81.6 | 77.2 | 58.0 | 51.0 | 78.6 | 76.6 | 93.2 | 48.6 | 80.4 | 59.0 | 92.1 | 85.3 | 84.8 | 80.7 | 48.1 | 77.3 | 66.5 | 84.7 | 65.6 |
| baseline+++ | ResNet-101 | COCO+07++12 | $\mathbf{8 3 . 8}$ | $\mathbf{9 2 . 1}$ | $\mathbf{8 8 . 4}$ | $\mathbf{8 4 . 8}$ | $\mathbf{7 5 . 9}$ | $\mathbf{7 1 . 4}$ | $\mathbf{8 6 . 3}$ | $\mathbf{8 7 . 8}$ | $\mathbf{9 4 . 2}$ | $\mathbf{6 6 . 8}$ | $\mathbf{8 9 . 4}$ | $\mathbf{6 9 . 2}$ | $\mathbf{9 3 . 9}$ | $\mathbf{9 1 . 9}$ | $\mathbf{9 0 . 9}$ | $\mathbf{8 9 . 6}$ | $\mathbf{6 7 . 9}$ | $\mathbf{8 8 . 2}$ | $\mathbf{7 6 . 8}$ | $\mathbf{9 0 . 3}$ | $\mathbf{8 0 . 0}$ |

Table 11. Detection results on the PASCAL VOC 2012 test set (http://host.robots.ox.ac.uk:8080/leaderboard/ displaylb.php?challengeid=11\&compid=4). The baseline is the Faster R-CNN system. The system "baseline+++" include box refinement, context, and multi-scale testing in Table 9.

We select two adjacent scales from the pyramid following [33]. RoI pooling and subsequent layers are performed on the feature maps of these two scales [33], which are merged by maxout as in [33]. Multi-scale testing improves the mAP by over 2 points (Table 9).

Using validation data. Next we use the $80 \mathrm{k}+40 \mathrm{k}$ trainval set for training and the 20 k test-dev set for evaluation. The testdev set has no publicly available ground truth and the result is reported by the evaluation server. Under this setting, the results are an $\mathrm{mAP} @ .5$ of $55.7 \%$ and an $\mathrm{mAP} @[.5, .95]$ of $34.9 \%$ (Table 9). This is our single-model result.

Ensemble. In Faster R-CNN, the system is designed to learn region proposals and also object classifiers, so an ensemble can be used to boost both tasks. We use an ensemble for proposing regions, and the union set of proposals are processed by an ensemble of per-region classifiers. Table 9 shows our result based on an ensemble of 3 networks. The mAP is $59.0 \%$ and $37.4 \%$ on the test-dev set. This result won the 1st place in the detection task in COCO 2015.

## PASCAL VOC ... page 11

We revisit the PASCAL VOC dataset based on the above model. With the single model on the COCO dataset ( $55.7 \%$ $\mathrm{mAP} @ .5$ in Table 9), we fine-tune this model on the PASCAL VOC sets. The improvements of box refinement, context, and multi-scale testing are also adopted. By doing so

|  | val2 | test |
| :-- | :--: | :--: |
| GoogLeNet [44] (ILSVRC'14) | - | 43.9 |
| our single model (ILSVRC'15) | 60.5 | 58.8 |
| our ensemble (ILSVRC'15) | $\mathbf{6 3 . 6}$ | $\mathbf{6 2 . 1}$ |

Table 12. Our results (mAP, \%) on the ImageNet detection dataset. Our detection system is Faster R-CNN [32] with the improvements in Table 9, using ResNet-101.
we achieve $85.6 \%$ mAP on PASCAL VOC 2007 (Table 10) and $83.8 \%$ on PASCAL VOC 2012 (Table 11) ${ }^{6}$. The result on PASCAL VOC 2012 is 10 points higher than the previous state-of-the-art result [6].

## ImageNet Detection ... page 11

The ImageNet Detection (DET) task involves 200 object categories. The accuracy is evaluated by mAP@.5. Our object detection algorithm for ImageNet DET is the same as that for MS COCO in Table 9. The networks are pretrained on the 1000-class ImageNet classification set, and are fine-tuned on the DET data. We split the validation set into two parts (val1/val2) following [8]. We fine-tune the detection models using the DET training set and the val1 set. The val2 set is used for validation. We do not use other ILSVRC 2015 data. Our single model with ResNet-101 has

[^0]
[^0]:    ${ }^{6}$ http://host.robots.ox.ac.uk:8080/anonymous/302402.html, submitted on 2015-11-26.