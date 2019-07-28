---
title: "Context in nlp"
date: 2019-07-19
#pubtype: "Talk,Article,Etc"
featured: true
description: "A history of 'context' in nlp"
tags: ["NLP", "Machine Learning"]
image: ""
#link: "URL linked from project details page"
#fact: "Interesting little tidbit shown below image on summary and detail page"
weight: 500
sitemap:
  priority : 0.8
---


One of the most important problems in Natural Langugage Understanding (NLU) is context. Not all words are different to each other in the same way, which is why models based on word frequency can perform poorly. Word embeddings such as [GLOVE](http://www.aclweb.org/anthology/D14-1162) are often used in order to represent the similarities and differences words or tokens. Words that are similar in meaning are represented closer together in the embedding space. Some words though have very different meanings in different contexts. For example, "bank" may mean the "bank" of a river (noun), a savings "bank" (noun), to "bank" money (verb), or a "bank" of computers (noun). This is difficult to represent and resolve the ambiguity with embeddings.

### CNN
The context of a word is not just determined by what words are around it but also their order and the syntax of the string. In NLU tasks such as text classification input documents are often encoded in to some representation of the whole document. This can be done using Convolutional Neural Networks [(CNN)](http://arxiv.org/abs/1408.5882) which allows the context of otherwise ambiguous words to be represented in the encoding.

### LSTM
[Sequence-to-sequence](http://arxiv.org/abs/1409.3215) models are often used for abstractive text summarisation tasks. The architecture is made up of an encoder which produces a representation of the input sequence and a decoder that produces an output sequence using this encoding as context. Recurrent Neural Networks (RNN) such as LSTM's are used for the encoders and decoders. This means the decoders input context is fixed at each step of the output generation.

### Attention
[Attention](https://arxiv.org/abs/1409.0473) is a mechanism for generating a unique context vector for each step of the decoder sequence. This means that the encoder does not need to encode all information from the input into a single fixed vector. The context vector for each step of the decoder is a weighted sum of the hidden states of the input sequence. These weights are calculated with a _score_ function taking the hidden states of the encoder and decoder as input. This score represents the how much attention should be given to each token of the input sequence at the current step of the output sequence. Attention allows for a dynamic context representing information over long sequences.

### Transformer
The [Transformer](http://arxiv.org/abs/1706.03762) model removes the need for an RNN by using only _self-attention_. Each layer of both the encoder and decoder transforms the embedding of each token of the sequence in to a new embedding which better represents the token in its context.
