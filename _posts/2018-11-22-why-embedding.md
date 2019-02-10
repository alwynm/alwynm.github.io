---
layout: post
title: Why embedding?
categories: Research
use_math: true
ready : true
---

As artificial neural networks(NN) only take numbers as input, we should somehow convert our data into numerical format. Images are represented as a matrix where each pixel value corresponds to an intensity value which makes them easier to feed into a network directly. Grayscale images are 2D matrices and RGB images are 3D matrices.

But if your data is text, in particular, sentences which are not numerical make it incompatible to use it directly on the network. Thus, we need to convert these text into some kind of numerical values.

# How would you feed a word to an NN?

## One-hot vectors

Let’s say your vocabulary has 10000 words, and you have defined an ordering over these words - “a”, “the”, “they”, “are”, “have”, etc. Now, you can represent the first word in the ordering 

<center>
$\begin{bmatrix} “a” \end{bmatrix}$
as $\begin{bmatrix} 1 & 0 & 0 & 0 &... \end{bmatrix}$, 
</center>

which is a vector of size 10000 with all zeros except at position 1. Similarly, the second, third, …, words can be defined as 

<center>
$\begin{bmatrix} 0 & 1 & 0 & 0 & ... \end{bmatrix}$,
$\begin{bmatrix} 0 & 0 & 1 & 0 & ... \end{bmatrix}$.
</center> 

So, the i<sup>th</sup> word will be a vector of size 10000 with all zeros except a 1 at the i<sup>th</sup> position.

Now, we have a way to feed the words into the NN. But the notion of distance that we had in case of images is not present. All words are equidistant from all other words. Secondly, the dimension of the input is huge. Your vocabulary size could easily go to 100,000 or more.

## Embedding

Instead of having a sparse vector for each word, you can have a dense vector for each word, that is, multiple elements of the vector are nonzero and each element of the vector can take continuous values. This immediately reduces the size of the vector. You can have an infinite number of unique vectors of size, say 10, where each element can take any arbitrary value \[as opposed to one-hot vectors where each element could take only values 0 or 1\]. 

So, for instance, 

$\begin{bmatrix} “a” \end{bmatrix}$ could be represented as 
<center>
$\begin{bmatrix} 0.13 & 0.46 & 0.85 & 0.96 & 0.66 & 0.12 & 0.01 & 0.38 & 0.76 & 0.95 \end{bmatrix}$, 
</center>
 
$\begin{bmatrix} “the” \end{bmatrix}$ could be represented as 
<center>
$\begin{bmatrix} 0.73 & 0.45 & 0.25 & 0.91 & 0.06 & 0.16 & 0.11 & 0.36 & 0.76 & 0.98 \end{bmatrix}$, 
</center>
and so on. 
 
The size of the vectors is a hyperparameter, set using cross-validation. So, how do you feed these dense vector representations of words into the network? The answer is an embedding layer - you will have an embedding layer that is essentially a matrix of size 10000 x 10 \[or more generally,  vocab_size×dense_vector_size\]. For every word, you have an index in the vocabulary, like "a" -> 0, "the" -> 1, etc., and you simply look up the corresponding row in the embedding matrix to get its 10-dimensional representation as the output. Another advantage of embedding is that, its trainable. For instance, you can initialize the embedding layer randomly, and train it with the other layers. You could also fix or fine tune embedding while using pretrained word vectors for the words.
