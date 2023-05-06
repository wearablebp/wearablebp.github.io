---
layout: page
title: Explained Deviation
permalink: /ed/
nav_order: 3
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

Here, we provide motivating examples of, details of, and insight from the adopted statistic used in our paper, Explained Deviation (ED).

<h3> Motivating examples </h3>

<h4> Case Study 1: Small dataset distribution and low error meets error requirements from standard. </h4>

![case1](/_includes/case1.png)

<h4> Case Study 2: Low accuracy does not mean accurate device. We must condition on BP distribution. </h4>

![case2](/_includes/case2.png)

If we consider only the accuracies, study 1 will be the more "accurate" device. However, if we were provided with the BP distribution, we see that study 2 has the better device because it "explains" the data better.

<h3> Explained Deviation </h3>

To account for heterogeneity between studies, we condition our performance metric based on the BP distribution by adopting an interpretable statistic coined Explained Deviation (ED):

$$ED = \frac{\sigma_{pop}}{\sigma_\epsilon}$$ for subject split studies 

and

$$ED = \frac{\sigma_{\Delta}}{\sigma_{\Delta, \epsilon}}$$ for personalization studies

where:

$$\sigma_{pop}$$ is the standard deviation of the BP distribution of the whole dataset

$$\sigma_{\epsilon}$$ is the standard deviation of the BP estimation errors of the whole dataset

$$\sigma_{\Delta}$$ is the standard deviation of the change in BP distribution of the whole dataset

$$\sigma_{\Delta, \epsilon}$$ is the standard deviation of the change in BP estimation errors of the whole dataset

We can compute confidence intervals and perform hypothesis testing (See Appendix 1 below). We also compute $$ED_{min}$$, the estimated minimum ED required to meet the AAMI/ANSI/ISO 81060-2:2019 standards (See Appendix 2 below). $ED_{min}$$ for SBP and DBP were 2.17 and 1.39.

Next we report several insights:

<h3> Distribution of SBP and DBP Explained Deviations: SBP has larger proportion of studies that have higher Explained Deviation. </h3>
{% include SBP_ED_stats.html %}

{% include DBP_ED_stats.html %}

<h3> How DBP Explained Deviation varies with SBP Explained Deviation </h3>

We plot the ED of SBP versus ED of DBP for subject split and personalization studies. The size of the points are inversely proportional to the marigin of error. We delineate in green the minimum ED ($$ED_{min}$$). Notice that even though many studies report low error, they have an ED of around 1.

{% include scatter.html %}

<h2> Appendix 1: Explained Deviation Confidence Interval </h2>

Assume:
1. $$n_1$$ independent samples from a normally distributed population with variance $$\sigma_1^2$$
2. $$n_2$$ independent samples from a normally distributed population with variance $$\sigma_2^2$$

Given sample variance $$s_1^2$$ and $$s_2^2$$, we can write $$\frac{(n_1 - 1)s_1^2}{\sigma_1} \sim \chi_{n_1-1}^2$$ and $$\frac{(n_2 - 1)s_2^2}{\sigma_2} \sim \chi_{n_2-1}^2$$ The ratio of these two distributions is an F-distribution and can be written in the form: 

$$F=\frac{s_1^2/\sigma_1^2}{s_2^2/\sigma_2^2}$$


The $1-\alpha$ confidence interval can be written as:

$$P(F_{\alpha/2}(n_1-1, n_2-1) \leq \frac{s_1^2/\sigma_1^2}{s_2^2/\sigma_2^2} \leq F_{1-\alpha/2}(n_1-1, n_2-1)) = 1-\alpha$$ 

Simplifying the expression using the identity $$F_{1-\alpha/2}(n_1-1, n_2-1) = \frac{1}{F_{\alpha/2}(n_2-1, n_1-1)}$$, and substituting $$\frac{s_1}{s_2}=ED_{est}$$ and $$\frac{\sigma_1}{\sigma_2}=ED_{true}$$ gives: 

$$P(\sqrt{F_{\alpha/2}(n-1, n-1)} ED_{est} \leq ED_{true} \leq \sqrt{F_{1-\alpha/2}(n-1, n-1)} ED_{est}) = 1-\alpha$$

<h3> Appendix 2: Estimating required Explained Deviation from AAMI/ANSI/ISO 81060-2:2019 </h3>

The AAMI/ANSI/ISO Standard specifies that a device that for the general population should:

* Have n=85 subjects, should include ≥30% males and ≥30% females
* Have ≥5% of the reference SBP readings ≤100 mm Hg, ≥5% with ≥160 mmHg, and ≥20% with ≥140 mmHg
* Have ≥5% of reference DBP readings ≤60 mmHg, ≥5% with ≥100 mmHg, and ≥20% with ≥85 mm Hg

We used subsamples of a current publicly available dataset that satisfies these demographics ([PPG-BP](https://figshare.com/articles/dataset/PPG-BP_Database_zip/5459299)). To determine a subsample that satisfied the AAMI/ANSI/ISO Standards, we performed weighted sampling of subjects, where the weights were determined using Iterative Proportional Fitting (IPF) marginalized on the requirements. We repeated this process 10000 times and determine the minimum variance of the subsampled datasets. Then, we took the maximum error standard deviation allowed by AAMI/ANSI/ISO (±8mmHg). The minimum ED for SBP and DBP was computed to be 2.17 and 1.39. The implementation can be found on [Github](https://github.com/wearablebp).