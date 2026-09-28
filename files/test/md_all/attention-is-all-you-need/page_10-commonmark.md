

Table 4: The Transformer generalizes well to English constituency
parsing (Results are on Section 23 of WSJ)

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr>
<th>Parser</th>
<th>Training</th>
<th>WSJ 23 F1</th>
</tr>
</thead>
<tbody>
<tr>
<td>Vinyals &amp; Kaiser el al. (2014) [37]</td>
<td>WSJ only, discriminative</td>
<td>88.3</td>
</tr>
<tr>
<td>Petrov et al. (2006) [29]</td>
<td>WSJ only, discriminative</td>
<td>90.4</td>
</tr>
<tr>
<td>Zhu et al. (2013) [40]</td>
<td>WSJ only, discriminative</td>
<td>90.4</td>
</tr>
<tr>
<td>Dyer et al. (2016) [8]</td>
<td>WSJ only, discriminative</td>
<td>91.7</td>
</tr>
<tr>
<td>Transformer (4 layers)</td>
<td>WSJ only, discriminative</td>
<td>91.3</td>
</tr>
<tr>
<td>Zhu et al. (2013) [40]</td>
<td>semi-supervised</td>
<td>91.3</td>
</tr>
<tr>
<td>Huang &amp; Harper (2009) [14]</td>
<td>semi-supervised</td>
<td>91.3</td>
</tr>
<tr>
<td>McClosky et al. (2006) [26]</td>
<td>semi-supervised</td>
<td>92.1</td>
</tr>
<tr>
<td>Vinyals &amp; Kaiser el al. (2014) [37]</td>
<td>semi-supervised</td>
<td>92.1</td>
</tr>
<tr>
<td>Transformer (4 layers)</td>
<td>semi-supervised</td>
<td>92.7</td>
</tr>
<tr>
<td>Luong et al. (2015) [23]</td>
<td>multi-task</td>
<td>93.0</td>
</tr>
<tr>
<td>Dyer et al. (2016) [8]</td>
<td>generative</td>
<td>93.3</td>
</tr>
</tbody>
</table>

increased the maximum output length to input length +300 . We used a
beam size of 21 and *α* = 0.3 for both WSJ only and the semi-supervised
setting.

Our results in Table 4 show that despite the lack of task-specific
tuning our model performs surprisingly well, yielding better results
than all previously reported models with the exception of the Recurrent
Neural Network Grammar \[8\].

In contrast to RNN sequence-to-sequence models \[37\], the Transformer
outperforms the Berkeley-Parser \[29\] even when training only on the
WSJ training set of 40K sentences.

# 7 Conclusion

In this work, we presented the Transformer, the first sequence
transduction model based entirely on attention, replacing the recurrent
layers most commonly used in encoder-decoder architectures with
multi-headed self-attention.

For translation tasks, the Transformer can be trained significantly
faster than architectures based on recurrent or convolutional layers. On
both WMT 2014 English-to-German and WMT 2014 English-to-French
translation tasks, we achieve a new state of the art. In the former task
our best model outperforms even all previously reported ensembles.

We are excited about the future of attention-based models and plan to
apply them to other tasks. We plan to extend the Transformer to problems
involving input and output modalities other than text and to investigate
local, restricted attention mechanisms to efficiently handle large
inputs and outputs such as images, audio and video. Making generation
less sequential is another research goals of ours.

The code we used to train and evaluate our models is available at
https://github.com/tensorflow/tensor2tensor.

Acknowledgements We are grateful to Nal Kalchbrenner and Stephan Gouws
for their fruitful comments, corrections and inspiration.

# References

\[1\] Jimmy Lei Ba, Jamie Ryan Kiros, and Geoffrey E Hinton. Layer
normalization. arXiv preprint arXiv:1607.06450, 2016. \[2\] Dzmitry
Bahdanau, Kyunghyun Cho, and Yoshua Bengio. Neural machine translation
by jointly learning to align and translate. CoRR, abs/1409.0473, 2014.
\[3\] Denny Britz, Anna Goldie, Minh-Thang Luong, and Quoc V. Le.
Massive exploration of neural machine translation architectures. CoRR,
abs/1703.03906, 2017. \[4\] Jianpeng Cheng, Li Dong, and Mirella Lapata.
Long short-term memory-networks for machine reading. arXiv preprint
arXiv:1601.06733, 2016.
