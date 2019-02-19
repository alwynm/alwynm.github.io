---
layout: post
title: Forward mapping
categories: Research
ready : true
---


Let's say, you have applied an affine transformation(translation and rotation and scaling) to an image. Applying these transformations will translate, rotate or rotate the image i.e., we have to move the pixel location of the source image according to the transformation to the target image. 

<img align="center" src="https://www.mathworks.com/content/mathworks/www/en/company/newsletters/articles/using-matlabs-meshgrid-command-and-array-operators-to-implement-one-and-two-variable-functions/jcr:content/mainParsys/image_2.adapt.full.low.gif/1469941369997.gif" alt="meshgrid">

### What is forward mapping?

As we are manipulation the pixel location, we will construct a grid where each grid values is the location of pixels on the source image. Apply the transformation to this grid to get the desired tranformed grid. Use tranformed grid to look back at the source image and copy pixel values to that output pixel. This is commonly called forward mapping.

<img align="center" src="https://blogs.mathworks.com/images/steve/53/forward_mapping_a.png" alt="forward mapping">


### Why you shouldnt use it?

Forward mapping has two main disadvantages as a computational procedure: gaps and overlaps. Depending on the specific spatial transform function, you may have some output pixels that did not receive any input image pixels; these are the gaps. You may also have some output pixels that received more than one input image pixel; these are the overlaps. In both cases, it is challenging to figure out a reasonable way to set those output pixels. 

<img align="center" src="https://blogs.mathworks.com/images/steve/53/forward_mapping_b.png" alt="forward mapping problems">