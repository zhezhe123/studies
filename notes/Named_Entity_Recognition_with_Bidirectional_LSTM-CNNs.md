# Named Entity Recognition with Bidirectional LSTM-CNNs
- Chiu and Nichols
[[paper]](https://www.aclweb.org/anthology/Q/Q16/Q16-1026.pdf)
- ACL 2016

* Motivation: NER usually requires loads of feature engineering
* Contribution: 
  1. NER model that combines CNN + LSTM to learn both char- and word- level features and does not require external features
  2. a novel method of encoding partial lexicon matches in NNs
* Method: 
* Results:
  1. Using only tokenized text and publicly available word embeddings, our model performs similarly to state-of-the-art models
  2. Using two lexicons constructed from publicly available sources, our model exceeds those with heavy feature engineering
* Future work: 

## Introduction
- Collobert's NER model implements NN and is free from feature engineering, but
  1. uses simple FFNN where context is restricted to a fixed sized window around each word and discards long-distance relationships
  2. solely depends on word embeddings and does not consider character level features that can help translate rare words
- RNNs and LSTMs are useful
  1. LSTMs help learn long-distance dependencies
  2. BiLSTM can take into account infinite amount of context on both sides of a word and eliminates problem of limited context
- CNNs are good for learning character-level information
  1. biLSTMs also considered, but performed not that much better than CNNs while costing more
  

## Related work
- Ling et al. Sequence to sequence learning with neural networks
[[paper]](http://papers.nips.cc/paper/5346-sequence-to-sequence-learning-with-neural-networks.pdf) 
[[notes]](https://github.com/mjc92/studies/blob/master/notes/Sequence_to_sequence_learning_with_neural_networks.md) 
: presents biLSTM for character level
- Cho et al. On the properties of neural machine translation: Encoder-Decoder approaches
[[paper]]() 
[[notes]]() 
: shows how performance drops when sentences become longer
- Graves et al. Generating Sequences With Recurrent Neural Networks
[[paper]](https://arxiv.org/pdf/1308.0850v5.pdf) 
[[notes]]() 
: used bidirectional RNN(BiRNN) in speech recognition


## Prerequisites
- Collobert et al. A Unified Architecture for Natural Language Processing: Deep Neural Networks with Multitask Learning
[[paper]](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.149.8551&rep=rep1&type=pdf) 
[[notes]]() 
: predecessor
  - lookup tables transform features such as words and chars into continuous vector representations, which are fed into a NN
- Graves et al. Speech Recognition with Deep Neural Networks
[[paper]](https://www.cs.toronto.edu/~fritz/absps/RNN13.pdf) 
[[notes]]() 
: applies BiLSTM in speech-recognition
- Santos et al. Boosting Named Entity Recognition with Neural Character Embeddings
[[paper]](https://arxiv.org/pdf/1505.05008v2.pdf) 
[[notes]]() 
: uses CNNs to extract character-level features for NER
- Labeau et al. Non-lexical neural architecture for fine-grained POS Tagging
[[paper]](http://www.aclweb.org/anthology/D15-1025) 
[[notes]]() 
: uses CNNs to extract character-level features for POS-tagging


## Methods

### Advanced NER model using biLSTM and CNN
- bidirectional LSTM for obtaining word-level information
  ![alt tag](https://github.com/mjc92/studies/blob/master/notes/images/biLSTM.JPG)  
- CNN for obtaining char-level features
  ![alt tag](https://github.com/mjc92/studies/blob/master/notes/images/char_level_CNN.JPG)  
- combined model
  - takes input in word-level
    1. word embeddings
    2. additional word features
    3. individual char- features extracted from CNN
  - applies biLSTM on output vector
  ![alt tag](https://github.com/mjc92/studies/blob/master/notes/images/biLSTM_CNN_for_NER.JPG)  
  
### Lexicons
- 


## Experiment Setting
- 

## Conclusion
- Contributions:
  1. New model: incorporates biLSTM and char-level CNN
    - partial matching lexicon algorithm
  2. Tackling problem: Improve previous NN models on NER and reduce feature engineering
  3. Performance: 
    - state-of-the-art in NER tasks with little feature engineering
    - can learn complex relationships from large amounts of data

- Future works:
  - improvement through more flexible application of existing lexicons
