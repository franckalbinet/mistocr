

output values. These are concatenated and once again projected,
resulting in the final values, as depicted in Figure 2.

Multi-head attention allows the model to jointly attend to information
from different representation subspaces at different positions. With a
single attention head, averaging inhibits this.

$$
\begin{aligned}
\operatorname{MultiHead}(Q, K, V) & =\operatorname{Concat}\left(\operatorname{head}\_{1}, \ldots, \text { head }\_{h}\right) W^{O} \\
\text { where head }\_{i} & =\operatorname{Attention}\left(Q W\_{i}^{Q}, K W\_{i}^{K}, V W\_{i}^{V}\right)
\end{aligned}
$$

Where the projections are parameter matrices
*W*<sub>*i*</sub><sup>*Q*</sup> ∈ ℝ<sup>*d*<sub>model </sub> × *d*<sub>*k*</sub></sup>, *W*<sub>*i*</sub><sup>*K*</sup> ∈ ℝ<sup>*d*<sub>model </sub> × *d*<sub>*k*</sub></sup>, *W*<sub>*i*</sub><sup>*V*</sup> ∈ ℝ<sup>*d*<sub>model </sub> × *d*<sub>*v*</sub></sup>
and
*W*<sup>*O*</sup> ∈ ℝ<sup>*h**d*<sub>*v*</sub> × *d*<sub>model </sub></sup>.

In this work we employ *h* = 8 parallel attention layers, or heads. For
each of these we use
*d*<sub>*k*</sub> = *d*<sub>*v*</sub> = *d*<sub>model </sub>/*h* = 64.
Due to the reduced dimension of each head, the total computational cost
is similar to that of single-head attention with full dimensionality.

# 3.2.3 Applications of Attention in our Model

The Transformer uses multi-head attention in three different ways:

- In “encoder-decoder attention” layers, the queries come from the
  previous decoder layer, and the memory keys and values come from the
  output of the encoder. This allows every position in the decoder to
  attend over all positions in the input sequence. This mimics the
  typical encoder-decoder attention mechanisms in sequence-to-sequence
  models such as \[38, 2, 9\].
- The encoder contains self-attention layers. In a self-attention layer
  all of the keys, values and queries come from the same place, in this
  case, the output of the previous layer in the encoder. Each position
  in the encoder can attend to all positions in the previous layer of
  the encoder.
- Similarly, self-attention layers in the decoder allow each position in
  the decoder to attend to all positions in the decoder up to and
  including that position. We need to prevent leftward information flow
  in the decoder to preserve the auto-regressive property. We implement
  this inside of scaled dot-product attention by masking out (setting to
  −∞ ) all values in the input of the softmax which correspond to
  illegal connections. See Figure 2.

### 3.3 Position-wise Feed-Forward Networks

In addition to attention sub-layers, each of the layers in our encoder
and decoder contains a fully connected feed-forward network, which is
applied to each position separately and identically. This consists of
two linear transformations with a ReLU activation in between.

FFN (*x*) = max (0, *x**W*<sub>1</sub> + *b*<sub>1</sub>)*W*<sub>2</sub> + *b*<sub>2</sub>

While the linear transformations are the same across different
positions, they use different parameters from layer to layer. Another
way of describing this is as two convolutions with kernel size 1. The
dimensionality of input and output is *d*<sub>model </sub> = 512, and
the inner-layer has dimensionality *d*<sub>*f**f*</sub> = 2048.

### 3.4 Embeddings and Softmax

Similarly to other sequence transduction models, we use learned
embeddings to convert the input tokens and output tokens to vectors of
dimension *d*<sub>model </sub>. We also use the usual learned linear
transformation and softmax function to convert the decoder output to
predicted next-token probabilities. In our model, we share the same
weight matrix between the two embedding layers and the pre-softmax
linear transformation, similar to \[30\]. In the embedding layers, we
multiply those weights by $\sqrt{d\_{\text {model }}}$.
