---
layout: page
title: Meta
permalink: /meta/
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

<br>




<h2> Method </h2>

<h4> Protocol and Registration, Information Sources, and Search </h4>
Keywords "wearable", "blood pressure", "monitoring", "estimation", "systolic", "diastolic", and "cuffless" were entered into the search tool [Publish or Perish](https://harzing.com/resources/publish-or-perish) on 5/10/2022 which retrieves and analyzes academic citations from external data sources, including Crossref, Google Scholar, PubMed, Scopus, and Semantic Scholar. The Maximum number of results were specified as 1000 and the articles were specified in the time-frame of 1979-2022. Additional studies were included from Google Scholar alerts of "blood pressure device" and from article references.

<h4> Eligibility Criteria </h4>
We develop an Eligibility Criteria to determine whether studies should be included or excluded from analysis. First, we include studies that report mean absolute error (MAE) or bias±standard deviation of error (ME) for Systolic and Diastolic Blood Pressure estimation. The AAMI/ANSI/ISO, BHS, and IEEE Standards all require either ME or MAE. Moreover, we can compute ME to MAE and vice versa (assuming zero bias) through a folded normal distribution. Second, we require the article to be written in the English language. Third, we only include studies that do not suffer from data leakage. In order to properly compare and contrast data, we must stratify by algorithmic level calibration technique. We coin the terms "record level split without personalization", "subject level split", and "personalization" to distinguish between calibration techniques. Record level split without personalization involves having data in the training and testing set from the same subjects, therefore suffering from data leakage. For example, randomly sampled segments from a subject are included in both the training and test set. Unfortunately there are currently no useful applications for the record level split without personalization calibration technique. On the other hand, Subject level split, which can be thought of as "population level calibration", involves using different subjects in the training and testing sets. For example, if 100 subjects are in the dataset, 50 subjects are used for training the model and the other 50 are used for testing the model. In contrast, personalization, which can be thought of as "individual level calibration", is a subset of record level split. This involves performing record level split with a temporal constraint, in which the training data is selected as the first portion of records and the testing data is selected as the latter portion of the record without overlap with the training data. For example, if a record for a single subject is 1 month long, data from the first day is used for training and the rest is used for testing. This individual level model is usually recalibrated at arbitrary intervals due to physiological changes that may render the model inaccurate. We only include articles that claim to perform subject level split or personalization. Fourth, we exclude models that dynamically update based on individual subjects and their time stamps. Fifth, we only include studies that perform experiments on human subjects, as we aim to deploy these devices on humans. Finally, we only include studies that have number of test subjects greater than 1 due to inability to compute blood pressure distributions of subject population. For studies that are not included, we provide a exclusion reason.

<h4> Data Collection Process and Data Items </h4>

A single author performed extraction of predefined data parameters. For studies that had multiple protocols and reported multiple results, the multiple entries were made in the compiled database. The predefined data fields include: Key Devices and Measurements, Calibration Technique, Algorithm,	Dataset, Number of Test Subjects, Training Subject Characteristics, Testing Subject Characteristics, Study Characteristics (observational or interventional study), BP Distribution, Evaluation Metric, and Reported Result. For personalization articles, we report the Time between Calibration and Test. To estimate the SBP and DBP population standard deviation when the BP distribution was not provided in the code, we used (if available) figures that had an axis with Reference SBP or DBP values, specifically correlation plots (Reference vs Estimated) and error plots (Reference vs Error). On the other hand, a Bland-Altman plot is not appropriate because the x-axis is the Average of the reference and estimated. Using these figures, we isolated the red, green or blue channels depending on the colors of the points of interest. Then, we sum the values along the non-reference axis, normalized them to attain a probability distribution function, fit a gaussian curve, and take the mean and standard deviation. The mean and standard deviation were reported as the BP distribution statistic. The implementation can be found at ____. Finally, for studies that were included in our meta-analysis, we report the implementation availability and the dataset availability. For a description of parameters and their values, refer to <a href="{{site.baseurl}}/key/">Key</a>. Note: Because one author summarized all studies, there could have been bias in extracting the results.

<h4> Summary Statistics </h4>

We propose a new estimate to evaluate estimation accuracy for studies that perform subject level split, Explained Deviation ($$ED$$), used to compute the effectiveness of a device with estimation error parameterized by ($$\mu_\epsilon, \sigma_\epsilon$$) on a population parameterized by ($$\mu_{pop}, \sigma_{pop}$$), where $$\mu$$ represents the mean and $$\sigma$$ represents the standard deviation. The ED can be computed as $$ ED = \frac{\sigma_{pop}}{\sigma_\epsilon}$$. The higher the EV, the better the device performs. On the other hand, an ED of 1 indicates that the estimator performs no better than an estimator that predicts a constant value. 

Using the same formulation, we compute $$ED$$ for personalization. However, in this case, we must take the change in BP of each subject into account: $$ED = \frac{\sigma_{\Delta BP, err}}{\sigma_{\Delta BP}}$$, where $$\sigma_{\Delta BP, err}$$ is the change in BP prediction error of the study cohort and $$\sigma_{\Delta BP}$$ is the standard deviation of the BP changes of the study cohort.

Moreover, we compute the 95% Margin of Error ($$E_{95}$$) and power ($$P$$) to determine the uncertainty of the reported result. To do this we need to define selected level of significance, $$\alpha$$, and $$\beta=1-P$$. The ANSI/AAMI/ISO 81060-2 requires device error to have an absolute mean and standard deviation within 5±8mmHg with $$\alpha=0.05$$ and $$\beta=0.02$$, corresponding to $$P$$=0.98 and a sample size of 83. To compute this, they consider a two independent sample and continuous outcome study. The minimum sample size for a given $$\alpha$$ and $$\beta$$ is: $$n=2(\frac{z_{1-\alpha/2}+z_{1-\beta}}{ES})^2$$ where $$ES$$ is the effect size, $$z_{1-\alpha/2}$$ is the z-score at $$1-\alpha/2$$. Assuming $$ES=\frac{5}{8}$$, the minimum number of subjects for $$\alpha=0.05$$ and $$P=1-\beta=0.98$$ is 83. Conversely, the power of a study can be computed as $$P=1-\beta=\phi(ES \sqrt{\frac{n}{2}}-z_{1-\alpha/2}))$$ where $$ES$$ (effect size) is given by error bias/error standard deviation $$ES=\frac{5}{8}$$, and $$\phi$$ is the cumulative distribution function of a normal distribution. In this case, the null hypothesis ($$H_0$$) is that the device has a mean difference and standard deviation of error above 5mmHg and 8mmHg. If the power is 0.98, that means that the probability of rejecting the $$H_0$$ given the alternative hypothesis is true is greater than 98%.

