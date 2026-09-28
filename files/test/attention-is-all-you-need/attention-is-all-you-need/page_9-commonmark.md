

Table 3: Variations on the Transformer architecture. Unlisted values are
identical to those of the base model. All metrics are on the
English-to-German translation development set, newstest2013. Listed
perplexities are per-wordpiece, according to our byte-pair encoding, and
should not be compared to per-word perplexities.

<table style="width:100%;">
<colgroup>
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
<col style="width: 7%" />
</colgroup>
<thead>
<tr>
<th style="text-align: center;"></th>
<th style="text-align: center;"><span
class="math inline"><em>N</em></span></th>
<th style="text-align: center;"><span
class="math inline"><em>d</em><sub>model </sub></span></th>
<th style="text-align: center;"><span
class="math inline"><em>d</em><sub>ff </sub></span></th>
<th style="text-align: center;"><span
class="math inline"><em>h</em></span></th>
<th style="text-align: center;"><span
class="math inline"><em>d</em><sub><em>k</em></sub></span></th>
<th style="text-align: center;"><span
class="math inline"><em>d</em><sub><em>v</em></sub></span></th>
<th style="text-align: center;"><span
class="math inline"><em>P</em><sub>drop </sub></span></th>
<th style="text-align: center;"><span
class="math inline"><em>ϵ</em><sub><em>l</em><em>s</em></sub></span></th>
<th style="text-align: center;">train steps</th>
<th style="text-align: center;">PPL <br> (dev)</th>
<th style="text-align: center;">BLEU <br> (dev)</th>
<th style="text-align: center;">params <span
class="math inline">×10<sup>6</sup></span></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: center;">base</td>
<td style="text-align: center;">6</td>
<td style="text-align: center;">512</td>
<td style="text-align: center;">2048</td>
<td style="text-align: center;">8</td>
<td style="text-align: center;">64</td>
<td style="text-align: center;">64</td>
<td style="text-align: center;">0.1</td>
<td style="text-align: center;">0.1</td>
<td style="text-align: center;">100K</td>
<td style="text-align: center;">4.92</td>
<td style="text-align: center;">25.8</td>
<td style="text-align: center;">65</td>
</tr>
<tr>
<td style="text-align: center;">(A)</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">512</td>
<td style="text-align: center;">512</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">5.29</td>
<td style="text-align: center;">24.9</td>
<td style="text-align: center;"></td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">4</td>
<td style="text-align: center;">128</td>
<td style="text-align: center;">128</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">5.00</td>
<td style="text-align: center;">25.5</td>
<td style="text-align: center;"></td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">16</td>
<td style="text-align: center;">32</td>
<td style="text-align: center;">32</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">4.91</td>
<td style="text-align: center;">25.8</td>
<td style="text-align: center;"></td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">32</td>
<td style="text-align: center;">16</td>
<td style="text-align: center;">16</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">5.01</td>
<td style="text-align: center;">25.4</td>
<td style="text-align: center;"></td>
</tr>
<tr>
<td style="text-align: center;">(B)</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">16</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">5.16</td>
<td style="text-align: center;">25.1</td>
<td style="text-align: center;">58</td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">32</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">5.01</td>
<td style="text-align: center;">25.4</td>
<td style="text-align: center;">60</td>
</tr>
<tr>
<td style="text-align: center;">(C)</td>
<td style="text-align: center;">2</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">6.11</td>
<td style="text-align: center;">23.7</td>
<td style="text-align: center;">36</td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;">4</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">5.19</td>
<td style="text-align: center;">25.3</td>
<td style="text-align: center;">50</td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;">8</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">32</td>
<td style="text-align: center;">32</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">4.88</td>
<td style="text-align: center;">25.5</td>
<td style="text-align: center;">80</td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">256</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">32</td>
<td style="text-align: center;">32</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">5.75</td>
<td style="text-align: center;">24.5</td>
<td style="text-align: center;">28</td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">1024</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">128</td>
<td style="text-align: center;">128</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">4.66</td>
<td style="text-align: center;">26.0</td>
<td style="text-align: center;">168</td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">1024</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">5.12</td>
<td style="text-align: center;">25.4</td>
<td style="text-align: center;">53</td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">4096</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">4.75</td>
<td style="text-align: center;">26.2</td>
<td style="text-align: center;">90</td>
</tr>
<tr>
<td style="text-align: center;">(D)</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">0.0</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">5.77</td>
<td style="text-align: center;">24.6</td>
<td style="text-align: center;"></td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">0.2</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">4.95</td>
<td style="text-align: center;">25.5</td>
<td style="text-align: center;"></td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">0.0</td>
<td style="text-align: center;"></td>
<td style="text-align: center;">4.67</td>
<td style="text-align: center;">25.3</td>
<td style="text-align: center;"></td>
</tr>
<tr>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">0.2</td>
<td style="text-align: center;"></td>
<td style="text-align: center;">5.47</td>
<td style="text-align: center;">25.7</td>
<td style="text-align: center;"></td>
</tr>
<tr>
<td style="text-align: center;">(E)</td>
<td style="text-align: center;">positional embedding instead of
sinusoids</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">4.92</td>
<td style="text-align: center;">25.7</td>
<td style="text-align: center;"></td>
</tr>
<tr>
<td style="text-align: center;">big</td>
<td style="text-align: center;">6</td>
<td style="text-align: center;">1024</td>
<td style="text-align: center;">4096</td>
<td style="text-align: center;">16</td>
<td style="text-align: center;"></td>
<td style="text-align: center;"></td>
<td style="text-align: center;">0.3</td>
<td style="text-align: center;"></td>
<td style="text-align: center;">300K</td>
<td style="text-align: center;">4.33</td>
<td style="text-align: center;">26.4</td>
<td style="text-align: center;">213</td>
</tr>
</tbody>
</table>

development set, newstest2013. We used beam search as described in the
previous section, but no checkpoint averaging. We present these results
in Table 3.

In Table 3 rows (A), we vary the number of attention heads and the
attention key and value dimensions, keeping the amount of computation
constant, as described in Section 3.2.2. While single-head attention is
0.9 BLEU worse than the best setting, quality also drops off with too
many heads.

In Table 3 rows (B), we observe that reducing the attention key size
*d*<sub>*k*</sub> hurts model quality. This suggests that determining
compatibility is not easy and that a more sophisticated compatibility
function than dot product may be beneficial. We further observe in rows
(C) and (D) that, as expected, bigger models are better, and dropout is
very helpful in avoiding over-fitting. In row (E) we replace our
sinusoidal positional encoding with learned positional embeddings \[9\],
and observe nearly identical results to the base model.

# 6.3 English Constituency Parsing

To evaluate if the Transformer can generalize to other tasks we
performed experiments on English constituency parsing. This task
presents specific challenges: the output is subject to strong structural
constraints and is significantly longer than the input. Furthermore, RNN
sequence-to-sequence models have not been able to attain
state-of-the-art results in small-data regimes \[37\].

We trained a 4-layer transformer with *d*<sub>model </sub> = 1024 on the
Wall Street Journal (WSJ) portion of the Penn Treebank \[25\], about 40K
training sentences. We also trained it in a semi-supervised setting,
using the larger high-confidence and BerkleyParser corpora from with
approximately 17M sentences \[37\]. We used a vocabulary of 16 K tokens
for the WSJ only setting and a vocabulary of 32 K tokens for the
semi-supervised setting. We performed only a small number of experiments
to select the dropout, both attention and residual (section 5.4),
learning rates and beam size on the Section 22 development set, all
other parameters remained unchanged from the English-to-German base
translation model. During inference, we
