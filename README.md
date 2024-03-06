# GLU Variants
Author: Zheling Zhang

Email: zheling.zhang@vanderbilt.edu

## Introdcution
Transformers have become a dominant architecture in the field of natural language processing. However, their capacity for modeling complex dependencies can be limited by the standard feed-forward networks used within. The introduction of GLU variants into the feed-forward layers offers a novel approach to enhancing the model's representational power.

## Paper Overview
The core problem addressed in this paper is the quest for architectural improvements that can lead to better model performance without significatly increasing computational cost or complexity. The approach taken by the author involves integrating GLUs (Gated Linear Units) variants into the transformer architechture. 

## Overview of GLUs and Variants

<details>
  <summary>What are GLUs (Gated Linear Units)?</summary>
  
Gated Linear Units (GLUs) are elements within neural networks designed to better manage how information flows through the model. At their core, GLUs perform a simple yet effective operation: they take two linear projections of the input data. Before combining these projections, one undergoes a transformation by a sigmoid function, effectively turning it into a gate. This gate then determines how much of the other linear projection’s information should be allowed to pass through. By doing so, GLUs give the network the ability to selectively focus on more relevant pieces of information while disregarding the rest, which can significantly enhance the learning efficiency of the model.

  </details><br>

The GLU Variants utilize the similar machanism to control the flow of information by using different non-linear (or even linear) functions in place of sigmoid.

**GLU**:
$$\text{GLU}(x, W, V, b, c) = \sigma(xW + b) \otimes (xV + c)$$

**Bilinear**:
$$\text{Bilinear}(x, W, V, b, c) = (xW + b) \otimes (xV + c)$$

**ReGLU**:
$$\text{ReGLU}(x, W, V, b, c) = \max(0, xW + b) \otimes (xV + c)$$

**GEGLU**:
$$\text{GEGLU}(x, W, V, b, c) = \text{GELU}(xW + b) \otimes (xV + c)$$

**SwiGLU**:
$$\text{SwiGLU}(x, W, V, b, c, \beta) = \text{Swish}_\beta(xW + b) \otimes (xV + c)$$

The additional variations on the transformer feed-forward network layer which use GLU or one of its variants in place of the first linear transformation and the activation function. The bias term is ommited in this paper.

**FFN_GLU**:
$$\text{FFNGLU}(x, W, V, W_2) = (\sigma(xW) \otimes xV)W_2$$

**FFN_Bilinear**:
$$\text{FFNBilinear}(x, W, V, W_2) = (xW \otimes xV)W_2$$

**FFN_ReGLU**:
$$\text{FFNReGLU}(x, W, V, W_2) = (\max(0, xW) \otimes xV)W_2$$

**FFN_GEGLU**:
$$\text{FFNGEGLU}(x, W, V, W_2) = (\text{GELU}(xW) \otimes xV)W_2$$

**FFN_SwiGLU**:
$$\text{FFNSwiGLU}(x, W, V, W_2) = (\text{Swish}_1(xW) \otimes xV)W_2$$

## Perplexity Result
![alt text](https://github.com/Zoliverling/Transformer_Paper_Presentation/blob/main/images/image.png)

## Fine-tuning

In the fine-tuning phase, fully-trained models are refined on a carefully curated dataset amalgamating the Stanford Question-Answering Dataset (SQuAD) with tasks from the GLUE and SuperGLUE benchmarks to enhance their performance across a spectrum of natural language understanding (NLU) challenges. This fine-tuning process, executed over 131,072 steps at a learning rate of 10^-3 and handling input sequences up to approximately 65,536 tokens in length, employs a dropout rate of 0.1 on various model components as a regularization strategy, following protocols established by Raffel et al., 2019. Notably, the embedding matrices remain unchanged during this phase, focusing the model's learning on the adjustment of higher-layer weights to the specificities of the task, thereby optimizing the model's adaptability and performance on complex NLU tasks.

![alt text](https://github.com/Zoliverling/Transformer_Paper_Presentation/blob/main/images/image-1.png)

![alt text](https://github.com/Zoliverling/Transformer_Paper_Presentation/blob/main/images/image-2.png)

![alt text](https://github.com/Zoliverling/Transformer_Paper_Presentation/blob/main/images/image-3.png)

## Pratical Benefits

The conclusion statement from the paper suggests that the GLU variants, when integrated into Transformer models, yield improved performance on various language understanding tasks. The practical applications of these findings are quite extensive, particularly in the field of Natural Language Processing (NLP), which involves teaching machines to understand, interpret, and generate human language. Here are some practical usages of such improvements:

**Sentiment Analysis**

Businesses and organizations can utilize these models to better gauge public sentiment from social media posts, reviews, and customer feedback, allowing for more responsive and targeted services.

**Question Answering Systems** 

Improved language models can lead to more accurate and relevant answers in AI-based customer service bots, virtual assistants, and information retrieval systems.

**Speech Recognition**

Incorporating these models into speech-to-text applications can result in more accurate transcription, which is beneficial for accessibility technology, legal transcriptions, and more.

## Citation

Shazeer, N. (2020b, February 12). GLU variants improve transformer. arXiv.org. https://arxiv.org/abs/2002.05202

## Useful links
Annotated Paper Implemenatation Notebook: https://nn.labml.ai/transformers/glu_variants/simple.html

Original code base: https://arxiv.org/pdf/1910.10683.pdf




