

Table 1: Maximum path lengths, per-layer complexity and minimum number
of sequential operations for different layer types. *n* is the sequence
length, *d* is the representation dimension, *k* is the kernel size of
convolutions and *r* the size of the neighborhood in restricted
self-attention.

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 26%" />
<col style="width: 26%" />
<col style="width: 26%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;">Layer Type</th>
<th style="text-align: center;">Complexity per Layer</th>
<th style="text-align: center;">Sequential <br> Operations</th>
<th style="text-align: center;">Maximum Path Length</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">Self-Attention</td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(<em>n</em><sup>2</sup> ⋅ <em>d</em>)</span></td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(1)</span></td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(1)</span></td>
</tr>
<tr>
<td style="text-align: left;">Recurrent</td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(<em>n</em> ⋅ <em>d</em><sup>2</sup>)</span></td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(<em>n</em>)</span></td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(<em>n</em>)</span></td>
</tr>
<tr>
<td style="text-align: left;">Convolutional</td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(<em>k</em> ⋅ <em>n</em> ⋅ <em>d</em><sup>2</sup>)</span></td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(1)</span></td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(log<sub><em>k</em></sub>(<em>n</em>))</span></td>
</tr>
<tr>
<td style="text-align: left;">Self-Attention (restricted)</td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(<em>r</em> ⋅ <em>n</em> ⋅ <em>d</em>)</span></td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(1)</span></td>
<td style="text-align: center;"><span
class="math inline"><em>O</em>(<em>n</em>/<em>r</em>)</span></td>
</tr>
</tbody>
</table>

# 3.5 Positional Encoding

Since our model contains no recurrence and no convolution, in order for
the model to make use of the order of the sequence, we must inject some
information about the relative or absolute position of the tokens in the
sequence. To this end, we add “positional encodings” to the input
embeddings at the bottoms of the encoder and decoder stacks. The
positional encodings have the same dimension *d*<sub>model </sub> as the
embeddings, so that the two can be summed. There are many choices of
positional encodings, learned and fixed \[9\]. In this work, we use sine
and cosine functions of different frequencies:

$$
\begin{aligned}
P E\_{(p o s, 2 i)} & =\sin \left(\operatorname{pos} / 10000^{2 i / d\_{\text {model }}}\right) \\
P E\_{(p o s, 2 i+1)} & =\cos \left(\operatorname{pos} / 10000^{2 i / d\_{\text {model }}}\right)
\end{aligned}
$$

where pos is the position and *i* is the dimension. That is, each
dimension of the positional encoding corresponds to a sinusoid. The
wavelengths form a geometric progression from 2*π* to 10000 ⋅ 2*π*. We
chose this function because we hypothesized it would allow the model to
easily learn to attend by relative positions, since for any fixed offset
*k*, *P**E*<sub>pos  + *k*</sub> can be represented as a linear function
of *P**E*<sub>pos </sub>. We also experimented with using learned
positional embeddings \[9\] instead, and found that the two versions
produced nearly identical results (see Table 3 row (E)). We chose the
sinusoidal version because it may allow the model to extrapolate to
sequence lengths longer than the ones encountered during training.

## 4 Why Self-Attention

In this section we compare various aspects of self-attention layers to
the recurrent and convolutional layers commonly used for mapping one
variable-length sequence of symbol representations
(*x*<sub>1</sub>, …, *x*<sub>*n*</sub>) to another sequence of equal
length (*z*<sub>1</sub>, …, *z*<sub>*n*</sub>), with
*x*<sub>*i*</sub>, *z*<sub>*i*</sub> ∈ ℝ<sup>*d*</sup>, such as a hidden
layer in a typical sequence transduction encoder or decoder. Motivating
our use of self-attention we consider three desiderata. One is the total
computational complexity per layer. Another is the amount of computation
that can be parallelized, as measured by the minimum number of
sequential operations required. The third is the path length between
long-range dependencies in the network. Learning long-range dependencies
is a key challenge in many sequence transduction tasks. One key factor
affecting the ability to learn such dependencies is the length of the
paths forward and backward signals have to traverse in the network. The
shorter these paths between any combination of positions in the input
and output sequences, the easier it is to learn long-range dependencies
\[12\]. Hence we also compare the maximum path length between any two
input and output positions in networks composed of the different layer
types. As noted in Table 1, a self-attention layer connects all
positions with a constant number of sequentially executed operations,
whereas a recurrent layer requires *O*(*n*) sequential operations. In
terms of computational complexity, self-attention layers are faster than
recurrent layers when the sequence
