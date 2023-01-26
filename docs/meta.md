---
layout: page
title: Meta-Analysis
permalink: /meta/
nav_order: 2
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

While other review papers have used common metrics such as mean absolute error (MAE) and percent error, these cannot be applied due to the large heterogeneity in datasets, devices, and algorithms used in each study. For example, a study with a dataset with small BP distribution may yield better results, as there is less variation that the model needs to explain. Here, we provide a brief summary of the statistics to account for heterogeneity in dataset distributions and calibration technique between studies and provide analysis with interactive visuals. For specific details related to methodology, see <a href="{{site.baseurl}}/methods/">Methods</a> and our [paper](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=10). Please see the Wearable BP on [GitHub](https://github.com/wearablebp/) for code to reproduce Systematic Review results and visuals. To access the raw data used in our systematic review, please fill out this [form](https://forms.gle/3g2yTkPNVmJFB2it6).

<h2> Metadata Statistics </h2>

To understand the distribution of extracted parameters for the studies included in our Systematic Review, we visualize the distribution of the different study parameters. For categorical statistics, hovering over the bars shows the number of entries and percentage composition of subject split and personalization studies in all categories. See <a href="{{site.baseurl}}/key/">Key</a> for a description of extracted parameters.

<h3> Distribution of Sensors and Systems: ECG and PPG+ECG are the most used Sensors and Systems </h3>

{% include Sensor_Data_stats.html %}

<h3> Distribution of Algorithm Classes: Classical ML and Deep Learning are the most used algorithm classes. </h3>

{% include Algorithm_stats.html %}

<h3> Distribution of Datasets: Most datasets are private/internal. MIMIC is the most used publicly available dataset. </h3>
{% include Dataset_stats.html %}

<h3> Distribution of Test Subject Characteristics: Most datasets only include either healthy or diseased subjects. </h3>
{% include Testing_Subject_Characteristics_stats.html %}

<h3> Distribution of Study Characteristics (observational or interventional): Most datasets are observational. Personalization studies are split between observational and interventional. </h3>
{% include Study_Characteristics_stats.html %}

<h3> Distribution of Number of Test SubjectsMost datasets contain less than 300 testing subjects. Personalization studies tend to have lower number of testing subjects than subject split studies. </h3>
{% include Number_of_Test_Subjects_stats.html %}

<h3> Distribution of Dataset SBP and DBP: Subject split studies tend to have larger BP STD compared to personalization change in BP STD. Relative magnitude of (change in) BP distribution is less for DBP. </h3>
{% include SBP_Distribution_STD_stats.html %}

{% include DBP_Distribution_STD_stats.html %}

<h3> Distribution of Study Power: Personalization studies tend to be less powered for <5±8mmHg on average. </h3>
{% include Power_stats.html %}

<h3> Importance of accounting for BP Distribution in evaluation: BP Distribution is a confounding factor in BP Error </h3>

To determine whether the BP distribution affects the error we plot the standard deviation of the errors against the standard deviation of the BP distributions. We find that lower error is harder to achieve for larger BP distributions. Therefore, we must take BP distribution into account in analysis. The relationship is insignificant in personalization. We suspect this is due to insufficient number of studies.

{% include scatter_std_err.html %}

<h3> How time between calibration and test varies with error </h3>

To determine whether the accuracy of the personalization changes over time, we regress the error on the time between calibration and test (∆t). For this, the time increments were binned into seconds (∆t=[0, 1)), minutes (∆t=[1, 2)), hours (∆t=[2, 3)), days (∆t=[3, 4)), and months (∆t=[4, 5)). Based on the number of intervals between each bin, we assign each ∆t to a value in the interval. For example, 2 weeks (14 days) will have a value of 3+14/30=3.47 because there are approximately 30 days in each month.

{% include scatter_time.html %}

There is no significant relationship between the accuracy of personalization studies and ∆t. However, it is interesting to note that visually, there is a faint increasing trend.

<h2> Supplementary: Power Analysis </h2>

Compute $$p=1-\beta=\phi(ES \sqrt{\frac{n}{2}}-z_{1-\alpha/2}))$$ where $$ES$$ (effect size) is given by error bias/error standard deviation=$$\frac{5}{8}$$, $$\alpha$$ is the selected level of significance, $$\beta=1-P$$, and $$\phi$$ is the cumulative distribution function of a normal distribution