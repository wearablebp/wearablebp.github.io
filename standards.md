---
layout: page
title: Standards
permalink: /standards/
---

<h2> (in progress) </h2>

<h2> Comparison between AAMI/ANSI/ISO Standard and IEEE Standard </h2>

| | [AAMI/ANSI/ISO Standard](https://journals.lww.com/jhypertension/Abstract/2018/03000/A_AAMI/ANSI/ISO_standard_for_the_validation_of_blood.4.aspx) | [IEEE Standard](https://ieeexplore.ieee.org/document/6882122)
Procedure (Static) | 3 pairs of measurements for each subject | 3 pairs of measurements for each subject OR the mean of all beats over a 20 s period for beat-to-beat devices
| Procedure (Test with BP change from calibration point) | Not specified | Dataset must include SBP changes of: -30 to -15 (13.6%), -15 to 0 (34.1%), 0-15 (34.1%), 15-30 (13.6%), and DBP changes of: -20 to -10 (13.6%), -10 to 0 (34.1%), 0-10 (34.1%), 10-20 (13.6%) 
| Procedure (Test after certain period of time) | Not specified | Not specified
| Number of Subjects Required	| 85 | 20 (phase 1), 25 additional (phase 2)
| Demographics (healthy+diseased)	| adults study shall include ≥30% males and ≥30% females and shall have ≥5% of the reference systolic BP readings ≤100 mm Hg, ≥5% with ≥160 mmHg, and ≥20% with ≥140 mmHg and ≥5% of reference diastolic BP readings ≤60 mmHg, ≥5% with ≥100 mmHg, and ≥20% with ≥85 mmHg | equal distribution (5, ≥6) of healthy, Prehypertension, Stage 1 Hypertension and Stage 2 Hypertension. Equal number of male and female subjects (≥22). All subjects between 18 and 65 years old.
| Evaluation Metric | Mean Error ± Standard Deviation (mmHg) | Mean Absolute Error (mmHg)

<h2> Relationship between Evaluation Metrics </h2>
To determine the relationship between AAMI/ANSI/ISO and IEEE Standards, we generate a 2D heatmap of Mean Difference versus Standard Deviation with shades of gray representing the mean absolute error, and the upper bound of IEEE grades represented in different colors.
<div style="text-align: center"><img src="/images/evalstandards.png" style="width: 100%; height: 100%"/></div>
Assuming zero-mean gaussian distribution, a Mean Absolute Error of ≤5mmHg guarantees meeting the AAMI/ANSI/ISO Standard.

<br> 
<h2> Publicly Available Datasets vs Standards </h2>

| | [AAMI/ANSI/ISO Standard](https://journals.lww.com/jhypertension/Abstract/2018/03000/A_AAMI/ANSI/ISO_standard_for_the_validation_of_blood.4.aspx) | [IEEE Standard](https://ieeexplore.ieee.org/document/6882122) | MIMIC Waveform Subset from [Kauchee et al., 2015](https://archive.ics.uci.edu/ml/datasets/Cuff-Less+Blood+Pressure+Estimation) | [University of Queensland Vital Signs Dataset](https://journals.lww.com/anesthesia-analgesia/Fulltext/2012/03000/University_of_Queensland_Vital_Signs_Dataset_.15.aspx) | [PPG-BP Dataset](https://www.nature.com/articles/sdata201820)
| Procedure (Static) | 3 pairs of measurements for each subject | 3 pairs of measurements for each subject OR the mean of all beats over a 20 s period for beat-to-beat devices | Continuous beat-to-beat BP from arterial line | Continuous beat-to-beat BP from arterial line | 3 pairs of measurements for each subject
| Procedure (Test with BP change from calibration point) | Not specified | Dataset must include SBP changes of: -30 to -15 (13.6%), -15 to 0 (34.1%), 0-15 (34.1%), 15-30 (13.6%), and DBP changes of: -20 to -10 (13.6%), -10 to 0 (34.1%), 0-10 (34.1%), 10-20 (13.6%) | Subset dependent| Subset dependent | None
| Procedure (Test after certain period of time) | Not specified | Not specified | Subset dependent | Subset dependent | None
| Number of Subjects Required | 85 | 20 (phase 1), 25 additional (phase 2) | | 32 | 219
| Demographics (healthy+diseased) | adults study shall include ≥30% males and ≥30% females and shall have ≥5% of the reference systolic BP readings ≤100 mm Hg, ≥5% with ≥160 mmHg, and ≥20% with ≥140 mmHg and ≥5% of reference diastolic BP readings ≤60 mmHg, ≥5% with ≥100 mmHg, and ≥20% with ≥85 mm Hg | equal distribution (5, ≥6) of healthy, Prehypertension, Stage 1 Hypertension and Stage 2 Hypertension. Equal number of male and female subjects (≥22). All subjects between 18 and 65 years old. | | | Subsets that meet AAMI/ANSI/ISO and IEEE Standards exist 


<h2> Estimating required Explained Deviation from AAMI/ANSI/ISO Standards </h2>
To estimate the ED that satisfies the AAMI/ANSI/ISO Standards, we use the PPG-BP dataset. The AAMI/ANSI/ISO Standard specifies that a device that for the general population should:

* Have n=85 subjects, should include ≥30% males and ≥30% females
* Have ≥5% of the reference SBP readings ≤100 mm Hg, ≥5% with ≥160 mmHg, and ≥20% with ≥140 mmHg
* Have ≥5% of reference DBP readings ≤60 mmHg, ≥5% with ≥100 mmHg, and ≥20% with ≥85 mm Hg

Currently, there are no publicly available datasets that satisfy these demographics. However, the PPG-BP satisfies the requirements if subsampled. To determine a subsample that satisfied the AAMI/ANSI/ISO Standards, we performed weighted sampling of subjects, where the weights were determined using Iterative Proportional Fitting (IPF) marginalized on the requirements. We repeat this process 1000 times and determine the minimum variance of the subsampled datasets. Then, we took the maximum standard deviation allowed by [4], 8mmHg, and computed the ED explained in <a href="{{site.baseurl}}/meta/">Meta</a>. This yielded a required SBP and DBP standard deviation of at least 19.34 mmHg and 11.67 mmHg respectively. The minimum ED for SBP and DBP was computed to be 2.42 and 1.46. The implementation can be found at ____.

<!-- <h2> 95% Confidence Intervals for AAMI/ANSI/ISO Standards </h2> -->
