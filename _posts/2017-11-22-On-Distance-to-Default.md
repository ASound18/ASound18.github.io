---
layout: post
title: On Distance-to-Default
comments: true
---

This post summarizes several methods in calculating distance-to-default (DD), which is an important factor in measuring a firm's probability of default.

## The Distance-to-Default

As the names suggests, distance-to-default (DD) measures how far a firm is away from default. Strictly speaking, the firm must have limited liability. DD has been widely used both in academic research and business applications. Moody's EDF is one of the most famous applications that uses DD to infer probability of default with an empirical mapping. 

The definition of DD is based on Merton's model, which assumes that firms are financed by equity and thus can be modeled as a call option on the underlying assets of the frim with a strike price equal to the book value of the firm's liabilities. The asset value *A* follows a geometric Brownian motion.

{![equation](http://www.sciweavers.org/tex2img.php?eq=%20%5Cfrac%7BdA%7D%7BA%7D%20%3D%20%5Cmu%20dt%2B%20%20%5Csigma%20_%7BA%7D%20dz&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)}

