---
layout: page
title: Meta
permalink: /meta/
---

todo:
1. add studies to results section
2. review figure descriptions


[Paper Citation](https://www.nature.com/natbiomedeng/)

<h2> Motivation </h2>
In contrast to the traditional narrative review, we propose to summarize the findings of studies via a systematic review. Due to the large number of studies and the large variation in study datasets, protocols and results, a systematic review with a meta-analysis is warranted to qualify the best design considerations and areas for improvement. There has yet to exist a meta-analysis performed on PPG for BP estimation that analyzes the design considerations on a device, dataset, and algorithm level. Two similar systematic review with a narrower scope exists, however they do do not break down the different possible variations in methodology such as algorithm, calibration technique, and sensor data. In our systematic review, we aim to present a bigger picture of PPG-based non-invasive, continuous, and cuffless BP monitoring.

<h2> Protocol and Registration, Information Sources, and Search </h2>
“photoplethysmography”, “ppg”, and “blood pressure” were entered into the search tool Publish or Perish which retrieves and analyzes academic citations from external data sources, including Crossref, Google Scholar, Google Scholar Profile, Microsoft Academic, OpenAlex, PubMed, Scopus, Semantic Scholar and Web of Science. The Maximum number of results were specified as 1000 and the articles were specified in the time-frame of 1979-2022.
<h2> Study selection </h2>
The compiled database included studies reporting SBP and/or DBP errors for classification and/or regression metrics. Moreover, missing papers and whitepapers were included on a case-by-case basis. Some studies are published more than once. Duplicate publications were identified and reported only once.
Eligibility criteria: Studies published in the English language that use PPG (both single-site and multi-site approaches) for BP estimation that report mean error (ME) and standard deviation (STD), or mean absolute error in mmHg for Systolic Blood Pressure (SBP) and/or Diastolic Blood Pressure (DBP). No constraint on subject demographics or population statistics. 
Data Collection Process: Independent extraction of n=___ unique articles by a single author using predefined data fields. For studies that had multiple protocols and reported multiple results, the multiple entries were made in the compiled database. 
<h2> Data Items </h2> 
Information from each included approach (hardware/software, regression/classification), key devices and features (i.e. device=PPG, measurement = whole based features), calibration technique (record level split without personalization, subject level split, personalization, and some details), algorithm (i.e. physiological model using Moens– Korteweg equation, classical machine learning using decision trees, deep learning using convolutional neural networks), dataset(s), number of subjects, subject characteristics (i.e. ICU patients, healthy males), study characteristics (observational or interventional), evaluation metric (i.e. MAE, ME±STD, MSE, % accuracy), and reported numerical results. For studies that performed personalization, additional fields included number of calibrations, number of tests, time between calibration and test, time of test, time of calibration, time of test and errors. For studies that included both MAE and ME±STD, the ME±STD was recorded. If studies included multiple reported values for the same experimental setup, the smallest error was reported.
<h2> Risk of bias in individual studies </h2> 
Because one author summarized all studies, there could have been bias in extracting the results. To alleviate this bias and to reduce error, the studies were summarized twice.
<h2> Summary measures </h2> 
Since the Universal Standard uses ME±STD and the IEEE standard uses MAE, we choose to alleviate this discrepancy and by assuming gaussian statistics and converting summary measures reported as ME±STD (gaussian distribution) to MAE (folded normal distribution). The mean and confidence intervals are reported for each dimension. MAE is readily interpretable, scientifically meaningful and comparable among meta-analyses, and has known sampling distribution.


<h2> Results </h2>

Study selection: A total of N studies were identified for inclusion in this analysis. The search in N provided a total of N citations. After adjusting for duplicates, N remained. Of these N studies, N studies were discarded after reviewing abstracts because they did not meet the criteria or were review papers. The full text of the remaining N citations was examined in more detail. Additional N studies from the references and citations of relevant papers, and that satisfied the inclusion criteria were included. No unpublished relevant studies were obtained. Within the N studies that met the criteria, N studies reported ME±STD or MAE, and were subsequently used for statistical analysis.


(insert flow diagram)

<h4> Summary Statistics </h4>
<div style="text-align: center"><img src="/images/summary.png" style="width: 100%; height: 100%"/></div> 
(insert description)
<br>

<h4> Dataset Level Analysis </h4>

We found different calibration techniques for the physical level and algorithmic levels. In order to properly compare and contrast data, we must stratify by algorithmic level calibration technique, namely record level split without personalization, subject level split, personalization. Record level split without personalization involves having data in the training and testing set from the same subjects. For example, randomly sampled segments from a subject are included in both the training and test set. Unfortunately there are currently no useful applications for record level split without personalization. Subject level split, also referred to as population level calibration, involves using different subjects in the training and testing sets. For example, if 100 subjects are in the dataset, 50 subjects are used for training and the other 50 are used for testing. This is generally used when the device accuracy is assumed to not wane over time and the model can be generalized to the population of interest. Personalization, also referred to as individual level calibration, is a subset of record level splitting. This involves performing record level split with a temporal constraint, in which the training data is selected as the first portion of records and the testing data is selected as the latter portion of the record without overlap with the training data. For example, if a record for a single subject is 1 month long, data from the first day is used for training and the rest is used for testing. This is used when the model does not have generalization ability across the population of interest, so an individual level model is fitted and usually recalibrated at arbitrary intervals due to physiological changes that may render the model inaccurate.

| Calibration Technique | Description | Use case
| ----------- | ----------- | -----------
| Record level split without personalization | allow data leakage and use the same subjects in the training and testing sets | N/A
| Subject level split (population level calibration) | use different subjects in training and testing sets | When device accuracy does not wane over time and want to generalize across population of interest
| Personalization (individual level calibration) | Subset of record level split with a temporal constraint, in which training data is selected as the first portion of records and testing data is selected as the latter portion with no overlap. | No generalization across subjects. Device accuracy wanes over time due to physiological changes.

The subjects in the datasets were classified into diseased and healthy, where diseased indicates subjects with medical conditions or undergoing medical treatment (i.e. hypertensive, ICU patients, surgical patients) and healthy indicates subjects without reported disease. This distinction needs to be made because there may be larger variation in physiologies between diseased subjects and across time for individual subjects.

<div style="text-align: center"><img src="/images/dla3.png" style="width: 100%; height: 100%"/></div>


<i> What is the distribution of internal databases? What subject characteristics are included in Internal Datasets? What is the expected size? </i>

The unique datasets used are internal, MIMIC, PPG-BP, UoQ. Internal datasets are composed of healthy, diseased and health+diseased subjects. The internal datasets are generally magnitudes smaller than the publicly available datasets, with the maximum size in the 1000s. Largest internal dataset was collected by Xing et al., from the local community and hospital. Evaluated in subjects with various age, height, weight and BP levels (n = 1249). In the young population (<50 years old) with low, medium and high systolic blood pressures (SBP, <120 mmHg; 120–139 mmHg; ≥140 mmHg).

<i> What are the various different datasets and their characteristics? What are the expected sizes of various publicly available datasets? Does everyone use the full dataset for publicaly available datasets? If not, how do they decide the subset? What are the BP distributions of the full public datasets? How do the different publicly available datasets compare to internal datasets?</i>

The largest dataset (by far) is from the MIMIC-III Waveform Database, which includes waveforms of approximtely 30000 ICU patients collected in an automated fashion. The BP data were collected continuously via invasive catheters (ABP waveform). However, as MIMIC is not a specific BP estimation database, not all these waveforms include the desired waveforms. Therefore, studies select a subset of records, decided in mostly arbitrary ways, including hand-picking records and performing signal quality evaluations. The most common MIMIC dataset used is from Kauchee et al., 2015, which consists of 12000 cleaned and filtered records. MIMIC and UoQ consist of diseased subjects, specifically UoQ has ECG, PPG and ABP waveform for 32 surgical patients and PPG-BP has 2.1s PPG waveforms and BP cuff measurements for both healthy and diseased subjects that have various forms of cardiovascular disease and diabetes, including hypertension.

<div style="text-align: center"><img src="/images/dla2.png" style="width: 100%; height: 100%"/></div>

<i> What is the distribution of subject characteristics for each calibration technique? </i>

Record level split without personalization and subject level split datasets are generally well distributed around 10s to 1000s range. But for personalization, the datasets are generally in the range of 10s, internal, and mostly healthy subjects. On the other hand, larger datasets are generally composed of diseased subjects. Moreover, hospital datasets with ground truth as catheterization may not lend itself well to personalization studies, as parts of the records may be missing (due to device detachment) and time between measurements may be irregular and short, as the measurement periods and intervals are not standardized. 

<div style="text-align: center"><img src="/images/dla1.png" style="width: 100%; height: 100%"/></div>

<i> How do the accuracies of using different subject characteristics and different calibration techniques compare? What is the most corroborated calibration technique and subject demographic? </i>

Clear that record level split without personalization is better than subject level split for healthy and for diseased subjects, but different for health+diseased subjects, possibly to do with low number of studies corroborating this datapoint. Subject Level Split performs the worst. Specifically, diseased subjects have much higher error compared to healthy subjects. This is may be due to the large biological variation in physiologies between subjects. Both of these subject characteristics do not lead to MAEs lower than 5mmHg. On the other hand, combining healthy and diseased datasets for subject level split lead to higher accuracies, albeit low number of studies. This may be due to the larger variety of physiologies that were used to train the models and therefore better generalizability. This is typically done in a transfer-learning framework, specifically by training the models on a large public dataset and fine-tuning the models on an internally collected dataset. This framework also allows to bypass the limitations of overfitting on a small internal dataset. In particular, (Hill et al., 2021).

Moreover, for healthy subjects, personalization achieved similar results compared to record level split without personalization. This is expected, as personalization is a subset of record level split (with a temporal constraint). Similar to subject level split, in personalization, datasets with diseased subjects perform worse, and may be due to the larger temporal differences within subjects. Finally, the reason for poor performance for personalization in healthy+diseased subjects is unknown, though there is small number of studies.

<br>

<h4> Algorithmic Level Analysis </h4>
<div style="text-align: center"><img src="/images/ala1.png" style="width: 100%; height: 100%"/></div>
<i> How do various calibration techniques compare in terms of accuracy? </i>

In terms of different calibration techniques, on average, record level split without personalization performs the best and subject level split performs worse than personalization. This makes sense because record level split allows for data leakage and personalization allows for some data leakage but in a temporally contrained manner.

<i> What algorithm configuration show potential to satisfy standards? </i>

For record level split without personalization, deep learning performs the best and has been the most investigated. This is may be because neural networks have a higher capacity to memorize data. For subject level split and personalization, we see that physiological models perform the best. Therefore, it is clear that the features extracted by classical ML and deep learning are not as telling as our understanding of physiology. Finally, the only useful technique that falls under 5mmHg for both SBP and DBP is using personalization and a physiological model. 

<div style="text-align: center"><img src="/images/ala2.png" style="width: 100%; height: 100%"/></div>

<i> Is there a relationship between time between calibration and test and accuracy? How do different subject characteristics affect personalization accuracy over time? </i>

There is a moderate positive relationship between the mean absolute error and the time between calibration and test on a logarithmic temporal scale for both systolic and diastolic blood pressure for datasets that consist of healthy subjects. However, such relationship is inconclusive for datasets with diseased subjects and health+diseased subjects, mainly due to the lack of data points.

<i> What are subject demographics for studies that show personalization for months? Are these verifiable? </i>

For personalized studies that span weeks to months, the datasets only consist of healthy subjects and are all internal. More efforts need to be placed into collecting personalized datasets and of subjects with diverse medical backgrounds.

<i> How long before error goes beyond standards? </i>

Based on the best fit line of MAE for SBP and DBP for healthy subjects, the errors exceed 5mmHg in days and months respectively. This is expected because, in general, reported DBP estimation errors are smaller due to the smaller absolute value of DBPs. The accuracy of the calibration depends on Blood Pressure Variability, which is highly temporally dependent based on physiology, time of day, and time of year. Therefore, instead reporting absolute BP errors, it is important to report the accuracy for change in BP. Some datasets have subjects with small BP changes and therefore report small BP errors.

<br>

<h4> Device Level Analysis </h4>
<div style="text-align: center"><img src="/images/dela1.png" style="width: 100%; height: 100%"/></div>
<br>

<h4> Mechanisms linking Photoplethysmography measurements to Blood Pressure </h4>
<div style="text-align: center"><img src="/images/mechanism.png" style="width: 100%; height: 100%"/></div>

<br>


<h4> Discussion </h4>

<h6> Blood Pressure and Blood Pressure Change Distribution </h6>

For internal datasets that have undisclosed BP distribution statistics and for personalization datasets that have undisclosed BP change statistics, a small variation in BP variations across subjects (for subject level split) and within subjects (for personalization) may lead to deceiving results. Ideally, a regression analysis on the error vs ground truth plot should yield slope=0, meaning there is no difference in prediction error in subject levels split or in personalization (between big BP change and small BP change). On the other hand, a slope closer to -1 means high prediction error for larger values and small prediction error for smaller values. However, there are many studies that do not report these. 

Adversarial examples may allow studies to meet the evaluation metrics specified by the Universal and IEEE Standards. For example, if the dataset distribution has a mean SBP of 120mmHg and a standard deviation of 8mmHg and the estimator consistently predicts 120mmHg, the estimator will meet the Universal Standard.

<h7> Experiments </h7>>

To investigate if this phenomenon still exists with a dataset distribution that meets the Universal Standards, we constructed a real life dataset from PPG-BP that meets the general population distribution specified in the standards and performed the same experiment. After meeting the general population criteria, the constant estimator yielded a minimum STD of 18mmHg and a MAE of 21mmHg. 

Similarly, to investigate whether this phenomenon exists in a publicly available dataset for personalization, we performed a personalization experiment with the MIMIC-II dataset provided by Kauchee et al. and using Pulse Arrival Time (PAT) to estimate SBP. Specifically, we use a subset of 100 subjects and perform a 200s calibration using a linear regression for points in the calibration segment to estimate SBP on a beat-beat level in the test segment.

<div style="text-align: center"><img src="/images/delta_bp.png" style="width: 100%; height: 100%"/></div>

From fig , we can see that in an observational experiment, the change in BP is small. Furthermore, from Fig, we observe that the average MAE was 3.35mmHg, which comfortably satisfies all standards. However, the MAE distribution across different changes in BP demonstrates a significantly higher error for larger changes and low error for values closer to zero change. This is a result of data imbalance towards a change in BP of zero. If we apply inverse probability weighting to weight each BP change equally, the MAE increases to 13mmHg. From this experiment, we see that it is imperative to demonstrate accuracy for a wide range of BP changes.


<h4> Meta-Analysis Dataset</h4>
A summarized table of studies. [Download Dataset](https://docs.google.com/spreadsheets/d/e/2PACX-1vTo1QIHqqKwKTCgCUDeA-4ihiCVt9sAVi2nUnUhXJqH6L8BmleY_RY-1GQcnv981fDb-Tv_vubDpg4B/pub?gid=2123644980&single=true&output=csv)
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vTo1QIHqqKwKTCgCUDeA-4ihiCVt9sAVi2nUnUhXJqH6L8BmleY_RY-1GQcnv981fDb-Tv_vubDpg4B/pubhtml?gid=2123644980&amp;single=true&amp;headers=false"  frameborder="0" scrolling="no" seamless="seamless" style="display:block; width:100%; height:50vh;"></iframe>


<h4> Extracted Parameters </h4>

Parameter | Description
---------- | ---------
Problem | Regression or Classification problem. Novelty in software or hardware or software+hardware
Key Devices and Measurements | Sensor Data (i.e. PPG, ECG+PPG) and some features
Calibration Technique | Record Split without personalization or Subject Level Split or Personalization (see table below)
Algorithm | Deep Learning: models that involve using neural networks (i.e. CNN, LSTM, Transformers) <br> Classical ML: models that involve using hand-crafted features (i.e. heart rate, pulse-transit time, entropy) and classical mathematical algorithms (i.e. linear regression, decision trees) <br> Physiological Model: models that involve using physiologically derived equations (i.e. Moens–Korteweg equation)
Dataset | Name of dataset; ground truth device; other 
Number of Subjects | Number of Subjects used in both training and testing
Subject Characteristics | healthy: no disclosed health conditions <br> diseased: subjects with medical conditions, including hypertensive subjects, ICU patients and surgical patients
Evaluation Metric | Reported evaluation metric (i.e. Mean Absolute Error (MAE), Mean Error ± Standard Deviation (ME±STD), regression coefficient (r))
Reported Result | Numerical result
Number of calibrations | Number of calibrations performed for each subject
Number of tests | Number of tests performed on each subject after calibration
Time between Calibration and Test | Time between calibration time and test time: s=seconds, m=minutes, h=hours, mon=months
Time of Calibration | Calibration segment length for each subject: s=seconds, m=minutes, h=hours, mon=months
Time of Test | Testing segment length for each subject: s=seconds, m=minutes, h=hours, mon=months