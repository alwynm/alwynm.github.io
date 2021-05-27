---
layout: post
title: Forward mapping
categories: Research
ready : true
---


Let's say, you have applied an affine transformation(translation and rotation and scaling) 
to an image. Applying these transformations will translate, rotate or rotate the image 
i.e., we have to move the pixel location of the source image according to the 
transformation to the target image. 

### What is forward mapping?

As we are manipulation the pixel location, we will construct a grid where each grid values 
is the location of pixels on the source image. Apply the transformation to this grid to 
get the desired tranformed grid. Use tranformed grid to look back at the source image 
and copy pixel values to that output pixel. This is commonly called forward mapping.

<p align="center">
  <img src="https://blogs.mathworks.com/images/steve/53/forward_mapping_a.png" alt="forward mapping">
</p>

### Why you shouldn't use forward mapping?

Forward mapping maybe the straight forward mapping you can think of, but it has two main 
disadvantages as a computational procedure: gaps and overlaps. Depending on the specific 
spatial transform function, you may have some output pixels that did not receive any 
input image pixels; these are the gaps. You may also have some output pixels that 
received more than one input image pixel; these are the overlaps. In both cases, 
it is challenging to figure out a reasonable way to set those output pixels. 

<p align="center">
  <img src="https://blogs.mathworks.com/images/steve/53/forward_mapping_b.png" alt="forward mapping problems">
</p>