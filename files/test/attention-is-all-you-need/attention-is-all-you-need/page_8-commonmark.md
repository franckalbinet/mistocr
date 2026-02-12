

Table 2: The Transformer achieves better BLEU scores than previous
state-of-the-art models on the English-to-German and English-to-French
newstest2014 tests at a fraction of the training cost.

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr>
<th>Model</th>
<th>BLEU</th>
<th></th>
<th>Training Cost (FLOPs)</th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td></td>
<td>EN-DE</td>
<td>EN-FR</td>
<td>EN-DE</td>
<td>EN-FR</td>
</tr>
<tr>
<td>ByteNet [18]</td>
<td>23.75</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>Deep-Att + PosUnk [39]</td>
<td></td>
<td>39.2</td>
<td></td>
<td><span class="math inline">1.0 ⋅ 10<sup>20</sup></span></td>
</tr>
<tr>
<td>GNMT + RL [38]</td>
<td>24.6</td>
<td>39.92</td>
<td><span class="math inline">2.3 ⋅ 10<sup>19</sup></span></td>
<td><span class="math inline">1.4 ⋅ 10<sup>20</sup></span></td>
</tr>
<tr>
<td>ConvS2S [9]</td>
<td>25.16</td>
<td>40.46</td>
<td><span class="math inline">9.6 ⋅ 10<sup>18</sup></span></td>
<td><span class="math inline">1.5 ⋅ 10<sup>20</sup></span></td>
</tr>
<tr>
<td>MoE [32]</td>
<td>26.03</td>
<td>40.56</td>
<td><span class="math inline">2.0 ⋅ 10<sup>19</sup></span></td>
<td><span class="math inline">1.2 ⋅ 10<sup>20</sup></span></td>
</tr>
<tr>
<td>Deep-Att + PosUnk Ensemble [39]</td>
<td></td>
<td>40.4</td>
<td></td>
<td><span class="math inline">8.0 ⋅ 10<sup>20</sup></span></td>
</tr>
<tr>
<td>GNMT + RL Ensemble [38]</td>
<td>26.30</td>
<td>41.16</td>
<td><span class="math inline">1.8 ⋅ 10<sup>20</sup></span></td>
<td><span class="math inline">1.1 ⋅ 10<sup>21</sup></span></td>
</tr>
<tr>
<td>ConvS2S Ensemble [9]</td>
<td>26.36</td>
<td>41.29</td>
<td><span class="math inline">7.7 ⋅ 10<sup>19</sup></span></td>
<td><span class="math inline">1.2 ⋅ 10<sup>21</sup></span></td>
</tr>
<tr>
<td>Transformer (base model)</td>
<td>27.3</td>
<td>38.1</td>
<td><span
class="math inline"><strong>3</strong><strong>.</strong><strong>3</strong> <strong>⋅</strong> <strong>1</strong><strong>0</strong><sup><strong>1</strong><strong>8</strong></sup></span></td>
<td></td>
</tr>
<tr>
<td>Transformer (big)</td>
<td>28.4</td>
<td>41.8</td>
<td><span class="math inline">2.3 ⋅ 10<sup>19</sup></span></td>
<td></td>
</tr>
</tbody>
</table>

Residual Dropout We apply dropout \[33\] to the output of each
sub-layer, before it is added to the sub-layer input and normalized. In
addition, we apply dropout to the sums of the embeddings and the
positional encodings in both the encoder and decoder stacks. For the
base model, we use a rate of *P*<sub>drop </sub> = 0.1.

Label Smoothing During training, we employed label smoothing of value
*ϵ*<sub>*l**s*</sub> = 0.1 \[36\]. This hurts perplexity, as the model
learns to be more unsure, but improves accuracy and BLEU score.

# 6 Results

### 6.1 Machine Translation

On the WMT 2014 English-to-German translation task, the big transformer
model (Transformer (big) in Table 2) outperforms the best previously
reported models (including ensembles) by more than 2.0 BLEU,
establishing a new state-of-the-art BLEU score of 28.4. The
configuration of this model is listed in the bottom line of Table 3.
Training took 3.5 days on 8 P100 GPUs. Even our base model surpasses all
previously published models and ensembles, at a fraction of the training
cost of any of the competitive models.

On the WMT 2014 English-to-French translation task, our big model
achieves a BLEU score of 41.0, outperforming all of the previously
published single models, at less than 1/4 the training cost of the
previous state-of-the-art model. The Transformer (big) model trained for
English-to-French used dropout rate *P*<sub>drop </sub> = 0.1, instead
of 0.3 . For the base models, we used a single model obtained by
averaging the last 5 checkpoints, which were written at 10-minute
intervals. For the big models, we averaged the last 20 checkpoints. We
used beam search with a beam size of 4 and length penalty *α* = 0.6
\[38\]. These hyperparameters were chosen after experimentation on the
development set. We set the maximum output length during inference to
input length +50 , but terminate early when possible \[38\].

Table 2 summarizes our results and compares our translation quality and
training costs to other model architectures from the literature. We
estimate the number of floating point operations used to train a model
by multiplying the training time, the number of GPUs used, and an
estimate of the sustained single-precision floating-point capacity of
each GPU <sup>5</sup>.

### 6.2 Model Variations

To evaluate the importance of different components of the Transformer,
we varied our base model in different ways, measuring the change in
performance on English-to-German translation on the

\[^0\] \[^0\]: <sup>5</sup> We used values of 2.8, 3.7, 6.0 and 9.5
TFLOPS for K80, K40, M40 and P100, respectively.
