

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
<td></td>
<td></td>
<td>3×3 max pool, stride 2</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>conv2_x</td>
<td>56×56</td>
<td>3×3, 64</td>
<td>2</td>
<td>3×3, 64</td>
<td>3</td>
<td>1×1, 64</td>
</tr>
<tr>
<td></td>
<td></td>
<td>3×3, 64</td>
<td></td>
<td>3×3, 64</td>
<td></td>
<td>3×3, 64</td>
</tr>
<tr>
<td></td>
<td></td>
<td>3×3, 64</td>
<td></td>
<td>1×1, 256</td>
<td></td>
<td>1×1, 256</td>
</tr>
<tr>
<td>conv3_x</td>
<td>28×28</td>
<td>3×3, 128</td>
<td>2</td>
<td>3×3, 128</td>
<td>4</td>
<td>1×1, 128</td>
</tr>
<tr>
<td></td>
<td></td>
<td>3×3, 128</td>
<td></td>
<td>3×3, 128</td>
<td></td>
<td>3×3, 128</td>
</tr>
<tr>
<td></td>
<td></td>
<td>3×3, 128</td>
<td></td>
<td>1×1, 512</td>
<td></td>
<td>1×1, 512</td>
</tr>
<tr>
<td>conv4_x</td>
<td>14×14</td>
<td>3×3, 256</td>
<td>2</td>
<td>3×3, 256</td>
<td>6</td>
<td>1×1, 256</td>
</tr>
<tr>
<td></td>
<td></td>
<td>3×3, 256</td>
<td></td>
<td>3×3, 256</td>
<td></td>
<td>3×3, 256</td>
</tr>
<tr>
<td></td>
<td></td>
<td>3×3, 256</td>
<td></td>
<td>1×1, 1024</td>
<td></td>
<td>1×1, 1024</td>
</tr>
<tr>
<td>conv5_x</td>
<td>7×7</td>
<td>3×3, 512</td>
<td>2</td>
<td>3×3, 512</td>
<td>3</td>
<td>1×1, 512</td>
</tr>
<tr>
<td></td>
<td></td>
<td>3×3, 512</td>
<td></td>
<td>3×3, 512</td>
<td></td>
<td>3×3, 512</td>
</tr>
<tr>
<td></td>
<td></td>
<td>3×3, 512</td>
<td></td>
<td>1×1, 2048</td>
<td></td>
<td>1×1, 2048</td>
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
<td>1.8×10^{9}</td>
<td>3.6×10^{9}</td>
<td>3.8×10^{9}</td>
<td>7.6×10^{9}</td>
<td>11.3×10^{9}</td>
</tr>
</tbody>
</table>

Table 1. Architectures for ImageNet. Building blocks are shown in
brackets (see also Fig. 5), with the numbers of blocks stacked.
Downsampling is performed by conv3_1, conv4_1, and conv5_1 with a stride
of 2.

![](img-3.jpeg) AI-generated image description: *** Two side-by-side
line graphs comparing training error rates over iterations for plain and
ResNet architectures with 18 and 34 layers. Left panel shows plain-18
(cyan) and plain-34 (dark red) networks, while right panel shows
ResNet-18 (cyan) and ResNet-34 (dark red) networks. The x-axis
represents iterations (×1e4) from 0 to 50, and y-axis shows error
percentage from 20% to 60%. Key findings: In plain networks, the deeper
34-layer model performs worse than the 18-layer model, with higher error
rates throughout training. In ResNet architectures, the 34-layer model
achieves lower error rates than the 18-layer model, demonstrating that
residual connections enable effective training of deeper networks. Both
architectures show rapid initial error reduction followed by gradual
convergence, with lighter colored lines appearing to represent
individual training runs or validation curves. ***

Figure 4. Training on **ImageNet**. Thin curves denote training error,
and bold curves denote validation error of the center crops. Left: plain
networks of 18 and 34 layers. Right: ResNets of 18 and 34 layers. In
this plot, the residual networks have no extra parameter compared to
their plain counterparts.

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

34-layer plain net has higher *training* error throughout the whole
training procedure, even though the solution space of the 18-layer plain
network is a subspace of that of the 34-layer one.

We argue that this optimization difficulty is *unlikely* to be caused by
vanishing gradients. These plain networks are trained with BN \[16\],
which ensures forward propagated signals to have non-zero variances. We
also verify that the backward propagated gradients exhibit healthy norms
with BN. So neither forward nor backward signals vanish. In fact, the
34-layer plain net is still able to achieve competitive accuracy (Table
3), suggesting that the solver works to some extent. We conjecture that
the deep plain nets may have exponentially low convergence rates, which
impact the reducing of the training error^{3}. The reason for such
optimization difficulties will be studied in the future.

**Residual Networks.** Next we evaluate 18-layer and 34-layer residual
nets (*ResNets*). The baseline architectures are the same as the above
plain nets, except that a shortcut connection is added to each pair of
3×3 filters as in Fig. 3 (right). In the first comparison (Table 2 and
Fig. 4 right), we use identity mapping for all shortcuts and
zero-padding for increasing dimensions (option A). So they have *no
extra parameter* compared to the plain counterparts.

We have three major observations from Table 2 and Fig. 4. First, the
situation is reversed with residual learning – the 34-layer ResNet is
better than the 18-layer ResNet (by 2.8%). More importantly, the
34-layer ResNet exhibits considerably lower training error and is
generalizable to the validation data. This indicates that the
degradation problem is well addressed in this setting and we manage to
obtain accuracy gains from increased depth.

Second, compared to its plain counterpart, the 34-layer

^{3}We have experimented with more training iterations (3×) and still
observed the degradation problem, suggesting that this problem cannot be
feasibly addressed by simply using more iterations.
