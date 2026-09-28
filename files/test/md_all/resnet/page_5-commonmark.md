

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr>
<th>layer name</th>
<th>output size</th>
<th>18-layer</th>
<th>34-layer</th>
<th>50-layer</th>
<th>101-layer</th>
<th>152-layer</th>
</tr>
</thead>
<tbody>
<tr>
<td>conv1</td>
<td>112×112</td>
<td>7×7, 64, stride 2</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>conv2_x</td>
<td>56×56</td>
<td>3×3 max pool, stride 2</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
<td>[3×3, 64]×2</td>
<td>[3×3, 64]×3</td>
<td>[1×1, 64]3×3, 641×1, 256</td>
<td>[1×1, 64]3×3, 641×1, 256</td>
<td>[1×1, 64]3×3, 641×1, 256</td>
</tr>
<tr>
<td>conv3_x</td>
<td>28×28</td>
<td>[3×3, 128]×2</td>
<td>[3×3, 128]×4</td>
<td>[1×1, 128]3×3, 1281×1, 512</td>
<td>[1×1, 128]3×3, 1281×1, 512</td>
<td>[1×1, 128]3×3, 1281×1, 512</td>
</tr>
<tr>
<td>conv4_x</td>
<td>14×14</td>
<td>[3×3, 256]×2</td>
<td>[3×3, 256]×6</td>
<td>[1×1, 256]3×3, 2561×1, 1024</td>
<td>[1×1, 256]3×3, 2561×1, 1024</td>
<td>[1×1, 256]3×3, 2561×1, 1024</td>
</tr>
<tr>
<td>conv5_x</td>
<td>7×7</td>
<td>[3×3, 512]×2</td>
<td>[3×3, 512]×3</td>
<td>[1×1, 512]3×3, 5121×1, 2048</td>
<td>[1×1, 512]3×3, 5121×1, 2048</td>
<td>[1×1, 512]3×3, 5121×1, 2048</td>
</tr>
<tr>
<td></td>
<td>1×1</td>
<td>average pool, 1000-d fc, softmax</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>FLOPs</td>
<td></td>
<td>1.8×109</td>
<td>3.6×109</td>
<td>3.8×109</td>
<td>7.6×109</td>
<td>11.3×109</td>
</tr>
</tbody>
</table>

![](img-4.jpeg) Figure 4. Training on ImageNet. Thin curves denote
training error, and bold curves denote validation error of the center
crops. Left: plain networks of 18 and 34 layers. Right: ResNets of 18
and 34 layers. In this plot, the residual networks have no extra
parameter compared to their plain counterparts.

<figure>
<img src="img-5.jpeg" alt="img-5.jpeg" />
<figcaption aria-hidden="true">img-5.jpeg</figcaption>
</figure>

Table 1. Architectures for ImageNet. Building blocks are shown in
brackets (see also Fig. 5), with the numbers of blocks stacked.
Down-sampling is performed by conv3_1, conv4_1, and conv5_1 with a
stride of 2.

<table>
<thead>
<tr>
<th></th>
<th>plain</th>
<th>ResNet</th>
</tr>
</thead>
<tbody>
<tr>
<td>18 layers</td>
<td>27.94</td>
<td>27.88</td>
</tr>
<tr>
<td>34 layers</td>
<td>28.54</td>
<td>25.03</td>
</tr>
</tbody>
</table>

Table 2. Top-1 error (%, 10-crop testing) on ImageNet validation. Here
the ResNets have no extra parameter compared to their plain
counterparts. Fig. 4 shows the training procedures.

34-layer plain net has higher training error throughout the whole
training procedure, even though the solution space of the 18-layer plain
network is a subspace of that of the 34-layer one.

We argue that this optimization difficulty is unlikely to be caused by
vanishing gradients. These plain networks are trained with BN \[16\],
which ensures forward propagated signals to have non-zero variances. We
also verify that the backward propagated gradients exhibit healthy norms
with BN. So neither forward nor backward signals vanish. In fact, the
34-layer plain net is still able to achieve competitive accuracy (Table
3), suggesting that the solver works to some extent. We conjecture that
the deep plain nets may have exponentially low convergence rates, which
impact the

reducing of the training error <sup>3</sup> . The reason for such
optimization difficulties will be studied in the future.

Residual Networks. Next we evaluate 18-layer and 34-layer residual nets
(ResNets). The baseline architectures are the same as the above plain
nets, expect that a shortcut connection is added to each pair of 3 × 3
filters as in Fig. 3 (right). In the first comparison (Table 2 and Fig.
4 right), we use identity mapping for all shortcuts and zero-padding for
increasing dimensions (option A). So they have no extra parameter
compared to the plain counterparts.

We have three major observations from Table 2 and Fig. 4. First, the
situation is reversed with residual learning – the 34-layer ResNet is
better than the 18-layer ResNet (by 2.8% ). More importantly, the
34-layer ResNet exhibits considerably lower training error and is
generalizable to the validation data. This indicates that the
degradation problem is well addressed in this setting and we manage to
obtain accuracy gains from increased depth.

Second, compared to its plain counterpart, the 34-layer
