![img-0.jpeg](img-0.jpeg)
AI-generated image description:
___
This is an architectural diagram of a Transformer model, showing both the encoder (left) and decoder (right) components. 

The encoder (left side) processes inputs through:
- Input Embedding layer at the bottom
- Positional Encoding (added via ⊕ symbol)
- N× stacked blocks, each containing:
  - Masked Multi-Head Attention (orange)
  - Add & Norm layer (yellow)
  - Feed Forward layer (blue)
  - Another Add & Norm layer (yellow)
- Residual connections shown as curved arrows around each sub-layer

The decoder (right side) processes outputs (shifted right) through:
- Output Embedding layer
- Positional Encoding (added via ⊕ symbol)
- N× stacked blocks, each containing:
  - Masked Multi-Head Attention (orange)
  - Add & Norm layer (yellow)
  - Multi-Head Attention that receives input from encoder (orange)
  - Add & Norm layer (yellow)
  - Feed Forward layer (blue)
  - Add & Norm layer (yellow)
- Residual connections around each sub-layer

The decoder output flows through:
- Linear layer (gray)
- Softmax layer (green)
- Final Output Probabilities

This diagram illustrates the classic "Attention is All You Need" Transformer architecture, showing the parallel processing structure, residual connections, and the flow of information from inputs to output probabilities.
___

Figure 1: The Transformer - model architecture.

The Transformer follows this overall architecture using stacked self-attention and point-wise, fully connected layers for both the encoder and decoder, shown in the left and right halves of Figure 1, respectively.

### 3.1 Encoder and Decoder Stacks  ... page 3

Encoder: The encoder is composed of a stack of $N=6$ identical layers. Each layer has two sub-layers. The first is a multi-head self-attention mechanism, and the second is a simple, positionwise fully connected feed-forward network. We employ a residual connection [11] around each of the two sub-layers, followed by layer normalization [1]. That is, the output of each sub-layer is $\operatorname{LayerNorm}(x+\operatorname{Sublayer}(x))$, where $\operatorname{Sublayer}(x)$ is the function implemented by the sub-layer itself. To facilitate these residual connections, all sub-layers in the model, as well as the embedding layers, produce outputs of dimension $d_{\text {model }}=512$.

Decoder: The decoder is also composed of a stack of $N=6$ identical layers. In addition to the two sub-layers in each encoder layer, the decoder inserts a third sub-layer, which performs multi-head attention over the output of the encoder stack. Similar to the encoder, we employ residual connections around each of the sub-layers, followed by layer normalization. We also modify the self-attention sub-layer in the decoder stack to prevent positions from attending to subsequent positions. This masking, combined with fact that the output embeddings are offset by one position, ensures that the predictions for position $i$ can depend only on the known outputs at positions less than $i$.

### 3.2 Attention ... page 3

An attention function can be described as mapping a query and a set of key-value pairs to an output, where the query, keys, values, and output are all vectors. The output is computed as a weighted sum