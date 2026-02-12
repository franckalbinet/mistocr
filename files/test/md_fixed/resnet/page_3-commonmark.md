

way networks have not demonstrated accuracy gains with extremely
increased depth (e.g., over 100 layers).

## 3 Deep Residual Learning … page 3

### 3.1 Residual Learning … page 3

Let us consider ℋ(**x**) as an underlying mapping to be fit by a few
stacked layers (not necessarily the entire net), with **x** denoting the
inputs to the first of these layers. If one hypothesizes that multiple
nonlinear layers can asymptotically approximate complicated functions,
then it is equivalent to hypothesize that they can asymptotically
approximate the residual functions, i.e., ℋ(**x**) − **x** (assuming
that the input and output are of the same dimensions). So rather than
expect stacked layers to approximate ℋ(**x**), we explicitly let these
layers approximate a residual function ℱ(**x**) := ℋ(**x**) − **x**. The
original function thus becomes ℱ(**x**) + **x**. Although both forms
should be able to asymptotically approximate the desired functions (as
hypothesized), the ease of learning might be different.

This reformulation is motivated by the counterintuitive phenomena about
the degradation problem (Fig. 1, left). As we discussed in the
introduction, if the added layers can be constructed as identity
mappings, a deeper model should have training error no greater than its
shallower counterpart. The degradation problem suggests that the solvers
might have difficulties in approximating identity mappings by multiple
nonlinear layers. With the residual learning reformulation, if identity
mappings are optimal, the solvers may simply drive the weights of the
multiple nonlinear layers toward zero to approach identity mappings.

In real cases, it is unlikely that identity mappings are optimal, but
our reformulation may help to precondition the problem. If the optimal
function is closer to an identity mapping than to a zero mapping, it
should be easier for the solver to find the perturbations with reference
to an identity mapping, than to learn the function as a new one. We show
by experiments (Fig. 7) that the learned residual functions in general
have small responses, suggesting that identity mappings provide
reasonable preconditioning.

### 3.2 Identity Mapping by Shortcuts … page 3

We adopt residual learning to every few stacked layers. A building block
is shown in Fig. 2. Formally, in this paper we consider a building block
defined as:

**y** = ℱ(**x**, {*W*<sub>*i*</sub>}) + **x**. (1)

Here **x** and **y** are the input and output vectors of the layers
considered. The function ℱ(**x**, {*W*<sub>*i*</sub>}) represents the
residual mapping to be learned. For the example in Fig. 2 that has two
layers, ℱ = *W*<sub>2</sub>*σ*(*W*<sub>1</sub>**x**) in which *σ*
denotes ReLU *\[29\]* and the biases are omitted for simplifying
notations. The operation ℱ + **x** is performed by a shortcut connection
and element-wise addition. We adopt the second nonlinearity after the
addition (i.e., *σ*(**y**), see Fig. 2).

The shortcut connections in Eqn.(1) introduce neither extra parameter
nor computation complexity. This is not only attractive in practice but
also important in our comparisons between plain and residual networks.
We can fairly compare plain/residual networks that simultaneously have
the same number of parameters, depth, width, and computational cost
(except for the negligible element-wise addition).

The dimensions of **x** and ℱ must be equal in Eqn.(1). If this is not
the case (e.g., when changing the input/output channels), we can perform
a linear projection *W*<sub>*s*</sub> by the shortcut connections to
match the dimensions:

**y** = ℱ(**x**, {*W*<sub>*i*</sub>}) + *W*<sub>*s*</sub>**x**. (2)

We can also use a square matrix *W*<sub>*s*</sub> in Eqn.(1). But we
will show by experiments that the identity mapping is sufficient for
addressing the degradation problem and is economical, and thus
*W*<sub>*s*</sub> is only used when matching dimensions.

The form of the residual function ℱ is flexible. Experiments in this
paper involve a function ℱ that has two or three layers (Fig. 5), while
more layers are possible. But if ℱ has only a single layer, Eqn.(1) is
similar to a linear layer: **y** = *W*<sub>1</sub>**x** + **x**, for
which we have not observed advantages.

We also note that although the above notations are about fully-connected
layers for simplicity, they are applicable to convolutional layers. The
function ℱ(**x**, {*W*<sub>*i*</sub>}) can represent multiple
convolutional layers. The element-wise addition is performed on two
feature maps, channel by channel.

### 3.3 Network Architectures … page 3

We have tested various plain/residual nets, and have observed consistent
phenomena. To provide instances for discussion, we describe two models
for ImageNet as follows.

Plain Network. … page 3

Our plain baselines (Fig. 3, middle) are mainly inspired by the
philosophy of VGG nets *\[41\]* (Fig. 3, left). The convolutional layers
mostly have 3$$3 filters and follow two simple design rules: (i) for the
same output feature map size, the layers have the same number of
filters; and (ii) if the feature map size is halved, the number of
filters is doubled so as to preserve the time complexity per layer. We
perform downsampling directly by convolutional layers that have a stride
of 2. The network ends with a global average pooling layer and a
1000-way fully-connected layer with softmax. The total number of
weighted layers is 34 in Fig. 3 (middle).

It is worth noticing that our model has fewer filters and lower
complexity than VGG nets *\[41\]* (Fig. 3, left). Our 34-layer baseline
has 3.6 billion FLOPs (multiply-adds), which is only 18% of VGG-19 (19.6
billion FLOPs).
