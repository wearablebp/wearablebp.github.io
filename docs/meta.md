---
layout: page
title: Meta
permalink: /meta/
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

While other review papers have used common metrics such as mean absolute error (MAE) and percent error, these cannot be applied due to the large heterogeneity in datasets, devices, and algorithms used in each study. For example, a study with a dataset with small BP distribution may yield better results, as there is less variation that the model needs to explain. Here, we provide a brief summary of the statistics to account for heterogeneity in dataset distributions and calibration technique between studies and provide analysis with interactive visuals. For specific details related to methodology, see <a href="{{site.baseurl}}/methods/">Methods</a> and our paper.

<h2> Summary Statistics </h2>

In addition to the performance criteria stated in the standards, we condition our performance metric based on the BP distribution, which is a significant source of heterogeneity between studies. To accomplish this, we adopt an interpretable statistic coined Explained Deviation (ED). For subject level split, ED is used to compute the effectiveness of a device with estimation error parameterized by ($\mu_\epsilon, \sigma_\epsilon$) on a population parameterized by ($$\mu_{pop}$$, $$\sigma_{pop}$$), where $\mu$ represents the mean and $$\sigma$$ represents the standard deviation. The ED can be computed as $$ED = \frac{\sigma_{pop}}{\sigma_\epsilon}$$. The higher the ED, the better the system performs. On the other hand, an ED of 1 indicates that the estimator performs no better than an estimator that predicts a constant value. Intuitively, this statistic determines how much the model “explains” the BP distribution. Statistically, ED is similar to an F-test for the ratio of two variances with equal sample size, the null hypothesis $$H_0: ED \leq ED_{min}$$, and the alternative hypothesis $$H_1: ED > ED_{min}$$ where $$ED_{min}$$ is the computed minimum Explained Deviation that meets the standards (See Supplementary 1). One limitation of using ED is the assumptions of zero bias and normality, which are not always the case. However, this gives a good ballpark estimate in practice.

