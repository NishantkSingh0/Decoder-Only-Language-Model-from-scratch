# Overview
This repository contains a custom-built language model trained on 400,000+ carefully curated paragraphs. The model architecture is based on the Transformer decoder, incorporating multiple layers of attention mechanisms, pointwise feed-forward networks, and advanced tokenization techniques such as Byte Pair Encoding (BPE). The model was designed to generate 100 token paragraphs, with an emphasis on handling large vocabularies and ensuring optimal training using a warmup learning rate schedule. Below, we delve into the details of the model architecture, dataset preparation, and the training process.

# About the Model
## Model Architecture
The model is built using a custom decoder-based Transformer architecture, consisting of multiple layers of attention, feed-forward networks, and a comprehensive positional encoding scheme. Below are the key components of the architecture:   
  
* #### Padding and Tokenization:   
The paragraphs are tokenized using SentencePiece with Byte Pair Encoding (BPE). This approach efficiently compresses the vocabulary size while preserving word semantics. Each paragraph is tokenized into a sequence of integers, padded to a fixed length of 300 tokens.  
  
* #### Embedding: 
The model utilizes an embedding layer that maps each token to a dense vector of dimension 20 (d_model=20). The embedding layer is followed by a positional encoding scheme that helps the model capture the sequential relationships between tokens.  
  
* #### Attention Mechanism: 
The model employs multi-head attention with 2 heads (num_heads=2), where each head operates on a depth of 10 (d_model/num_heads). This mechanism allows the model to focus on different parts of the input sequence simultaneously.  
  
* #### Pointwise Feed-Forward Network (PFFN):  
The PFFN consists of two dense layers, where the first layer expands the dimensionality to 256 (dff=256), followed by a ReLU activation, and the second layer projects it back to 20 (d_model=20). This allows the model to learn complex transformations of the input data.  
  
* #### Decoder Layers:  
The decoder has 2 layers (numLayers=2), each containing a multi-head attention mechanism, followed by a pointwise feed-forward network. The output of each layer is normalized and combined with the input to the layer using residual connections.    
  
* #### Regularization:  
The model employs dropout with a rate of 0.3 to prevent overfitting.  

# About the Dataset
### Dataset Preparation
The dataset consists of 50,000 paragraphs, carefully filtered to remove irrelevant or noisy content. The paragraphs were standardized to a fixed sequence length of 300 tokens, ensuring consistency across the training data. This involved the following steps:

__* Cleaning:__ Removing unnecessary symbols, special characters, and noise.  
__* Tokenization:__ Each paragraph was tokenized using SentencePiece with BPE, producing a sequence of integer tokens.  
__* Padding and Truncation:__ Paragraphs shorter than 300 tokens were padded with zeros, while longer paragraphs were truncated to exactly 300 tokens.  
#### The dataset is balanced and highly relevant to the language modeling task, making it ideal for training robust language models.  
### Sample:
The 4K PS4 might be officially announced soon. The existence of the upgraded version of Sony\'s console was previously reported by Kotaku, and today The Wall Street Journal reports that the device is expected to be officially unveiled before the October launch of PlayStation VR. As with the previous report, the WSJ says that the beefed-up version of the console will support 4K graphics as well as provide extra power for the PSVR virtual reality add-on. The new PS4 is expected to include both an upgraded processor and GPU, and the WSJ says that it\'s likely that both versions of the console will share an identical software catalog. There are no details on when it might launch or how much it will cost.\n\nThis type of mid-cycle upgrade for a console isn\'t exactly common, but Microsoft has hinted that it could do something similar for the Xbox One, with Xbox chief Phil Spencer predicting that consoles could eventually resemble PCs in this regard. "When you look at the console space, I believe we will see more hardware innovation in the console space than we\'ve ever seen," he explained. While both Sony and Microsoft could potentially release new, slightly upgraded versions of their consoles, competitor Nintendo is going in a more traditional direction with a brand new device codenamed NX, that will replace the Wii U and is expected to be unveiled some time this year.\n\nHands-on with the PlayStation VR ...

# Byte Pair Encoding (BPE)
The model utilizes Byte Pair Encoding (BPE) for tokenization, a subword tokenization technique that helps in handling rare words and reducing the vocabulary size. BPE works by iteratively merging the most frequent pairs of bytes, allowing the model to represent any word as a sequence of subwords or tokens. This is particularly beneficial for languages with a large vocabulary or a significant amount of inflection.

# Warmup Learning Rate Schedule
To ensure stable and effective training, the model employs a custom warmup learning rate schedule. The learning rate starts low and gradually increases during the initial steps (warmup phase), followed by a gradual decrease. This helps prevent the model from converging to a suboptimal solution too quickly and improves generalization.

![Screenshot (129)](https://github.com/user-attachments/assets/33e66734-801f-4da1-963a-0bdd01abc7e3)


The learning rate is calculated using a cosine decay function after the warmup phase, ensuring a smooth transition to lower learning rates as training progresses.


# Achievements
__● Custom Transformer Decoder:__ Designed and implemented a Transformer-based language model with a focus on understanding and generating text.   
__● Advanced Tokenization:__ Integrated SentencePiece with BPE for efficient vocabulary management and improved handling of rare words.   
__● Robust Training:__ Achieved stable and effective training using a warmup learning rate schedule, enhancing the model's generalization capabilities.   
__● Scalable Dataset:__ Managed and processed a large dataset of 50,000 paragraphs, ensuring high-quality input for the language model.   