<h2> Results </h2>

<h4> Study selection </h4> 
We identified a total of 2510 articles from our database search and 29 articles from other sources. For inclusion in this analysis. After adjusting for duplicates by code, 2177 remained remained. We inspected the full articles and excluded 2007 unique articles and 36 additional studies (from articles that report multiple studies) based on the inclusion criteria. Likewise, we included 174 unique articles and 68 additional studies. From the 242 studies, we determined 94 studies performed subject level split and 148 studies performed personalization. Upon further examination, we identified the (change in) BP distribution of 61 and 16 studies for subject level split and personalization respecitvely. Ultimately, we included 77 studies in the meta-analysis. We provide a flow chart and statistics for extracted parameters in Fig. and Fig. respectively. See <a href="{{site.baseurl}}/search/">Search</a> for a complete list of studies and extracted parameters.

<br>
<div style="text-align: center"><img src="/images/graphviz.png" style="width: 100%"/></div>
<br>
<center> <i> Fig . . Summary of the review process. N indicates the number of records and n indicates the number of studies. Some articles report multiple studies. </i> </center>
<br>

{% include metadata_stats.html %}

<center> <i> Fig. . Extracted parameter statistics of meta-analysis included studies. Using the tabs above allows to switch between different extracted parameter distributions. Moreover, for categorical statistics, hovering over the bars shows the number of entries and percentage composition of subject level split and personalization studies. See <a href="{{site.baseurl}}/key/">Key</a> for a description of extracted parameters. </i> </center> <br>

