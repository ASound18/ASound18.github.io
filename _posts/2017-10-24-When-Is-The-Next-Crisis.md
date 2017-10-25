---
layout: post
title: When Is The Next Crisis
---

In short, my answer is around **two months** from now. I will explain in details.

For the next financial crisis, there might be hundreds of questions to ask. 
+ When will it arrive? 
+ What would be the cause? 
+ How would the impact be?
+ How should we get prepared for it?
+ And so on...

Unfortunately, I am not capable of answering every single one of them, or even anyone of them. But I did some exploration to try to address the first question about the timing of the next crisis based on the data I have with some prediction techniques. 

Moody's Analytics **Default & Recovery Database (DRD)** has data for 500,000+ debts and 50,000+ global coporate and sovereign entities, including rating, default, and recovery history[^first]. The data is filtered to 1983 and later, with the number of default issuers and average recovery rates calculated by 30 day post-default trading prices[^second]. From the chart below, there is obviously a credit trending cycle with an approximate 10-year window.

![Moodys_Default_Recovery](/images/Moodys_Default_Recovery.png)

Then I gave a try of the recently learnt **Kinetic Component Analysis** on the data in order to make some predictions. It is worth noticing that the chart above is generated using annual data, while daily data is used for making predictions. Kinetic Component Analysis decompose noisy data into three components: position, velocity and acceleration, after which the estimations are done through **Kalman Filters**. Since annual data from 1983 to today does not really contain much noise, predictions based on annual data would have really funky results. So below is the chart of applying **Kinetic Component Analysis** in making predictions.

![KCA_Default_Prediction](/images/KCA_Default_Prediction.png)

The prediction window is 50 work day ahead, which can be converted to roughly a bit over two months. Based on the prediction chart, the level of position will be close to that of previous crisis no later than two months from now. Again, this is merely an application of **Kinetic Component Analysis** on Moody's **Default & Recovery Database (DRD)**. The prediction has been made, and let's see how it goes.




[^first]: [Moody's Analytics Default & Recovery Database (DRD)](https://www.moodysanalytics.com/product-list/default-and-recovery-database)
[^second]: For distressed exchanges, trading prices at default are used. For other types of defaults, trading prices approximately one month after default are used.
