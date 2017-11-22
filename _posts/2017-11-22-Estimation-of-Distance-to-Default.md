---
layout: post
title: Estimation of Distance-to-Default
comments: true
---

This post summarizes several methods in calculating distance-to-default (DD), which is an important factor in measuring a firm's probability of default.

## The Distance-to-Default

As the names suggests, distance-to-default (DD) measures how far a firm is away from default. Strictly speaking, the firm must have limited liability. DD has been widely used both in academic research and business applications. Moody's EDF is one of the most famous applications that use DD to infer probability of default with an empirical mapping. 

The definition of DD is based on Merton's model, which assumes that firms are financed by equity and thus can be modeled as a call option on the underlying assets of the firm with a strike price equal to the book value of the firm's liabilities. The asset value *V* follows a geometric Brownian motion.

![equation](http://www.sciweavers.org/tex2img.php?eq=%20%5Cfrac%7BdV%7D%7BV%7D%20%3D%20%5Cmu%20dt%2B%20%20%5Csigma%20_%7BV%7D%20dz&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

Then the equity value at time *t* by Black-Scholes option pricing formula becomes

![equation](http://www.sciweavers.org/tex2img.php?eq=S%28%20V_%7Bt%7D%20%2C%20%5Csigma%20%29%3D%20V_%7Bt%7D%20N%28%20d_%7Bt%7D%20%29-%20e%5E%7B-r%28T-t%29%7DFN%28%20d_%7Bt%7D-%20%5Csigma%20%5Csqrt%7BT-t%7D%20%20%20%29%20&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

Then DD is defined as below. It can be seen as the logarithm of the leverage ratio shifted by the expected return and scaled by the volatility.

![equation](http://www.sciweavers.org/tex2img.php?eq=DD%20%3D%20%20%5Cfrac%7Bln%28%20%5Cfrac%7BV_%7Bt%7D%7D%7BF%7D%20%29%20%2B%20%28%20%5Cmu%20-%20%5Cfrac%7B%20%20%5Csigma%20%5E%7B2%7D%20%7D%7B2%7D%20%29%28T-t%29%7D%7B%5Csigma%20%5Csqrt%7BT-t%7D%7D%20&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

In practice, however, the asset return drift term cannot be estimated with reasonable precision using high frequency data over a time span of several years due to the nature of diffusion models. Therefore, DD is calculated in the following reduced form, which yields a more stable value. So in order to calculate DD, we need to first estimate asset drift and asset volatility.

![equation](https://www.sciweavers.org/tex2img.php?eq=%20DD%5E%7B%2A%7D%20%20%3D%20%20%5Cfrac%7Bln%28%20%5Cfrac%7BV_%7Bt%7D%7D%7BF%7D%20%29%20%7D%7B%5Csigma%20%5Csqrt%7BT-t%7D%7D%20&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)


## The Market Value Proxy Method

Since the market value of asset is not directly observable and hard to determine, an intuitive alternative is to use the sum of equity value and the market value of liability. For public firms, it is easy to obtain the equity value, but the market value of liability is hard to estimate since most firms have a large portion of debt in some non-tradable forms. Therefore, the market value proxy method offers a hybrid approach of adding equity value to the book value of liabilities. Using the market value proxy method, it is straightforward to estimate the asset drift and asset volatility. However, it is argued that the market value proxy method provides an upward biased estimation of the asset value, which results in overestimation of DD. 


## The Volatility Restriction Method

By applying Ito's lemma to both sides of the Black-Scholes option pricing formula, one can arrive at the following second equation decribing the relationship between asset volatility and equity volatility (the so-called volatility restriction).

![equation](http://www.sciweavers.org/tex2img.php?eq=%20S_%7Bt%7D%20%3D%20S%28%20V_%7Bt%7D%3B%20%5Csigma%20%20%29&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

![equation](http://www.sciweavers.org/tex2img.php?eq=%20%20%5Csigma%20_%7B%20S_%7Bt%7D%20%7D%20%3D%20%5Csigma%20%20%5Cfrac%7B%20V_%7Bt%7D%20%7D%7BS%28%20V_%7Bt%7D%2C%20%5Csigma%20%20%29%7D%20N%28%20d_%7Bt%7D%20%29&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

Then together the two equations above have two unknowns, the asset value and asset volatility. So the two equation system can be solved at any given time point. In practice the volatility restriction method can be implemented through the following two approaches, which do not yield exactly the same results and thus create some inconsistency.

- Approach 1: solve the two-equation system repeatedly to get a time series of asset values, them compute the sample mean to obtain an estimate for 𝝁.
- Appraoch 2: solve the two-equation system once at a single time, and apply the obtained 𝝈 to all earlier time points to obtain a time series of implied asset values and then derive the 𝝁 from the time series


