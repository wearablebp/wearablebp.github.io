---
layout: page
title: Meta
permalink: /meta/
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

Here, we provide a brief summary of the statistics to account for heterogeneity in dataset distributions and calibration technique between studies. Furthemore, we provide interactive visuals. For specific details related to methodology, see <a href="{{site.baseurl}}/methods/">Methods</a> and our paper.

<h4> Summary Statistics </h4>

We adopt an estimate to evaluate estimation accuracy for studies that perform subject level split, coined Explained Deviation ($$ED$$), used to compute the effectiveness of a device with estimation error parameterized by ($$\mu_\epsilon, \sigma_\epsilon$$) on a population parameterized by ($$\mu_{pop}, \sigma_{pop}$$), where $$\mu$$ represents the mean and $$\sigma$$ represents the standard deviation. The ED can be computed as $$ ED = \frac{\sigma_{pop}}{\sigma_\epsilon}$$. The higher the ED, the better the device performs. On the other hand, an ED of 1 indicates that the estimator performs no better than an estimator that predicts a constant value. This is equivalent to an F-test for ratio of two variances with equal sample size, the null hypothesis $$H_0: ED \leq ED_{min}$$, and the alternative hypothesis $$H_1: ED \gt ED_{min}$$ where $$ED_{min}$$ is the computed minimum Explained Deviation that meets the standards. Furthermore, confidence intervals can be computed using the F-distribution by determining the probability $$P(\sqrt{F_{\alpha/2}(n-1, n-1)} ED_{est} < ED_{true} < \sqrt{F_{1-\alpha/2}(n-1, n-1)} ED_{est})  = 1-\alpha $$ where $$\alpha$$ is the level of significance, $$P$$ is the probability, $$F$$ is the F-distribution, and $$n$$ in the sample size. 

Using the same formulation, we compute $$ED$$ for personalization. However, in this case, we must take the change in BP of each subject into account: $$ED = \frac{\sigma_{\Delta BP, err}}{\sigma_{\Delta BP}}$$, where $$\sigma_{\Delta BP, err}$$ is the change in BP prediction error of the study cohort and $$\sigma_{\Delta BP}$$ is the standard deviation of the BP changes of the study cohort.

Moreover, we compute power ($$p$$) to determine whether the sample size is sufficient to detect the reported result. To do this we need to define selected level of significance, $$\alpha$$, and $$\beta=1-p$$. The ANSI/AAMI/ISO 81060-2 requires device error to have an absolute mean and standard deviation within 5±8mmHg with $$\alpha=0.05$$ and $$\beta=0.02$$, corresponding to $$p=0.98$$ and a sample size of 83. To compute this, they consider a two independent sample and continuous outcome study. The minimum sample size for a given $$\alpha$$ and $$\beta$$ is: $$n=2(\frac{z_{1-\alpha/2}+z_{1-\beta}}{ES})^2$$ where $$ES$$ is the effect size, $$z_{1-\alpha/2}$$ is the z-score at $$1-\alpha/2$$. Assuming $$ES=\frac{5}{8}$$, the minimum number of subjects for $$\alpha=0.05$$ and $$p=1-\beta=0.98$$ is 83. Conversely, the power of a study can be computed as $$p=1-\beta=\phi(ES \sqrt{\frac{n}{2}}-z_{1-\alpha/2}))$$ where $$ES$$ (effect size) is given by error bias/error standard deviation $$ES=\frac{5}{8}$$, and $$\phi$$ is the cumulative distribution function of a normal distribution. In this case, the null hypothesis ($$H_0$$) is that the device has a mean difference and standard deviation of error above 5mmHg and 8mmHg. If the power is 0.98, that means that the probability of rejecting the $$H_0$$ given the alternative hypothesis is true is greater than 98%.



Using our proposed metric to evaluate estimation accuracy, we plot the ED of SBP versus ED of DBP for subject level split and personalization studies. We indicate the size of points using the power of the study and also report important study information using a hover tool. Moreover, we delineate in green the minimum ED ($$ED_{min}$$), computed from the AAMI/ANSI/ISO Standards for SBP and DBP, which were 2.17 and 1.39 respectively. See <a href="{{site.baseurl}}/standards/">Standards</a> for more information about the calculation. 

