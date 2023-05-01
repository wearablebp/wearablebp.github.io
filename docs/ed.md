---
layout: page
title: Explained Deviation
permalink: /ed/
nav_order: 3
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

<h3> Explained Deviation </h3>

To account for heterogeneity between studies, we condition our performance metric based on the BP distribution by adopting an interpretable statistic coined Explained Deviation (ED). For subject split, ED is used to compute the effectiveness of a device with estimation error of the combined device and algorithm parameterized by ($$\mu_\epsilon, \sigma_\epsilon$$) on a population measured with a gold standard and parameterized by ($$\mu_{pop}, \sigma_{pop}$$), where $$\mu$$ represents the mean and $$\sigma$$ represents the standard deviation. The ED can be computed as $$ ED = \frac{\sigma_{pop}}{\sigma_\epsilon}$$. In general, the higher the ED, the better the device performs on the dataset. But an ED of 1 indicates that the estimator performs no better than an estimator that predicts a constant value at the mean of the BP distribution. Intuitively, this statistic determines how much the device and algorithm “explains” the BP distribution. For personalization, we must take the change in BP of each subject into account: $$ED = \frac{\sigma_{\Delta}}{\sigma_{\Delta, \epsilon}}$$, where $$\sigma_{\Delta}$$ is the standard deviation of the BP changes of the whole dataset and $$\sigma_{\Delta, \epsilon}$$ is the BP change error of the study cohort. We can also compute confidence intervals and perform hypothesis testing

<h3> Estimating required Explained Deviation from AAMI/ANSI/ISO 81060-2:2019 </h3>

The AAMI/ANSI/ISO Standard specifies that a device that for the general population should:

* Have n=85 subjects, should include ≥30% males and ≥30% females
* Have ≥5% of the reference SBP readings ≤100 mm Hg, ≥5% with ≥160 mmHg, and ≥20% with ≥140 mmHg
* Have ≥5% of reference DBP readings ≤60 mmHg, ≥5% with ≥100 mmHg, and ≥20% with ≥85 mm Hg

Currently, there are no publicly available datasets that satisfy these demographics. However, the [PPG-BP](https://figshare.com/articles/dataset/PPG-BP_Database_zip/5459299) can meet these requirements if it is subsampled. To determine a subsample that satisfied the AAMI/ANSI/ISO Standards, we performed weighted sampling of subjects, where the weights were determined using Iterative Proportional Fitting (IPF) marginalized on the requirements. We repeat this process 10000 times and determine the minimum variance of the subsampled datasets. Then, we took the maximum error standard deviation allowed by AAMI/ANSI/ISO (±8mmHg). The minimum ED for SBP and DBP was computed to be 2.17 and 1.39. The implementation can be found on [Github](https://github.com/wearablebp).


<h3> Distribution of SBP and DBP Explained Deviations: SBP has larger proportion of studies that have higher Explained Deviation. </h3>
{% include SBP_ED_stats.html %}

{% include DBP_ED_stats.html %}

<h3> How DBP Explained Deviation varies with SBP Explained Deviation </h3>

Using our proposed metric to evaluate estimation accuracy, we plot the ED of SBP versus ED of DBP for subject split and personalization studies. We indicate the size of points using the power of the study and also report important study information using a hover tool. Moreover, we delineate in green the minimum ED ($$ED_{min}$$), computed from the AAMI/ANSI/ISO Standards for SBP and DBP, which were 2.17 and 1.39 respectively.

{% include scatter.html %}

<h2> Supplementary 1: Explained Deviation Confidence Interval </h2>

Assume:
1. $$n_1$$ independent samples from a normally distributed population with variance $$\sigma_1^2$$
2. $$n_2$$ independent samples from a normally distributed population with variance $$\sigma_2^2$$

Given sample variance $$s_1^2$$ and $$s_2^2$$, we can write $$\frac{(n_1 - 1)s_1^2}{\sigma_1} \sim \chi_{n_1-1}^2$$ and $$\frac{(n_2 - 1)s_2^2}{\sigma_2} \sim \chi_{n_2-1}^2$$ The ratio of these two distributions is an F-distribution and can be written in the form: 

$$F=\frac{s_1^2/\sigma_1^2}{s_2^2/\sigma_2^2}$$


The $1-\alpha$ confidence interval can be written as:

$$P(F_{\alpha/2}(n_1-1, n_2-1) \leq \frac{s_1^2/\sigma_1^2}{s_2^2/\sigma_2^2} \leq F_{1-\alpha/2}(n_1-1, n_2-1)) = 1-\alpha$$ 

Simplifying the expression using the identity $$F_{1-\alpha/2}(n_1-1, n_2-1) = \frac{1}{F_{\alpha/2}(n_2-1, n_1-1)}$$, and substituting $$\frac{s_1}{s_2}=ED_{est}$$ and $$\frac{\sigma_1}{\sigma_2}=ED_{true}$$ gives: 

$$P(\sqrt{F_{\alpha/2}(n-1, n-1)} ED_{est} \leq ED_{true} \leq \sqrt{F_{1-\alpha/2}(n-1, n-1)} ED_{est}) = 1-\alpha$$