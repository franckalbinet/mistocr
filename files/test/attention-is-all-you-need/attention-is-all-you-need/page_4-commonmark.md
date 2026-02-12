

<figure>
<img src="img-1.jpeg" alt="img-1.jpeg" />
<figcaption aria-hidden="true">img-1.jpeg</figcaption>
</figure>

Figure 2: (left) Scaled Dot-Product Attention. (right) Multi-Head
Attention consists of several attention layers running in parallel. of
the values, where the weight assigned to each value is computed by a
compatibility function of the query with the corresponding key.

# 3.2.1 Scaled Dot-Product Attention

We call our particular attention “Scaled Dot-Product Attention” (Figure
2). The input consists of queries and keys of dimension
*d*<sub>*k*</sub>, and values of dimension *d*<sub>*v*</sub>. We compute
the dot products of the query with all keys, divide each by
$\sqrt{d\_{k}}$, and apply a softmax function to obtain the weights on
the values.

In practice, we compute the attention function on a set of queries
simultaneously, packed together into a matrix *Q*. The keys and values
are also packed together into matrices *K* and *V*. We compute the
matrix of outputs as:

$$
\operatorname{Attention}(Q, K, V)=\operatorname{softmax}\left(\frac{Q K^{T}}{\sqrt{d\_{k}}}\right) V
$$

The two most commonly used attention functions are additive attention
\[2\], and dot-product (multiplicative) attention. Dot-product attention
is identical to our algorithm, except for the scaling factor of
$\frac{1}{\sqrt{d\_{k}}}$. Additive attention computes the compatibility
function using a feed-forward network with a single hidden layer. While
the two are similar in theoretical complexity, dot-product attention is
much faster and more space-efficient in practice, since it can be
implemented using highly optimized matrix multiplication code.

While for small values of *d*<sub>*k*</sub> the two mechanisms perform
similarly, additive attention outperforms dot product attention without
scaling for larger values of *d*<sub>*k*</sub> \[3\]. We suspect that
for large values of *d*<sub>*k*</sub>, the dot products grow large in
magnitude, pushing the softmax function into regions where it has
extremely small gradients <sup>4</sup>. To counteract this effect, we
scale the dot products by $\frac{1}{\sqrt{d\_{k}}}$.

### 3.2.2 Multi-Head Attention

Instead of performing a single attention function with
*d*<sub>model </sub>-dimensional keys, values and queries, we found it
beneficial to linearly project the queries, keys and values *h* times
with different, learned linear projections to
*d*<sub>*k*</sub>, *d*<sub>*k*</sub> and *d*<sub>*v*</sub> dimensions,
respectively. On each of these projected versions of queries, keys and
values we then perform the attention function in parallel, yielding
*d*<sub>*v*</sub>-dimensional

\[^0\] \[^0\]: <sup>4</sup> To illustrate why the dot products get
large, assume that the components of *q* and *k* are independent random
variables with mean 0 and variance 1 . Then their dot product,
$q \cdot k=\sum\_{i=1}^{d\_{k}} q\_{i} k\_{i}$, has mean 0 and variance
*d*<sub>*k*</sub>.
