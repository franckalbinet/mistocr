

<table>
<thead>
<tr>
<th style="text-align: left;">model</th>
<th style="text-align: center;">top-1 err.</th>
<th style="text-align: center;">top-5 err.</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">VGG-16 [41]</td>
<td style="text-align: center;">28.07</td>
<td style="text-align: center;">9.33</td>
</tr>
<tr>
<td style="text-align: left;">GoogLeNet [44]</td>
<td style="text-align: center;">-</td>
<td style="text-align: center;">9.15</td>
</tr>
<tr>
<td style="text-align: left;">PReLU-net [13]</td>
<td style="text-align: center;">24.27</td>
<td style="text-align: center;">7.38</td>
</tr>
<tr>
<td style="text-align: left;">plain-34</td>
<td style="text-align: center;">28.54</td>
<td style="text-align: center;">10.02</td>
</tr>
<tr>
<td style="text-align: left;">ResNet-34 A</td>
<td style="text-align: center;">25.03</td>
<td style="text-align: center;">7.76</td>
</tr>
<tr>
<td style="text-align: left;">ResNet-34 B</td>
<td style="text-align: center;">24.52</td>
<td style="text-align: center;">7.46</td>
</tr>
<tr>
<td style="text-align: left;">ResNet-34 C</td>
<td style="text-align: center;">24.19</td>
<td style="text-align: center;">7.40</td>
</tr>
<tr>
<td style="text-align: left;">ResNet-50</td>
<td style="text-align: center;">22.85</td>
<td style="text-align: center;">6.71</td>
</tr>
<tr>
<td style="text-align: left;">ResNet-101</td>
<td style="text-align: center;">21.75</td>
<td style="text-align: center;">6.05</td>
</tr>
<tr>
<td style="text-align: left;">ResNet-152</td>
<td style="text-align: center;"><span
class="math inline"><strong>2</strong><strong>1</strong><strong>.</strong><strong>4</strong><strong>3</strong></span></td>
<td style="text-align: center;"><span
class="math inline"><strong>5</strong><strong>.</strong><strong>7</strong><strong>1</strong></span></td>
</tr>
</tbody>
</table>

Table 3. Error rates ( %, 10-crop testing) on ImageNet validation.
VGG-16 is based on our test. ResNet-50/101/152 are of option B that only
uses projections for increasing dimensions.

<table>
<thead>
<tr>
<th style="text-align: left;">method</th>
<th style="text-align: center;">top-1 err.</th>
<th style="text-align: center;">top-5 err.</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">VGG [41] (ILSVRC’14)</td>
<td style="text-align: center;">-</td>
<td style="text-align: center;"><span
class="math inline">8.43<sup>†</sup></span></td>
</tr>
<tr>
<td style="text-align: left;">GoogLeNet [44] (ILSVRC’14)</td>
<td style="text-align: center;">-</td>
<td style="text-align: center;">7.89</td>
</tr>
<tr>
<td style="text-align: left;">VGG [41] (v5)</td>
<td style="text-align: center;">24.4</td>
<td style="text-align: center;">7.1</td>
</tr>
<tr>
<td style="text-align: left;">PReLU-net [13]</td>
<td style="text-align: center;">21.59</td>
<td style="text-align: center;">5.71</td>
</tr>
<tr>
<td style="text-align: left;">BN-inception [16]</td>
<td style="text-align: center;">21.99</td>
<td style="text-align: center;">5.81</td>
</tr>
<tr>
<td style="text-align: left;">ResNet-34 B</td>
<td style="text-align: center;">21.84</td>
<td style="text-align: center;">5.71</td>
</tr>
<tr>
<td style="text-align: left;">ResNet-34 C</td>
<td style="text-align: center;">21.53</td>
<td style="text-align: center;">5.60</td>
</tr>
<tr>
<td style="text-align: left;">ResNet-50</td>
<td style="text-align: center;">20.74</td>
<td style="text-align: center;">5.25</td>
</tr>
<tr>
<td style="text-align: left;">ResNet-101</td>
<td style="text-align: center;">19.87</td>
<td style="text-align: center;">4.60</td>
</tr>
<tr>
<td style="text-align: left;">ResNet-152</td>
<td style="text-align: center;"><span
class="math inline"><strong>1</strong><strong>9</strong><strong>.</strong><strong>3</strong><strong>8</strong></span></td>
<td style="text-align: center;"><span
class="math inline"><strong>4</strong><strong>.</strong><strong>4</strong><strong>9</strong></span></td>
</tr>
</tbody>
</table>

Table 4. Error rates (%) of single-model results on the ImageNet
validation set (except <sup>†</sup> reported on the test set).

