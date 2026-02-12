

length *n* is smaller than the representation dimensionality *d*, which
is most often the case with sentence representations used by
state-of-the-art models in machine translations, such as word-piece
*\[38\]* and byte-pair *\[31\]* representations. To improve
computational performance for tasks involving very long sequences,
self-attention could be restricted to considering only a neighborhood of
size *r* in the input sequence centered around the respective output
position. This would increase the maximum path length to *O*(*n*/*r*).
We plan to investigate this approach further in future work.

A single convolutional layer with kernel width *k* \< *n* does not
connect all pairs of input and output positions. Doing so requires a
stack of *O*(*n*/*k*) convolutional layers in the case of contiguous
kernels, or *O*(*l**o**g*<sub>*k*</sub>(*n*)) in the case of dilated
convolutions *\[18\]*, increasing the length of the longest paths
between any two positions in the network. Convolutional layers are
generally more expensive than recurrent layers, by a factor of *k*.
Separable convolutions *\[6\]*, however, decrease the complexity
considerably, to *O*(*k* ⋅ *n* ⋅ *d* + *n* ⋅ *d*<sup>2</sup>). Even with
*k* = *n*, however, the complexity of a separable convolution is equal
to the combination of a self-attention layer and a point-wise
feed-forward layer, the approach we take in our model.

As side benefit, self-attention could yield more interpretable models.
We inspect attention distributions from our models and present and
discuss examples in the appendix. Not only do individual attention heads
clearly learn to perform different tasks, many appear to exhibit
behavior related to the syntactic and semantic structure of the
sentences.

## 5 Training … page 7

This section describes the training regime for our models.

### 5.1 Training Data and Batching … page 7

We trained on the standard WMT 2014 English-German dataset consisting of
about 4.5 million sentence pairs. Sentences were encoded using byte-pair
encoding *\[3\]*, which has a shared source-target vocabulary of about
37000 tokens. For English-French, we used the significantly larger WMT
2014 English-French dataset consisting of 36M sentences and split tokens
into a 32000 word-piece vocabulary *\[38\]*. Sentence pairs were batched
together by approximate sequence length. Each training batch contained a
set of sentence pairs containing approximately 25000 source tokens and
25000 target tokens.

### 5.2 Hardware and Schedule … page 7

We trained our models on one machine with 8 NVIDIA P100 GPUs. For our
base models using the hyperparameters described throughout the paper,
each training step took about 0.4 seconds. We trained the base models
for a total of 100,000 steps or 12 hours. For our big models,(described
on the bottom line of table 3), step time was 1.0 seconds. The big
models were trained for 300,000 steps (3.5 days).

### 5.3 Optimizer … page 7

We used the Adam optimizer *\[20\]* with *β*<sub>1</sub> = 0.9,
*β*<sub>2</sub> = 0.98 and *ϵ* = 10<sup>−9</sup>. We varied the learning
rate over the course of training, according to the formula:

*l**r**a**t**e* = *d*<sub>model</sub><sup>−0.5</sup> ⋅ min (*s**t**e**p*\_*n**u**m*<sup>−0.5</sup>, *s**t**e**p*\_*n**u**m* ⋅ *w**a**r**m**u**p*\_*s**t**e**p**s*<sup>−1.5</sup>)
(3)

This corresponds to increasing the learning rate linearly for the first
*w**a**r**m**u**p*\_*s**t**e**p**s* training steps, and decreasing it
thereafter proportionally to the inverse square root of the step number.
We used *w**a**r**m**u**p*\_*s**t**e**p**s* = 4000.

### 5.4 Regularization … page 7

We employ three types of regularization during training:
