---
layout: post
title: Inverse mapping
categories: Research
ready : true
---

Let's say, you have applied an affine transformation(translation and rotation and scaling) to an image. Applying these transformations will translate, rotate or rotate the image i.e., we have to move the pixel location of the source image according to the transformation to the target image. As discussed in the [last post](blog/research/forward-mapping), forward mapping has two disadvantages. We could use inverse mapping to solve these problems.

### What is inverse mapping?

Instead of transforming source grid and map from source to destination pixels, here we apply the inverse transformation on destination grid and map pixels from destination to source. We should use some interpolation method to find the approximate pixel values in the source as the inverse transformed grid will not fall exactly on a grid point on the source.

<p align="center">
  <img src="https://blogs.mathworks.com/images/steve/55/inverse_mapping.png" alt="inverse mapping">
</p>