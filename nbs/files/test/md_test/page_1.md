# Attention Is All You Need  ... page 1

Ashish Vaswani*<br>Google Brain<br>avaswani@google.com<br>Llion Jones*<br>Google Research<br>llion@google.com

Noam Shazeer*<br>Google Brain<br>noam@google.com<br>Niki Parmar*<br>Google Research<br>nikip@google.com<br>Jakob Uszkoreit*<br>Google Research<br>usz@google.com<br>Aidan N. Gomez* ${ }^{\dagger}$<br>University of Toronto<br>aidan@cs.toronto.edu

Łukasz Kaiser*<br>Google Brain<br>lukaszkaiser@google.com

## Illia Polosukhin* ${ }^{\ddagger}$<br>illia.polosukhin@gmail.com ... page 1


## Abstract ... page 1

The dominant sequence transduction models are based on complex recurrent or convolutional neural networks that include an encoder and a decoder. The best performing models also connect the encoder and decoder through an attention mechanism. We propose a new simple network architecture, the Transformer, based solely on attention mechanisms, dispensing with recurrence and convolutions entirely. Experiments on two machine translation tasks show these models to be superior in quality while being more parallelizable and requiring significantly less time to train. Our model achieves 28.4 BLEU on the WMT 2014 English-to-German translation task, improving over the existing best results, including ensembles, by over 2 BLEU. On the WMT 2014 English-to-French translation task, our model establishes a new single-model state-of-the-art BLEU score of 41.8 after training for 3.5 days on eight GPUs, a small fraction of the training costs of the best models from the literature. We show that the Transformer generalizes well to other tasks by applying it successfully to English constituency parsing both with large and limited training data.


[^0]
[^0]:    *Equal contribution. Listing order is random. Jakob proposed replacing RNNs with self-attention and started the effort to evaluate this idea. Ashish, with Illia, designed and implemented the first Transformer models and has been crucially involved in every aspect of this work. Noam proposed scaled dot-product attention, multi-head attention and the parameter-free position representation and became the other person involved in nearly every detail. Niki designed, implemented, tuned and evaluated countless model variants in our original codebase and tensor2tensor. Llion also experimented with novel model variants, was responsible for our initial codebase, and efficient inference and visualizations. Lukasz and Aidan spent countless long days designing various parts of and implementing tensor2tensor, replacing our earlier codebase, greatly improving results and massively accelerating our research.
    ${ }^{\dagger}$ Work performed while at Google Brain.
    ${ }^{\ddagger}$ Work performed while at Google Research.