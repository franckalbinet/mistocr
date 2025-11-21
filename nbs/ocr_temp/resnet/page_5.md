|  layer name | output size | 18-layer | 34-layer | 50-layer | 101-layer | 152-layer  |
| --- | --- | --- | --- | --- | --- | --- |
|  conv1 | 112×112 | 7×7, 64, stride 2 |  |  |  |   |
|   |  | 3×3 max pool, stride 2 |  |  |  |   |
|  conv2_x | 56×56 | 3×3, 64 | 2 | 3×3, 64 | 3 | 1×1, 64  |
|   |  | 3×3, 64 |  | 3×3, 64 |  | 3×3, 64  |
|   |  | 3×3, 64 |  | 1×1, 256 |  | 1×1, 256  |
|  conv3_x | 28×28 | 3×3, 128 | 2 | 3×3, 128 | 4 | 1×1, 128  |
|   |  | 3×3, 128 |  | 3×3, 128 |  | 3×3, 128  |
|   |  | 3×3, 128 |  | 1×1, 512 |  | 1×1, 512  |
|  conv4_x | 14×14 | 3×3, 256 | 2 | 3×3, 256 | 6 | 1×1, 256  |
|   |  | 3×3, 256 |  | 3×3, 256 |  | 3×3, 256  |
|   |  | 3×3, 256 |  | 1×1, 1024 |  | 1×1, 1024  |
|  conv5_x | 7×7 | 3×3, 512 | 2 | 3×3, 512 | 3 | 1×1, 512  |
|   |  | 3×3, 512 |  | 3×3, 512 |  | 3×3, 512  |
|   |  | 3×3, 512 |  | 1×1, 2048 |  | 1×1, 2048  |
|   | 1×1 | average pool, 1000-d fc, softmax |  |  |  |   |
|  FLOPs |  | 1.8×10^{9} | 3.6×10^{9} | 3.8×10^{9} | 7.6×10^{9} | 11.3×10^{9}  |

Table 1. Architectures for ImageNet. Building blocks are shown in brackets (see also Fig. 5), with the numbers of blocks stacked. Downsampling is performed by conv3_1, conv4_1, and conv5_1 with a stride of 2.

![img-3.jpeg](img-3.jpeg)

Figure 4. Training on **ImageNet**. Thin curves denote training error, and bold curves denote validation error of the center crops. Left: plain networks of 18 and 34 layers. Right: ResNets of 18 and 34 layers. In this plot, the residual networks have no extra parameter compared to their plain counterparts.

|   | plain | ResNet  |
| --- | --- | --- |
|  18 layers | 27.94 | 27.88  |
|  34 layers | 28.54 | 25.03  |

Table 2. Top-1 error (%, 10-crop testing) on ImageNet validation. Here the ResNets have no extra parameter compared to their plain counterparts. Fig. 4 shows the training procedures.

34-layer plain net has higher *training* error throughout the whole training procedure, even though the solution space of the 18-layer plain network is a subspace of that of the 34-layer one.

We argue that this optimization difficulty is *unlikely* to be caused by vanishing gradients. These plain networks are trained with BN [16], which ensures forward propagated signals to have non-zero variances. We also verify that the backward propagated gradients exhibit healthy norms with BN. So neither forward nor backward signals vanish. In fact, the 34-layer plain net is still able to achieve competitive accuracy (Table 3), suggesting that the solver works to some extent. We conjecture that the deep plain nets may have exponentially low convergence rates, which impact the reducing of the training error^{3}. The reason for such optimization difficulties will be studied in the future.

**Residual Networks.** Next we evaluate 18-layer and 34-layer residual nets (*ResNets*). The baseline architectures are the same as the above plain nets, except that a shortcut connection is added to each pair of 3×3 filters as in Fig. 3 (right). In the first comparison (Table 2 and Fig. 4 right), we use identity mapping for all shortcuts and zero-padding for increasing dimensions (option A). So they have *no extra parameter* compared to the plain counterparts.

We have three major observations from Table 2 and Fig. 4. First, the situation is reversed with residual learning – the 34-layer ResNet is better than the 18-layer ResNet (by 2.8%). More importantly, the 34-layer ResNet exhibits considerably lower training error and is generalizable to the validation data. This indicates that the degradation problem is well addressed in this setting and we manage to obtain accuracy gains from increased depth.

Second, compared to its plain counterpart, the 34-layer

^{3}We have experimented with more training iterations (3×) and still observed the degradation problem, suggesting that this problem cannot be feasibly addressed by simply using more iterations.