# Overview
This repository contains a custom-built language model trained on 50,000 carefully curated paragraphs. The model architecture is based on the Transformer decoder, incorporating multiple layers of attention mechanisms, pointwise feed-forward networks, and advanced tokenization techniques such as Byte Pair Encoding (BPE). The model was designed to process sequences of 300 tokens, with an emphasis on handling large vocabularies and ensuring optimal training using a warmup learning rate schedule. Below, we delve into the details of the model architecture, dataset preparation, and the training process.

# About the Model
## Model Architecture
The model is built using a custom decoder-based Transformer architecture, consisting of multiple layers of attention, feed-forward networks, and a comprehensive positional encoding scheme. Below are the key components of the architecture:   
  
__Padding and Tokenization:__ The paragraphs are tokenized using SentencePiece with Byte Pair Encoding (BPE). This approach efficiently compresses the vocabulary size while preserving word semantics. Each paragraph is tokenized into a sequence of integers, padded to a fixed length of 300 tokens.  
  
__Embedding:__ The model utilizes an embedding layer that maps each token to a dense vector of dimension 20 (d_model=20). The embedding layer is followed by a positional encoding scheme that helps the model capture the sequential relationships between tokens.  
  
__Attention Mechanism:__ The model employs multi-head attention with 2 heads (num_heads=2), where each head operates on a depth of 10 (d_model/num_heads). This mechanism allows the model to focus on different parts of the input sequence simultaneously.  
  
__Pointwise Feed-Forward Network (PFFN):__ The PFFN consists of two dense layers, where the first layer expands the dimensionality to 256 (dff=256), followed by a ReLU activation, and the second layer projects it back to 20 (d_model=20). This allows the model to learn complex transformations of the input data.  
  
__Decoder Layers:__ The decoder has 2 layers (numLayers=2), each containing a multi-head attention mechanism, followed by a pointwise feed-forward network. The output of each layer is normalized and combined with the input to the layer using residual connections.    
  
__Regularization:__ The model employs dropout with a rate of 0.25 to prevent overfitting.  
