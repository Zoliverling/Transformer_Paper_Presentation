# GLU Variants
Author: Zheling Zhang

Email: zheling.zhang@vanderbilt.edu

## Introdcution
Transformers have become a dominant architecture in the field of natural language processing. However, their capacity for modeling complex dependencies can be limited by the standard feed-forward networks used within. The introduction of GLU variants into the feed-forward layers offers a novel approach to enhancing the model's representational power.

## Paper Overview
The core problem addressed in this paper is the quest for architectural improvements that can lead to better model performance without significatly increasing computational cost or complexity. The approach taken by the author involves integrating GLUs (Gated Linear Units) variants into the transformer architechture. GLUs are a type of neural network component that controls the flow of information through the network by applying a gating mechanism to linear units. This gating mechanism allows the model to learn which parts of the information to pass through and which to block, potentially leading to more efficient learning process.

## Overview of GLUs and Variants

GLU:
$$\text{GLU}(x, W, V, b, c) = \sigma(xW + b) \otimes (xV + c)$$

Bilinear:
$$\text{Bilinear}(x, W, V, b, c) = (xW + b) \otimes (xV + c)$$

ReGLU:
$$\text{ReGLU}(x, W, V, b, c) = \max(0, xW + b) \otimes (xV + c)$$

GEGLU:
$$\text{GEGLU}(x, W, V, b, c) = \text{GELU}(xW + b) \otimes (xV + c)$$

SwiGLU:
$$\text{SwiGLU}(x, W, V, b, c, \beta) = \text{Swish}_\beta(xW + b) \otimes (xV + c)$$

The additional variations on the transformer feed-forward network layer which use GLU or one of its variants in place of the first linear transformation and the activation function. The bias term is ommited in this paper.

FFNGLU:
$$\text{FFNGLU}(x, W, V, W_2) = (\sigma(xW) \otimes xV)W_2$$

FFNBilinear:
$$\text{FFNBilinear}(x, W, V, W_2) = (xW \otimes xV)W_2$$

FFNReGLU:
$$\text{FFNReGLU}(x, W, V, W_2) = (\max(0, xW) \otimes xV)W_2$$

FFNGEGLU:
$$\text{FFNGEGLU}(x, W, V, W_2) = (\text{GELU}(xW) \otimes xV)W_2$$

FFNSwiGLU:
$$\text{FFNSwiGLU}(x, W, V, W_2) = (\text{Swish}_1(xW) \otimes xV)W_2$$




