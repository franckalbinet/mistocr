![img-1.jpeg](img-1.jpeg)
AI-generated image description:
___
This image shows a technical comparison diagram of two attention mechanisms used in neural networks: Scaled Dot-Product Attention (left) and Multi-Head Attention (right).

Left side - Scaled Dot-Product Attention:
The diagram shows a vertical flow chart with the following sequential operations:
1. Three inputs at the bottom: Q (Query), K (Key), and V (Value)
2. MatMul operation combining Q and K
3. Scale operation
4. Mask (opt.) - optional masking step shown in pink
5. SoftMax operation shown in green
6. MatMul operation combining with V (shown in purple)
7. Output arrow at the top

Right side - Multi-Head Attention:
The diagram illustrates a parallel architecture with:
1. Three inputs at the bottom: V, K, and Q
2. Three parallel Linear transformation layers for each input
3. Multiple parallel Scaled Dot-Product Attention blocks (shown as stacked layers with 'h' indicating the number of heads)
4. Concat operation (shown in yellow) that combines outputs from all attention heads
5. Final Linear transformation layer
6. Output arrow at the top

The visualization effectively demonstrates how Multi-Head Attention uses multiple parallel attention mechanisms (indicated by the stacked/layered appearance) compared to the single-path Scaled Dot-Product Attention, which is a fundamental architectural difference in transformer models.
___

Figure 2: (left) Scaled Dot-Product Attention. (right) Multi-Head Attention consists of several attention layers running in parallel.
of the values, where the weight assigned to each value is computed by a compatibility function of the query with the corresponding key.

#### 3.2.1 Scaled Dot-Product Attention  ... page 4

We call our particular attention "Scaled Dot-Product Attention" (Figure 2). The input consists of queries and keys of dimension $d_{k}$, and values of dimension $d_{v}$. We compute the dot products of the query with all keys, divide each by $\sqrt{d_{k}}$, and apply a softmax function to obtain the weights on the values.

In practice, we compute the attention function on a set of queries simultaneously, packed together into a matrix $Q$. The keys and values are also packed together into matrices $K$ and $V$. We compute the matrix of outputs as:

$$
\operatorname{Attention}(Q, K, V)=\operatorname{softmax}\left(\frac{Q K^{T}}{\sqrt{d_{k}}}\right) V
$$

The two most commonly used attention functions are additive attention [2], and dot-product (multiplicative) attention. Dot-product attention is identical to our algorithm, except for the scaling factor of $\frac{1}{\sqrt{d_{k}}}$. Additive attention computes the compatibility function using a feed-forward network with a single hidden layer. While the two are similar in theoretical complexity, dot-product attention is much faster and more space-efficient in practice, since it can be implemented using highly optimized matrix multiplication code.

While for small values of $d_{k}$ the two mechanisms perform similarly, additive attention outperforms dot product attention without scaling for larger values of $d_{k}$ [3]. We suspect that for large values of $d_{k}$, the dot products grow large in magnitude, pushing the softmax function into regions where it has extremely small gradients ${ }^{4}$. To counteract this effect, we scale the dot products by $\frac{1}{\sqrt{d_{k}}}$.

#### 3.2.2 Multi-Head Attention ... page 4

Instead of performing a single attention function with $d_{\text {model }}$-dimensional keys, values and queries, we found it beneficial to linearly project the queries, keys and values $h$ times with different, learned linear projections to $d_{k}, d_{k}$ and $d_{v}$ dimensions, respectively. On each of these projected versions of queries, keys and values we then perform the attention function in parallel, yielding $d_{v}$-dimensional

[^0]
[^0]:    ${ }^{4}$ To illustrate why the dot products get large, assume that the components of $q$ and $k$ are independent random variables with mean 0 and variance 1 . Then their dot product, $q \cdot k=\sum_{i=1}^{d_{k}} q_{i} k_{i}$, has mean 0 and variance $d_{k}$.