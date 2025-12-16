![img-8.jpeg](img-8.jpeg)
AI-generated image description:
___
Line graph showing error percentage versus iteration (×1e4) for different plain layer configurations (20, 32, 44, and 56 layers). The y-axis shows error percentage from 0 to 20%, and the x-axis shows iterations from 0 to 6 (×1e4). Multiple colored lines represent different layer depths, with darker/warmer colors (red/brown) representing 56-layer networks and lighter/cooler colors (cyan/light blue) representing 20-layer networks. The graph demonstrates training convergence behavior, with a notable sharp drop in error around iteration 2-3 for all configurations. The 56-layer and 20-layer configurations are specifically labeled on the right side of the graph. The deeper networks (56-layer) show higher final error rates around 12-15%, while shallower networks (20-layer) achieve lower error rates around 8-10%, suggesting a degradation problem with increased network depth.
___
Figure 6. Training on CIFAR-10. Dashed lines denote training error, and bold lines denote testing error. Left: plain networks. The error of plain-110 is higher than  $60\%$  and not displayed. Middle: ResNets. Right: ResNets with 110 and 1202 layers.

![img-9.jpeg](img-9.jpeg)
AI-generated image description:
___
Line graph showing error percentage versus iteration (1e4) for different ResNet architectures. The graph compares ResNet-20, ResNet-32, ResNet-44, ResNet-56, and ResNet-110 models, represented by different colored lines (green, cyan, red, yellow, and black respectively). The y-axis shows error percentage ranging from 0 to 20%, while the x-axis shows iterations from 0 to 6 (×1e4). All models start with high error rates around 15-20% and decrease over iterations. The deeper networks (ResNet-56 and ResNet-110) converge to lower error rates around 5-6%, while shallower networks (ResNet-20 and ResNet-32) stabilize at slightly higher error rates around 8-9%. The graph demonstrates that deeper ResNet architectures achieve better performance, with the 110-layer model achieving the lowest final error rate. The convergence behavior shows initial rapid decrease followed by gradual stabilization after approximately 3×10^4 iterations.
___

![img-10.jpeg](img-10.jpeg)
AI-generated image description:
___
Line graph showing error percentage versus iteration number (1e4). The plot displays two residual curves labeled 'residual-110' (purple/magenta line) and 'residual-1202' (black line). The y-axis shows error percentage ranging from 0 to 20%, while the x-axis shows iterations from 0 to 6 (×1e4). Both curves show a general downward trend, starting around 8-9% error and converging to approximately 6-7% error by iteration 6. The residual-110 curve (purple) shows slightly more variation and maintains a marginally higher error rate compared to residual-1202 (black) throughout the training process. This appears to be a training convergence plot comparing two different residual network architectures.
___

![img-11.jpeg](img-11.jpeg)
AI-generated image description:
___
Two-panel line graph comparing neural network architectures (plain-20, plain-56, VGG-20, ResNet-56, and ResNet-110). Top panel shows layer index in original order on x-axis (0-110) versus standard deviation on y-axis (0-3). Bottom panel shows the same layers sorted by magnitude on x-axis (0-110) versus standard deviation on y-axis (0-3). The top panel reveals high variability in standard deviation across layers for plain and VGG networks (yellow, orange, and red lines showing peaks up to 3), while ResNet architectures (dark red and black lines) maintain consistently low standard deviation around 1. The bottom panel, with layers sorted by magnitude, shows a clearer separation between architectures, with plain/VGG networks exhibiting higher initial values that gradually decrease, while ResNet networks maintain lower, more stable values throughout. This visualization demonstrates the stability characteristics of different deep learning architectures across their layers.
___
Figure 7. Standard deviations (std) of layer responses on CIFAR-10. The responses are the outputs of each  $3 \times 3$  layer, after BN and before nonlinearity. Top: the layers are shown in their original order. Bottom: the responses are ranked in descending order.

networks such as FitNet [35] and Highway [42] (Table 6), yet is among the state-of-the-art results  $(6.43\%)$  Table 6).

Analysis of Layer Responses. Fig. 7 shows the standard deviations (std) of the layer responses. The responses are the outputs of each  $3 \times 3$  layer, after BN and before other nonlinearity (ReLU/addition). For ResNets, this analysis reveals the response strength of the residual functions. Fig. 7 shows that ResNets have generally smaller responses than their plain counterparts. These results support our basic motivation (Sec.3.1) that the residual functions might be generally closer to zero than the non-residual functions. We also notice that the deeper ResNet has smaller magnitudes of responses, as evidenced by the comparisons among ResNet-20, 56, and 110 in Fig. 7. When there are more layers, an individual layer of ResNets tends to modify the signal less.

Exploring Over 1000 layers. We explore an aggressively deep model of over 1000 layers. We set  $n = 200$  that leads to a 1202-layer network, which is trained as described above. Our method shows no optimization difficulty, and this  $10^{3}$ -layer network is able to achieve training error  $&lt; 0.1\%$  (Fig. 6, right). Its test error is still fairly good  $(7.93\%, \text{Table 6})$ .

But there are still open problems on such aggressively deep models. The testing result of this 1202-layer network is worse than that of our 110-layer network, although both

|  training data | 07+12 | 07++12  |
| --- | --- | --- |
|  test data | VOC 07 test | VOC 12 test  |
|  VGG-16 | 73.2 | 70.4  |
|  ResNet-101 | 76.4 | 73.8  |

Table 7. Object detection mAP (\%) on the PASCAL VOC 2007/2012 test sets using baseline Faster R-CNN. See also Table 10 and 11 for better results.

|  metric | mAP@.5 | mAP@[.5, .95]  |
| --- | --- | --- |
|  VGG-16 | 41.5 | 21.2  |
|  ResNet-101 | 48.4 | 27.2  |

Table 8. Object detection mAP (\%) on the COCO validation set using baseline Faster R-CNN. See also Table 9 for better results.

have similar training error. We argue that this is because of overfitting. The 1202-layer network may be unnecessarily large (19.4M) for this small dataset. Strong regularization such as maxout [10] or dropout [14] is applied to obtain the best results ([10, 25, 24, 35]) on this dataset. In this paper, we use no maxout/dropout and just simply impose regularization via deep and thin architectures by design, without distracting from the focus on the difficulties of optimization. But combining with stronger regularization may improve results, which we will study in the future.

### 4.3. Object Detection on PASCAL and MS COCO ... page 8

Our method has good generalization performance on other recognition tasks. Table 7 and 8 show the object detection baseline results on PASCAL VOC 2007 and 2012 [5] and COCO [26]. We adopt Faster R-CNN [32] as the detection method. Here we are interested in the improvements of replacing VGG-16 [41] with ResNet-101. The detection implementation (see appendix) of using both models is the same, so the gains can only be attributed to better networks. Most remarkably, on the challenging COCO dataset we obtain a  $6.0\%$  increase in COCO's standard metric (mAP@[.5, .95]), which is a  $28\%$  relative improvement. This gain is solely due to the learned representations.

Based on deep residual nets, we won the 1st places in several tracks in ILSVRC &amp; COCO 2015 competitions: ImageNet detection, ImageNet localization, COCO detection, and COCO segmentation. The details are in the appendix.