# Overview
This repository contains a custom-built language model trained on over 400,000 carefully curated paragraphs from a diverse corpus. The model architecture is based on the Transformer decoder, integrating multiple layers of attention mechanisms, pointwise feed-forward networks, and advanced tokenization techniques such as Byte Pair Encoding (BPE). Designed to generate high-quality text with a focus on handling large vocabularies, the model employs a warmup learning rate schedule to ensure optimal training.

# Model Architecture
The model utilizes a custom Transformer decoder architecture, featuring:

![Screenshot (152)](https://github.com/user-attachments/assets/37f34175-9b13-4416-83d2-31cee95f2849)

* ### Tokenization and Padding:  
   Tokenization is handled by SentencePiece using BPE, optimizing vocabulary size while retaining semantic integrity. Each paragraph is tokenized into sequences of integers, padded to a fixed length of 100 tokens.

* ### Embedding: 
   Tokens are mapped to dense vectors of dimension 204 (d_model=204) via an embedding layer, followed by positional encoding to capture sequential token relationships.

* ### Attention Mechanism:  
   The model employs multi-head attention with 6 heads (num_heads=6), each processing a depth of 34 (d_model/num_heads). This allows the model to simultaneously focus on various parts of the input sequence.

* ### Pointwise Feed-Forward Network (PFFN): 
   The PFFN comprises two dense layers, with the first expanding dimensionality to 512 (dff=512) followed by ReLU activation, and the second projecting back to 204 (d_model=204), enabling complex input transformations.

* ### Decoder Layers:
   The architecture includes 8 decoder layers (num_layers=8), each incorporating multi-head attention and a PFFN, with residual connections and normalization enhancing model stability and performance.

* ### Regularization: 
   Dropout with a rate of 0.3 is used to prevent overfitting.

  ![Screenshot (147)](https://github.com/user-attachments/assets/c1f295f5-327b-49b5-8d61-cf6f67f85731)


# Dataset
The dataset comprises 400,000+ paragraphs, meticulously filtered using advanced NLP techniques to ensure quality and relevance. Key preparation steps include:

* ### Data Cleaning:  
   Removal of noise, special characters, and irrelevant content.

* ### Tokenization:  
   Tokenization was performed using SentencePiece with BPE, resulting in a balanced and manageable vocabulary.

* ### Padding and Truncation:  
   Sequences were standardized to 300 tokens, ensuring consistency in model input.

### Sample Data
Example Paragraph:  
"a third person would mean an opportunity to come together with her and with konnor to help keep them all alive. that is, if konnor didn't go completely over the deep end. she would have to take time to better assess his condition. even as she considered doing that, she knew she would have problems."

# Byte Pair Encoding (BPE)
The model employs BPE for tokenization, a technique that effectively handles rare words and optimizes vocabulary size (20,000) by merging frequent byte pairs, facilitating efficient subword representation.

# Warmup Learning Rate Schedule
To ensure robust training, the model employs a warmup learning rate schedule. The learning rate starts low, gradually increasing during the warmup phase, then decays smoothly using a cosine function, promoting stability and preventing premature convergence.
![Screenshot (129)](https://github.com/user-attachments/assets/41473cc8-8c5c-4361-b3ff-23fc740e6d1c)


# Achievements
* ### Custom Transformer Decoder:  
   Successfully designed and implemented a Transformer-based language model optimized for text generation.
  
* ### Advanced Tokenization:  
   Integrated SentencePiece with BPE, enhancing vocabulary management and handling of rare words.

* ### Robust and Effective Training:  
   Implemented a warmup learning rate schedule, resulting in improved generalization and stable training dynamics.

* ### High-Quality Dataset:  
   Processed and curated a large-scale dataset of 400,000+ paragraphs, providing a solid foundation for language modeling.
