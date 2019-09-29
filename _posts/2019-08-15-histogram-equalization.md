---
title: "Histogram Equalization"
tags: [digital-image-processing, algorithm, 'histogram']
category: 'fundamentals'
mathjax:  true
---

Histogram is an effective tool to look at and manipulate images. In many cases, we want to flatten the histogram of an image so that we can increase the contrast and have a better look on objects and details in the images. Histogram Equalization is the technique to achieve this goal.  

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/histogram-equalization/hist-equal2.png">

We first consider tntensity levels in an image as random variables in the interval $$ [0, L-1] $$ where $$ L $$ is the number of gray levels.

Let $$ s $$ and $$ r $$ be the random variables with PDF $$ p_s(s) $$ and $$ p_r(r) $$ respectively, where $$ r $$ represents intensity of the original image while $$ s $$ the output image. 

What we wants is to find a transform function $$ T(r) $$ such that the final $$ p_s(s) $$ will (approximately) become a constant function or a uniform probability distribution:

$$ p_s(s) = \frac{1}{L-1}, \; 0\leq s \leq L-1 \quad (1) $$

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/histogram-equalization/hist-equal1.png">

On the other hand, we also have a constraint:

$$ p_s(s)ds = p_r(r)dr \quad (2)$$

which means that the area under the curve $$ p_s(s) $$ and $$ p_r(r) $$ has to be equal.

Subtitute (1) to (2), we have:

$$ \frac{1}{L-1}ds = p_r(r)dr$$

$$ \Leftrightarrow \frac{1}{L-1}ds = p_r(r)dr $$

$$ \Leftrightarrow \int ds = (L-1) \int p_r(r)dr $$


The result:

$$ s  = T(r) = (L-1)\int_{0}^{r}p_r(x)dx $$

Discrete form:

$$
\begin{split} 
s = T(r) &= (L-1)\cdot p_x(r) \\ 
         &= (L-1)\sum_{j=0}^{k}r_j = \frac{L-1}{MN}\sum_{0}^{k}n_j
\end{split}
$$ 

$$
\begin{split}
p_X(x)  &= P(X=x) \\
        &= P(X=k)
\end{split}
$$

## References:

Digital Image Processing, 3rd Edition. Rafael C. Gonzalez, University of Tennessee. Richard E. Woods, MedData Interactive. ©2008 