---
title: "Segmentation of Forvea Avascular Zone"
date: 2019-09-03
tags: ["image processing", "Forvea Avascular Zone", "segmentation"]
classes: wide
header:
    teaser: "assets/images/faz-procedure.png"
excerpt: "PURPOSE: Present a method for automatic FAZ segmentation based on Hessian-based filter and Level Set in optical coherence tomography angiography (OCTA) images"
mathjax: "true"
author_profile: false
sidebar:
  - title: "Role"
    # image: http://placehold.it/350x250
    # image_alt: "logo"
    text: "Researcher"
  - title: "Responsibilities"
    text: "Implement evaluation metrics for the algorithm. Write the journal article."
# gallery:
#   - url: /assets/images/laohac.jpg
#     image_path: assets/images/mandala.jpg
#     alt: "placeholder image 1"
#   - url: /assets/images/green-papaya.png
#     image_path: assets/images/walden.jpg
#     alt: "placeholder image 2"
#   - url: /assets/images/wheatfield.jpg
#     image_path: assets/images/decision-tree.jpg
#     alt: "placeholder image 3"
---

## Introduction
Fovea region of the human retina for high resolution vision. Within fovea is a region devoid from retinal vessels called <a href="https://en.wikipedia.org/wiki/Foveal_avascular_zone" class="btn btn--info">Fovea Avascular Zone</a> (FAZ) where the light is sensed without loss or distortions. While the FAZ shape and size may vary widely in normal human eyes, certain changes of shape and size of the FAZ are related to developmental events and injury or disease before birth, during infancy, or later stages in life and these may cause loss of vision. To understand the effects of retinal diseases on the FAZ, it is essential first to measure the FAZ area accurately. 

However, we observes that most ongoing researches on algorithm FAZ segmentation algorithms suffer one major problem. The evaluating metrics for image segmentation result are quite simple and in our view, not sufficient to verify its validity. Most studies rely on FAZ area due to its clinical interpretation, however, area does not guarantee similarity between the automatic and manual segmentation. On the contrary, if the similarity is confirmed, it is highly likely that two area values would agree.

> In this study, we present (i) a novel method for automatic FAZ segmentation that achieved comparable results with manual labelling and better performance than previous studies and (ii) a more comprehensive and more adequate evaluation framework for assessing FAZ segmentation algorithm. We adopted Hessian filter and Level Set for FAZ segmentation. The method has been widely used and frequently used in the domain of neural imaging. However, the usage of this method on OCTA, especially in FAZ segmentation, is yet to be explored.
{: .notice--success}

## Method
Our method is summarized as follows:
<img src="{{ site.url }}{{ site.baseurl }}/images/segmentation-faz/faz-procedure.png" alt="FAZ segmentation procedure">

1. Image Processing

    a. Hessian-based filter
    
    $$
    H =\begin{pmatrix}
    \frac{\partial^2 I}{\partial{x^2}} &\frac{\partial^2 I}{\partial{x}\partial{y}} &\frac{\partial^2 I}{\partial{x}\partial{z}} \\

    \frac{\partial^2 I}{\partial{y}\partial{x}} &\frac{\partial^2 I}{\partial{y^2}} &\frac{\partial^2 I}{\partial{y}\partial{z}} \\

    \frac{\partial^2 I}{\partial{z}\partial{x}} &\frac{\partial^2 I}{\partial{z}\partial{y}} &\frac{\partial^2 I}{\partial{z^2}} \\
    
    \end{pmatrix},$$

    Gaussian filter:
    $$ I(x,y,z,\sigma) = G(x,y,z,\sigma)*I(x,y,z) $$

    b. Level set

2. Method
3. Evaluation

## Results

## Conclustion

<!-- {% include gallery caption="This is a sample gallery to go along with this case study." %} -->