{% include scatter.html %} <br> 
<center> <i> Fig. . A scatter plot of Explained Deviation for SBP versus Explained Deviation for DBP color coded by sensor device configuration. The size represent the power of the study. The tabs above allow to switch between Calibration Technique (subject level split or personalization). Hovering over the scatter points displays important parameter information related to the study. Clicking the legend allows to show or hide particular sensor data configurations. Finally, panning, zooming, tapping, resetting, and hovering tools are included on the right hand side of the legend. See <a href="{{site.baseurl}}/key/">Key</a> for a description of extracted parameters. </i> </center> <br>

We observe that there are 20 subject level split studies and 0 personalization studies that report an $$ED$$ that exceed $$ED_{min}$$ for both SBP and DBP. Moreover, we further narrow the criteria to studies that exceed $$ED_{min}$$ with 95% confidence and exceed a power of 0.98. To do this, we recompute the 90% margin of error ($$MOE_{90}$$), since the margin of error is computed on both sides of the distribution, and compute $$ED_{min} - MOE_{90}$$ to get the lower bound of the 95% confidence interval of the study. For brevity, this is called Explained Deviation SBP/DBP Lower Bound in Fig. . This ensures that there is a 95% probability that the true mean of the computed $$ED$$ is above $$ED_{min}$$.

<h4> Study selection </h4> 
We identified a total of 2510 articles from our database search and 29 articles from other sources. For inclusion in this analysis. After adjusting for duplicates by code, 2177 remained remained. We inspected the full articles and excluded 2008 unique articles and 36 additional studies (from articles that report multiple studies) based on the inclusion criteria. Likewise, we included 173 unique articles and 68 additional studies. From the 241 studies, we determined 94 studies performed subject level split and 147 studies performed personalization. Upon further examination, we identified the (change in) BP distribution of 61 and 9 studies for subject level split and personalization respecitvely. Ultimately, we included 70 studies in the meta-analysis. We provide a flow chart and statistics for extracted parameters in Fig. and Fig. respectively. See <a href="{{site.baseurl}}/search/">Search</a> for a complete list of studies and extracted parameters.

<br>
<div style="text-align: center"><img src="/images/graphviz.png" style="width: 100%"/></div>
<br>
<center> <i> Fig . . Summary of the review process. N indicates the number of records and n indicates the number of studies. Some articles report multiple studies. </i> </center>
<br>

{% include metadata_stats.html %}

<center> <i> Fig. . Extracted parameter statistics of meta-analysis included studies. Using the tabs above allows to switch between different extracted parameter distributions. Moreover, for categorical statistics, hovering over the bars shows the number of entries and percentage composition of subject level split and personalization studies. See <a href="{{site.baseurl}}/key/">Key</a> for a description of extracted parameters. </i> </center> <br>

From Fig. ,for sensor data, we observe that the most common sensor data configuration used for BP estimation is photoplethysmography and photoplethysmography with electrocardiography. For algorithm, we observe that the most common class of algorithm used is classical machine learning, often in conjuntion with hand-crafted features. For subject characteristics, overall, we observe that there is a similar split between using healthy, diseased and a mix of healthy and diseased subjects in the study. However, it is notable that there were significantly less studies that used diseased subjects for personalization. For datasets used, we observe that an overwheming number of studies used databases collected internally that are not avaialble for the public and the most common publically available database used is Medical Information Mart for Intensive Care (MIMIC). For study characteristics, we observe that the majority of subject level split studies were observational. On the other hand, we observe that the personalization studies were split similarly between observational and interventional studies. For the quantitative metrics, notably, the standard devation of the BP distribution for SBP is larger than that for DBP and the standard deviation of the BP distribution of subject level split studies is greater than that of personalization studies.











To provide actionable recommendations, we summarize our findings in several insights.
<h4> Insight 1: Most studies suffer from Data Leakage </h4>
Whether conscious or unconscious, 83\% of the studies suffer from high bias in algorithm design, specifically in data leakage. This may be a result of publication bias, in which only the studies with good results are published. In particular, studies that perform record level split without personalization report remarkably low errors. Researchers must take care in algorithm design to avoid these common pitfalls. 
\subsection{Insight 2: Most studies do not produce statistically significant results}
For the studies that are included in our analysis, only 28\% of studies report sufficient power. Researchers must take care in study design to ensure that there are enough participants.

