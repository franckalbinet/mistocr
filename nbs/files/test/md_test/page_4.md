![img-1.jpeg](img-1.jpeg)
AI-generated image description:
___
This is a computational flow diagram showing the architecture of a neural network attention mechanism, specifically depicting the scaled dot-product attention computation. The diagram shows a bottom-up flow with three inputs labeled Q (Query), K (Key), and V (Value). The processing steps are: (1) MatMul operation combining Q and K inputs, (2) Scale operation to normalize the result, (3) optional Mask operation indicated by 'Mask (opt.)', (4) SoftMax activation function shown in green, (5) another MatMul operation combining the SoftMax output with V, and finally outputting the result at the top. This represents the standard transformer attention mechanism formula: Attention(Q,K,V) = softmax(QK^T/√d_k)V, where the scaling factor prevents gradients from becoming too small in higher dimensions.
___
Scaled Dot-Product Attention

![img-2.jpeg](img-2.jpeg)
AI-generated image description:
___
Architecture diagram of a Scaled Dot-Product Attention mechanism, a fundamental component in transformer neural networks. The diagram shows the data flow from bottom to top: three inputs labeled V (Value), K (Key), and Q (Query) each pass through separate Linear transformation layers. These outputs feed into a Scaled Dot-Product Attention block (shown in purple/lavender), which has a parameter 'h' indicating multi-head attention. The attention mechanism's output goes through a Concat (concatenation) operation, followed by a final Linear layer at the top. Arrows indicate the direction of data flow through the network. This is a standard representation of the multi-head attention architecture used in transformer models.
___
Multi-Head Attention
Figure 2: (left) Scaled Dot-Product Attention. (right) Multi-Head Attention consists of several attention layers running in parallel.

of the values, where the weight assigned to each value is computed by a compatibility function of the query with the corresponding key.

#### 3.2.1 Scaled Dot-Product Attention ... page 4

We call our particular attention "Scaled Dot-Product Attention" (Figure 2). The input consists of queries and keys of dimension  $d_{k}$ , and values of dimension  $d_{v}$ . We compute the dot products of the query with all keys, divide each by  $\sqrt{d_k}$ , and apply a softmax function to obtain the weights on the values.

In practice, we compute the attention function on a set of queries simultaneously, packed together into a matrix  $Q$ . The keys and values are also packed together into matrices  $K$  and  $V$ . We compute the matrix of outputs as:

$$
\operatorname {A t t e n t i o n} (Q, K, V) = \operatorname {s o f t m a x} \left(\frac {Q K ^ {T}}{\sqrt {d _ {k}}}\right) V \tag {1}
$$

The two most commonly used attention functions are additive attention [2], and dot-product (multiplicative) attention. Dot-product attention is identical to our algorithm, except for the scaling factor of  $\frac{1}{\sqrt{d_k}}$ . Additive attention computes the compatibility function using a feed-forward network with a single hidden layer. While the two are similar in theoretical complexity, dot-product attention is much faster and more space-efficient in practice, since it can be implemented using highly optimized matrix multiplication code.

While for small values of  $d_{k}$  the two mechanisms perform similarly, additive attention outperforms dot product attention without scaling for larger values of  $d_{k}$  [3]. We suspect that for large values of  $d_{k}$ , the dot products grow large in magnitude, pushing the softmax function into regions where it has extremely small gradients. To counteract this effect, we scale the dot products by  $\frac{1}{\sqrt{d_k}}$ .

#### 3.2.2 Multi-Head Attention ... page 4

Instead of performing a single attention function with  $d_{\mathrm{model}}$ -dimensional keys, values and queries, we found it beneficial to linearly project the queries, keys and values  $h$  times with different, learned linear projections to  $d_k$ ,  $d_k$  and  $d_v$  dimensions, respectively. On each of these projected versions of queries, keys and values we then perform the attention function in parallel, yielding  $d_v$ -dimensional