Furthermore, we can compute confidence intervals using the F-distribution by determining the bounds $$P(\sqrt{F_{\alpha/2}(n-1, n-1)} ED_{est} \leq ED_{true} \leq \sqrt{F_{1-\alpha/2}(n-1, n-1)} ED_{est})  = 1-\alpha $$ where $$\alpha$$ is the level of significance, $$P$$ are the probability, $$F$$ is the F-distribution and $$n$$ in the sample size. The Margin of Error is half the Confidence Interval. Using the same formulation, we compute ED for personalization. However, in this case, we must take the change in BP of each subject into account: $$ED = \frac{\sigma_{\Delta BP, err}}{\sigma_{\Delta BP}}$$, where $$\sigma_{\Delta BP, err}$$ is the BP change error of the study cohort and $$\sigma_{\Delta BP}$$ is the standard deviation of the BP changes of the study cohort. Finally, to determine whether the sample size is sufficient to detect the reported result, we compute power ($$p$$). To do this we define $$\alpha=0.05$$, $$\beta=0.02$$, and effect size $$ES=\frac{5}{8}$$, based on [ANSI/AAMI/ISO 81060-2:2019](https://webstore.ansi.org/standards/aami/ansiaamiiso810602019). This corresponds to $$p=0.98$$ and a sample size of approximately 85.

<h2> Estimating required Explained Deviation from AAMI/ANSI/ISO 81060-2:2019 </h2>

The AAMI/ANSI/ISO Standard specifies that a device that for the general population should:

* Have n=85 subjects, should include ≥30% males and ≥30% females
* Have ≥5% of the reference SBP readings ≤100 mm Hg, ≥5% with ≥160 mmHg, and ≥20% with ≥140 mmHg
* Have ≥5% of reference DBP readings ≤60 mmHg, ≥5% with ≥100 mmHg, and ≥20% with ≥85 mm Hg

Currently, there are no publicly available datasets that satisfy these demographics. However, the [PPG-BP](https://figshare.com/articles/dataset/PPG-BP_Database_zip/5459299) can meet these requirements if it is subsampled. To determine a subsample that satisfied the AAMI/ANSI/ISO Standards, we performed weighted sampling of subjects, where the weights were determined using Iterative Proportional Fitting (IPF) marginalized on the requirements. We repeat this process 10000 times and determine the minimum variance of the subsampled datasets. Then, we took the maximum error standard deviation allowed by AAMI/ANSI/ISO (±8mmHg). The minimum ED for SBP and DBP was computed to be 2.17 and 1.39. The implementation can be found on [Github](https://github.com/wearablebp).


<h2> Synthesis of studies </h2>

Using our proposed metric to evaluate estimation accuracy, we plot the ED of SBP versus ED of DBP for subject level split and personalization studies. We indicate the size of points using the power of the study and also report important study information using a hover tool. Moreover, we delineate in green the minimum ED ($$ED_{min}$$), computed from the AAMI/ANSI/ISO Standards for SBP and DBP, which were 2.17 and 1.39 respectively.

{% include scatter.html %} <br> 
<center> <i> Fig. . A scatter plot of Explained Deviation for SBP versus Explained Deviation for DBP color coded by sensor device configuration. The size represent the power of the study. The tabs above allow to switch between Calibration Technique (subject level split or personalization). Hovering over the scatter points displays important parameter information related to the study. Clicking the legend allows to show or hide particular sensor data configurations. Finally, panning, zooming, tapping, resetting, and hovering tools are included on the right hand side of the legend. See <a href="{{site.baseurl}}/key/">Key</a> for a description of extracted parameters. </i> </center> <br>

{% include metadata_stats.html %}

<center> <i> Fig. . Extracted parameter statistics of meta-analysis included studies. Using the tabs above allows to switch between different extracted parameter distributions. Moreover, for categorical statistics, hovering over the bars shows the number of entries and percentage composition of subject level split and personalization studies. See <a href="{{site.baseurl}}/key/">Key</a> for a description of extracted parameters. </i> </center> <br>



<h2> Supplementary 1: Explained Deviation Confidence Interval </h2>

Assume: 
1. $$n_1$$ in dependent observations from a normally distributed popoulation with variance $$\sigma_1^2$$ and
2. $$n_2$$ independent observations from a normall distributed population with variance $$\sigma_2^2$$. 

Given sample variance $$s_1^2$$ and $$s_2^2$$, we can write $$\frac{(n_1 - 1)s_1^2}{\sigma_1} \sim \chi_{n_1-1}^2$$ and $$\frac{(n_2 - 1)s_2^2}{\sigma_2} \sim \chi_{n_2-1}^2$$ <br> The ratio of these two distributions is a F-distribution and can be written in the form $$F=\frac{s_1^2/\sigma_1^2}{s_2^2/\sigma_2^2}$$ <br> The $$1-\alpha$$ confidence interval can be written as $$P(F_{\alpha/2}(n_1-1, n_2-1) \lt \frac{s_1^2/\sigma_1^2}{s_2^2/\sigma_2^2} \lt F_{1-\alpha/2}(n_1-1, n_2-1)$$ <br> Simplying the expression, using the identity $$F_{1-\alpha/2}(n_1-1, n_2-1) = \frac{1}{F_{\alpha/2}(n_2-1, n_1-1)}$$, and substituting $$\frac{s_1}{s_2}=ED_{est}$$ and $$\frac{\sigma_1}{\sigma_2}=ED_{true}$$ gives $$P(\sqrt{F_{\alpha/2}(n-1, n-1)} ED_{est} < ED_{true} < \sqrt{F_{1-\alpha/2}(n-1, n-1)} ED_{est})  = 1-\alpha $$

<h2> Supplementary 2: Power Analysis </h2>

Compute $$p=1-\beta=\phi(ES \sqrt{\frac{n}{2}}-z_{1-\alpha/2}))$$ where $$ES$$ (effect size) is given by error bias/error standard deviation=$$\frac{5}{8}$$, $$\alpha$$ is the selected level of significance, $$\beta=1-P$$, and $$\phi$$ is the cumulative distribution function of a normal distribution