<h4> Insight 3: Most personalization studies are not well designed </h4>
It is notable that less than 10\% of the personalization studies include information about the change in BP distribution. Even though there are studies that report the initial BP distribution of subjects, this is not sufficient, as some experiments do not allow sufficient variation in BP. As a consequence, allowing the initial calibrated BP values to be the estimator can lead to small errors. In a similar vein, the number of observational studies and interventional type studies for personalization studies was almost equal. However, observational studies may not allow sufficient BP variation, leading to lower $ED$. Due to the lack of longitudinal personalization studies that have high $ED$, we suspect that longitudinal studies may demonstrate device estimation accuracy no more than stable BP over the test period.

Furthermore, it is also notable that even though there may be sufficient time between training and testing data, physiology may be the same. Therefore, it is essential to characterize these changes in physiologies. Mukkamala et al., (2017) discusses the maximum calibration period for acceptable error limits. However, this may only demonstrate when the physiology of a person changes so significantly that the PTT model estimation is outside the limits. Since the rate of physiological change is individually and temporally dependent, there is no one-size-fits-all maximum calibration period.

Finally, it is worthwhile to note that even though Pulse Arrival Time (PAT) and Pulse Transit Time (PTT) are considered well-established features \cite{mukkamala2015theory}, there are no personalization studies that demonstrate an $ED$ that is greater or equal to $ED_{min}$. To elaborate, there are no personalization studies that involve the use of PTT that reported the change in BP distribution. All of the PAT and PTT personalization studies cluster around the 1, with some that are below the error boundaries established by the standards. This may be due to poor study design or that the PTT model is too simple to represent the changing physiologies.

Researchers need to conduct more well-designed studies to determine if these features can explicitly detect changes in BP.

<h4> Insight 4: Some studies do not have reproducible results </h4>
It is important for a study to have reproducible results so the algorithms can be tested on other datasets for validity. Not only do these algorithms include estimation models, but they also include the data filtering algorithms that may shift the training and testing set distributions. Therefore, we implemented four studies that exceed $ED_{min}$ and have sufficient power. Then, we benchmarked the data filtering algorithms and model combinations on publically available datasets. The implementation was done based on the code provided (on GitHub) and/or the details of the algorithms presented in the paper. 

{% include replicated_ed_diff_scatter.html %}
<br>

{% include benchmark_table.html %}
<br>

Based on the implemented benchmarks, the claimed Explained Deviation for particular data filtering algorithm and model were not matched for the four algorithms selected. In fact, three of the four algorithms yielded an ED of 1. This may be a result of incomplete reporting and/or misleading reporting of specific details in the algorithms. Moreover, none of the benchmarked algorithms provided data filtering algorithms that allow users to download a dataset and perform operations such as detecting movement artifacts or poor-quality signals.

Moreover, reproducibility is not only limited to software. Some studies involve using unconventional sensors. Based on our review, 2 of 11 studies (22%) that do not use PPG or ECG+PPG suffer from low power compared to 17 of 42 (40%). More than half of high-powered studies use one or more of the publicly available datasets. Although developing new devices is important for exploratory research, these devices are not verifiable by an external party. In addition to transparent hardware, there needs to be more transparency in experimental protocols. For example, the contact pressure is known to affect waveform morphology \cite{chandrasekhar2020ppg}. Since feature extraction techniques rely on waveform morphology to detect key points, devices used in one study may not yield the same results without standardization of experimental protocols. Some studies may use a PPG sensor with a different spring constant.
More details on experimental protocols, data, devices, and code should be publically available to ensure reproducibility.

<h4> Insight 5: Photoplethysmography shows promise for scalable and wearable blood pressure monitoring </h4>
Photoplethysmography (PPG) is a low-cost, ubiquitous, and wearable sensor. All of the studies that report high $ED$ with sufficient power involve the use of PPG. This may be because all publicly available datasets that have sufficient power include PPG, namely MIMIC \cite{mimic3}, PPG-BP \cite{ppgbp}, and VitalDB \cite{vitaldb}. Therefore, PPG is a good candidate for benchmarking BP estimation algorithms.
