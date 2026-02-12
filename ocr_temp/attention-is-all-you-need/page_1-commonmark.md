

# Attention Is All You Need … page 1

Ashish Vaswani\*

Google Brain

avaswani@google.com

Noam Shazeer\*

Google Brain

noam@google.com

Niki Parmar\*

Google Research

nikip@google.com

Jakob Uszkoreit\*

Google Research

usz@google.com

Llion Jones\*

Google Research

llion@google.com

Aidan N. Gomez\*†

University of Toronto

aidan@cs.toronto.edu

Łukasz Kaiser\*

Google Brain

lukaszkaiser@google.com

Illia Polosukhin\*‡

illia.polosukhin@gmail.com

## Abstract … page 1

The dominant sequence transduction models are based on complex recurrent
or convolutional neural networks that include an encoder and a decoder.
The best performing models also connect the encoder and decoder through
an attention mechanism. We propose a new simple network architecture,
the Transformer, based solely on attention mechanisms, dispensing with
recurrence and convolutions entirely. Experiments on two machine
translation tasks show these models to be superior in quality while
being more parallelizable and requiring significantly less time to
train. Our model achieves 28.4 BLEU on the WMT 2014 English-to-German
translation task, improving over the existing best results, including
ensembles, by over 2 BLEU. On the WMT 2014 English-to-French translation
task, our model establishes a new single-model state-of-the-art BLEU
score of 41.8 after training for 3.5 days on eight GPUs, a small
fraction of the training costs of the best models from the literature.
We show that the Transformer generalizes well to other tasks by applying
it successfully to English constituency parsing both with large and
limited training data.

31st Conference on Neural Information Processing Systems (NIPS 2017),
Long Beach, CA, USA.
