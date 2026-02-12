

34-layer net with this 3-layer bottleneck block, resulting in a 50-layer
ResNet (Table 1). We use option B for increasing dimensions. This model
has 3.8 billion FLOPs.

101-layer and 152-layer ResNets: We construct 101-layer and 152-layer
ResNets by using more 3-layer blocks (Table 1). Remarkably, although the
depth is significantly increased, the 152-layer ResNet (11.3 billion
FLOPs) still has lower complexity than VGG-16/19 nets (15.3/19.6 billion
FLOPs).

The 50/101/152-layer ResNets are more accurate than the 34-layer ones by
considerable margins (Table 3 and 4). We do not observe the degradation
problem and thus enjoy significant accuracy gains from considerably
increased depth. The benefits of depth are witnessed for all evaluation
metrics (Table 3 and 4).

Comparisons with State-of-the-art Methods. In Table 4 we compare with
the previous best single-model results. Our baseline 34-layer ResNets
have achieved very competitive accuracy. Our 152-layer ResNet has a
single-model top-5 validation error of 4.49% . This single-model result
outperforms all previous ensemble results (Table 5). We combine six
models of different depth to form an ensemble (only with two 152-layer
ones at the time of submitting). This leads to 3.57% top-5 error on the
test set (Table 5). This entry won the 1st place in ILSVRC 2015.

# 4.2. CIFAR-10 and Analysis

We conducted more studies on the CIFAR-10 dataset \[20\], which consists
of 50k training images and 10k testing images in 10 classes. We present
experiments trained on the training set and evaluated on the test set.
Our focus is on the behaviors of extremely deep networks, but not on
pushing the state-of-the-art results, so we intentionally use simple
architectures as follows.

The plain/residual architectures follow the form in Fig. 3
(middle/right). The network inputs are 32 × 32 images, with the
per-pixel mean subtracted. The first layer is 3 × 3 convolutions. Then
we use a stack of 6*n* layers with 3 × 3 convolutions on the feature
maps of sizes {32, 16, 8} respectively, with 2*n* layers for each
feature map size. The numbers of filters are {16, 32, 64} respectively.
The subsampling is performed by convolutions with a stride of 2. The
network ends with a global average pooling, a 10-way fully-connected
layer, and softmax. There are totally 6*n* + 2 stacked weighted layers.
The following table summarizes the architecture:

<table>
<thead>
<tr>
<th>output map size</th>
<th>32×32</th>
<th>16×16</th>
<th>8×8</th>
</tr>
</thead>
<tbody>
<tr>
<td># layers</td>
<td>1+2n</td>
<td>2n</td>
<td>2n</td>
</tr>
<tr>
<td># filters</td>
<td>16</td>
<td>32</td>
<td>64</td>
</tr>
</tbody>
</table>

When shortcut connections are used, they are connected to the pairs of
3 × 3 layers (totally 3*n* shortcuts). On this dataset we use identity
shortcuts in all cases (i.e., option A),

<table>
<thead>
<tr>
<th>method</th>
<th></th>
<th></th>
<th>error (%)</th>
</tr>
</thead>
<tbody>
<tr>
<td>Maxout [10]</td>
<td></td>
<td></td>
<td>9.38</td>
</tr>
<tr>
<td>NIN [25]</td>
<td></td>
<td></td>
<td>8.81</td>
</tr>
<tr>
<td>DSN [24]</td>
<td></td>
<td></td>
<td>8.22</td>
</tr>
<tr>
<td></td>
<td># layers</td>
<td># params</td>
<td></td>
</tr>
<tr>
<td>FitNet [35]</td>
<td>19</td>
<td>2.5M</td>
<td>8.39</td>
</tr>
<tr>
<td>Highway [42, 43]</td>
<td>19</td>
<td>2.3M</td>
<td>7.54 (7.72±0.16)</td>
</tr>
<tr>
<td>Highway [42, 43]</td>
<td>32</td>
<td>1.25M</td>
<td>8.80</td>
</tr>
<tr>
<td>ResNet</td>
<td>20</td>
<td>0.27M</td>
<td>8.75</td>
</tr>
<tr>
<td>ResNet</td>
<td>32</td>
<td>0.46M</td>
<td>7.51</td>
</tr>
<tr>
<td>ResNet</td>
<td>44</td>
<td>0.66M</td>
<td>7.17</td>
</tr>
<tr>
<td>ResNet</td>
<td>56</td>
<td>0.85M</td>
<td>6.97</td>
</tr>
<tr>
<td>ResNet</td>
<td>110</td>
<td>1.7M</td>
<td>6.43 (6.61±0.16)</td>
</tr>
<tr>
<td>ResNet</td>
<td>1202</td>
<td>19.4M</td>
<td>7.93</td>
</tr>
</tbody>
</table>

Table 6. Classification error on the CIFAR-10 test set. All methods are
with data augmentation. For ResNet-110, we run it 5 times and show “best
(mean±std)” as in \[43\].

so our residual models have exactly the same depth, width, and number of
parameters as the plain counterparts.

We use a weight decay of 0.0001 and momentum of 0.9, and adopt the
weight initialization in \[13\] and BN \[16\] but with no dropout. These
models are trained with a minibatch size of 128 on two GPUs. We start
with a learning rate of 0.1, divide it by 10 at 32k and 48k iterations,
and terminate training at 64k iterations, which is determined on a
45k/5k train/val split. We follow the simple data augmentation in \[24\]
for training: 4 pixels are padded on each side, and a 32 × 32 crop is
randomly sampled from the padded image or its horizontal flip. For
testing, we only evaluate the single view of the original 32 × 32 image.

We compare *n* = {3, 5, 7, 9} , leading to 20, 32, 44, and 56-layer
networks. Fig. 6 (left) shows the behaviors of the plain nets. The deep
plain nets suffer from increased depth, and exhibit higher training
error when going deeper. This phenomenon is similar to that on ImageNet
(Fig. 4, left) and on MNIST (see \[42\]), suggesting that such an
optimization difficulty is a fundamental problem.

Fig. 6 (middle) shows the behaviors of ResNets. Also similar to the
ImageNet cases (Fig. 4, right), our ResNets manage to overcome the
optimization difficulty and demonstrate accuracy gains when the depth
increases.

We further explore *n* = 18 that leads to a 110-layer ResNet. In this
case, we find that the initial learning rate of 0.1 is slightly too
large to start converging. So we use 0.01 to warm up the training until
the training error is below 80% (about 400 iterations), and then go back
to 0.1 and continue training. The rest of the learning schedule is as
done previously. This 110-layer network converges well (Fig. 6, middle).
It has fewer parameters than other deep and thin