From Fig. ,for sensor data, we observe that the most common sensor data configuration used for BP estimation is photoplethysmography and photoplethysmography with electrocardiography. For algorithm, we observe that the most common class of algorithm used is classical machine learning, often in conjuntion with hand-crafted features. For subject characteristics, overall, we observe that there is a similar split between using healthy, diseased and a mix of healthy and diseased subjects in the study. However, it is notable that there were significantly less studies that used diseased subjects for personalization. For datasets used, we observe that an overwheming number of studies used databases collected internally that are not avaialble for the public and the most common publically available database used is Medical Information Mart for Intensive Care (MIMIC). For study characteristics, we observe that the majority of subject level split studies were observational. On the other hand, we observe that the personalization studies were split similarly between observational and interventional studies. For the quantitative metrics, notably, the standard devation of the BP distribution for SBP is larger than that for DBP and the standard deviation of the BP distribution of subject level split studies is greater than that of personalization studies.

<h2> Meta-Analysis </h2>

Using our proposed metric to evaluate estimation accuracy, we plot the ED of SBP versus ED of DBP for subject level split and personalization studies. We indicate the size of points using the power of the study and also report important study information using a hover tool. Moreover, we delineate in green the minimum ED computed from the AAMI/ANSI/ISO Standards for SBP and DBP, which were 2.42 and 1.46 respectively. See <a href="{{site.baseurl}}/standards/">Standards</a> for more information about the calculation. <br> <br>

{% include scatter.html %} <br> 
<center> <i> Fig. . A scatter plot of Explained Deviation for SBP versus Explained Deviation for DBP color coded by sensor device configuration. The size represent the power of the study. The tabs above allow to switch between Calibration Technique (subject level split or personalization). Hovering over the scatter points displays important parameter information related to the study. Clicking the legend allows to show or hide particular sensor data configurations. Finally, panning, zooming, tapping, resetting, and hovering tools are included on the right hand side of the legend. See <a href="{{site.baseurl}}/key/">Key</a> for a description of extracted parameters. </i> </center> <br>

We observe that there are 20 subject level split studies and 4 personalization studies that exceed the minimum determined ED.

{% include metadata_stats_meetspecs.html %}


<h4> Insight 1: Longitudinal personalization studies without sufficient BP variation demonstrate device estimation acccuracy no more than stable BP over test period </h4>

It is notable that less than 10% of the personalization studies include information about the change in BP distribution. Even though there are studies that report the initial BP distribution of subjects, this is not sufficient, as some experiments do not allow sufficient variation in BP. As a consequence, allowing the intial calibrated BP values to be the estimator can lead to small errors. In a similar vein, the number of observational studies and interventional type studies for personalization studies were almost equal. However, observational studies may not allow sufficient BP variation, leading to lower ED. Due to the lack of longitudinal personalization studies that have high ED, we suspect that longitudinal studies demonstrate device estimation accuracy no more than stable BP over the test period. 

<h4> Insight 2: Pulse Arrival Time is not a strong indicator of BP change </h4>

Pulse Arrival Time (PAT) and Pulse Transit Time (PTT) are considered considered as well-established features, yet there are no studies that demonstrate an ED that are greater or equal to the computed ED of the requirements. In fact, all of the PAT/PTT studies cluster around the 1, with some that are below the error boundaries established by the standards. 


{% include patptt_scatter.html %}





