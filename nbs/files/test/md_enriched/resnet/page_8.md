![img-5.jpeg](img-5.jpeg)
AI-generated image description:
___
Three line graphs showing training error (%) versus iterations (1e4) for different neural network architectures. Left panel compares plain networks (plain-20, plain-32, plain-44, plain-56) showing error rates between 0-20%, with deeper networks performing worse. Middle panel shows ResNet architectures (ResNet-20, ResNet-32, ResNet-44, ResNet-56, ResNet-110) with error rates 0-20%, demonstrating that deeper ResNets achieve lower error rates, with 56-layer and 20-layer performance labeled. Right panel compares residual-110 and residual-1202 models showing error rates 0-20%, with both converging to similar performance around 5-7% error. The graphs illustrate the effectiveness of residual connections in enabling training of deeper networks compared to plain architectures.
___

Figure 6. Training on **CIFAR-10**. Dashed lines denote training error, and bold lines denote testing error. **Left**: plain networks. The error of plain-110 is higher than 60% and not displayed. **Middle**: ResNets. **Right**: ResNets with 110 and 1202 layers.

![img-6.jpeg](img-6.jpeg)
AI-generated image description:
___
Two line graphs comparing standard deviation (std) across layer indices for different neural network architectures (plain-20, plain-56, ResNet-20, ResNet-56, and ResNet-110). The top graph shows layers in original order (x-axis: 0-110), while the bottom graph shows layers sorted by magnitude (x-axis: 0-110). In the top graph, all architectures show fluctuating standard deviations between 1-3, with notable spikes around layers 20-30 and 40-50. The bottom graph reveals that when sorted by magnitude, plain networks (especially plain-56) show higher initial standard deviations that decay more rapidly, while ResNet architectures (particularly ResNet-110) maintain more consistent, lower standard deviations across layers. This visualization likely demonstrates the stability properties of residual networks compared to plain networks.
___

Figure 7. Standard deviations (std) of layer responses on CIFAR-10. The responses are the outputs of each 3×3 layer, after BN and before nonlinearity. **Top**: the layers are shown in their original order. **Bottom**: the responses are ranked in descending order.

networks such as FitNet [35] and Highway [42] (Table 6), yet is among the state-of-the-art results (6.43%, Table 6).

**Analysis of Layer Responses.** Fig. 7 shows the standard deviations (std) of the layer responses. The responses are the outputs of each 3×3 layer, after BN and before other nonlinearity (ReLU/addition). For ResNets, this analysis reveals the response strength of the residual functions. Fig. 7 shows that ResNets have generally smaller responses than their plain counterparts. These results support our basic motivation (Sec.3.1) that the residual functions might be generally closer to zero than the non-residual functions. We also notice that the deeper ResNet has smaller magnitudes of responses, as evidenced by the comparisons among ResNet-20, 56, and 110 in Fig. 7. When there are more layers, an individual layer of ResNets tends to modify the signal less.

**Exploring Over 1000 layers.** We explore an aggressively deep model of over 1000 layers. We set *n* = 200 that leads to a 1202-layer network, which is trained as described above. Our method shows *no optimization difficulty*, and this 10<sup>3</sup>-layer network is able to achieve *training error* <0.1% (Fig. 6, right). Its test error is still fairly good (7.93%, Table 6).

But there are still open problems on such aggressively deep models. The testing result of this 1202-layer network is worse than that of our 110-layer network, although both have similar training error. We argue that this is because of overfitting. The 1202-layer network may be unnecessarily large (19.4M) for this small dataset. Strong regularization such as maxout [10] or dropout [14] is applied to obtain the best results ([10, 25, 24, 35]) on this dataset. In this paper, we use no maxout/dropout and just simply impose regularization via deep and thin architectures by design, without distracting from the focus on the difficulties of optimization. But combining with stronger regularization may improve results, which we will study in the future.

### 4.3. Object Detection on PASCAL and MS COCO ... page 8

Our method has good generalization performance on other recognition tasks. Table 7 and 8 show the object detection baseline results on PASCAL VOC 2007 and 2012 [5] and COCO [26]. We adopt *Faster R-CNN* [32] as the detection method. Here we are interested in the improvements of replacing VGG-16 [41] with ResNet-101. The detection implementation (see appendix) of using both models is the same, so the gains can only be attributed to better networks. Most remarkably, on the challenging COCO dataset we obtain a 6.0% increase in COCO's standard metric (mAP@[,5, .95]), which is a 28% relative improvement. This gain is solely due to the learned representations.

Based on deep residual nets, we won the 1st places in several tracks in ILSVRC & COCO 2015 competitions: ImageNet detection, ImageNet localization, COCO detection, and COCO segmentation. The details are in the appendix.