<table>
<thead>
<tr>
<th style="text-align: left;">method</th>
<th style="text-align: center;">top-5 err. (test)</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">VGG [41] (ILSVRC’14)</td>
<td style="text-align: center;">7.32</td>
</tr>
<tr>
<td style="text-align: left;">GoogLeNet [44] (ILSVRC’14)</td>
<td style="text-align: center;">6.66</td>
</tr>
<tr>
<td style="text-align: left;">VGG [41] (v5)</td>
<td style="text-align: center;">6.8</td>
</tr>
<tr>
<td style="text-align: left;">PReLU-net [13]</td>
<td style="text-align: center;">4.94</td>
</tr>
<tr>
<td style="text-align: left;">BN-inception [16]</td>
<td style="text-align: center;">4.82</td>
</tr>
<tr>
<td style="text-align: left;">ResNet (ILSVRC’15)</td>
<td style="text-align: center;"><span
class="math inline"><strong>3</strong><strong>.</strong><strong>5</strong><strong>7</strong></span></td>
</tr>
</tbody>
</table>

Table 5. Error rates (%) of ensembles. The top-5 error is on the test
set of ImageNet and reported by the test server.

ResNet reduces the top-1 error by 3.5% (Table 2), resulting from the
successfully reduced training error (Fig. 4 right *v**s*. left). This
comparison verifies the effectiveness of residual learning on extremely
deep systems.

Last, we also note that the 18-layer plain/residual nets are comparably
accurate (Table 2), but the 18-layer ResNet converges faster (Fig. 4
right vs. left). When the net is “not overly deep” (18 layers here), the
current SGD solver is still able to find good solutions to the plain
net. In this case, the ResNet eases the optimization by providing faster
convergence at the early stage.

Identity vs. Projection Shortcuts. We have shown that ![](img-4.jpeg)
AI-generated image description: *** Neural network architecture diagram
showing two parallel residual blocks. The left block processes a
64-dimensional input through two 3x3 convolutional layers with 64
filters each, connected by ReLU activations, with a skip connection that
adds the input to the output before a final ReLU. The right block
processes a 256-dimensional input through a 1x1 convolution (64
filters), followed by a 3x3 convolution (64 filters), then a 1x1
convolution (256 filters), with ReLU activations between layers and a
skip connection adding the original input to the final output before
ReLU. Both blocks demonstrate residual learning with identity mappings,
commonly used in ResNet-style architectures. The left block maintains
dimensionality while the right block uses bottleneck design with
dimension reduction and expansion. ***

Figure 5. A deeper residual function ℱ for ImageNet. Left: a building
block (on 56 × 56 feature maps) as in Fig. 3 for ResNet34. Right: a
“bottleneck” building block for ResNet-50/101/152. parameter-free,
identity shortcuts help with training. Next we investigate projection
shortcuts (Eqn.(2)). In Table 3 we compare three options: (A)
zero-padding shortcuts are used for increasing dimensions, and all
shortcuts are parameterfree (the same as Table 2 and Fig. 4 right); (B)
projection shortcuts are used for increasing dimensions, and other
shortcuts are identity; and (C) all shortcuts are projections.

Table 3 shows that all three options are considerably better than the
plain counterpart. B is slightly better than A. We argue that this is
because the zero-padded dimensions in A indeed have no residual
learning. C is marginally better than B , and we attribute this to the
extra parameters introduced by many (thirteen) projection shortcuts. But
the small differences among A/B/C indicate that projection shortcuts are
not essential for addressing the degradation problem. So we do not use
option C in the rest of this paper, to reduce memory/time complexity and
model sizes. Identity shortcuts are particularly important for not
increasing the complexity of the bottleneck architectures that are
introduced below.

Deeper Bottleneck Architectures. Next we describe our deeper nets for
ImageNet. Because of concerns on the training time that we can afford,
we modify the building block as a bottleneck design <sup>4</sup>. For
each residual function ℱ, we use a stack of 3 layers instead of 2 (Fig.
5). The three layers are 1 × 1, 3 × 3, and 1 × 1 convolutions, where the
1 × 1 layers are responsible for reducing and then increasing
(restoring) dimensions, leaving the 3 × 3 layer a bottleneck with
smaller input/output dimensions. Fig. 5 shows an example, where both
designs have similar time complexity.

The parameter-free identity shortcuts are particularly important for the
bottleneck architectures. If the identity shortcut in Fig. 5 (right) is
replaced with projection, one can show that the time complexity and
model size are doubled, as the shortcut is connected to the two
high-dimensional ends. So identity shortcuts lead to more efficient
models for the bottleneck designs.

50-layer ResNet: We replace each 2-layer block in the

\[^0\] \[^0\]: <sup>4</sup> Deeper non-bottleneck ResNets (e.g., Fig. 5
left) also gain accuracy from increased depth (as shown on CIFAR-10),
but are not as economical as the bottleneck ResNets. So the usage of
bottleneck designs is mainly due to practical considerations. We further
note that the degradation problem of plain nets is also witnessed for
the bottleneck designs.
