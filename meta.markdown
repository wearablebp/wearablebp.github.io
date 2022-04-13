---
layout: page
title: Meta
permalink: /meta/
---

<h4> Summary Statistics </h4>
<div style="text-align: center"><img src="/images/summary.png" style="width: 100%; height: 100%"/></div> 
<br>

<h4> Dataset Level Analysis </h4>
<div style="text-align: center"><img src="/images/dla3.png" style="width: 100%; height: 100%"/></div>
<div style="text-align: center"><img src="/images/dla2.png" style="width: 100%; height: 100%"/></div>
<div style="text-align: center"><img src="/images/dla1.png" style="width: 100%; height: 100%"/></div>
<br>

<h4> Algorithmic Level Analysis </h4>
<div style="text-align: center"><img src="/images/ala1.png" style="width: 100%; height: 100%"/></div>
<div style="text-align: center"><img src="/images/ala2.png" style="width: 100%; height: 100%"/></div>
<br>

<h4> Device Level Analysis </h4>
<div style="text-align: center"><img src="/images/dela1.png" style="width: 100%; height: 100%"/></div>
<br>

<h4> Mechanisms linking Photoplethysmography measurements to Blood Pressure </h4>
<div style="text-align: center"><img src="/images/mechanism.png" style="width: 100%; height: 100%"/></div>

<br>
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

<h4> Calibration Techniques </h4>

| Calibration Technique | Description | Use case
| ----------- | ----------- | -----------
| Record level split without personalization | allow data leakage and use the same subjects in the training and testing sets | N/A
| Subject level split (population level calibration) | use different subjects in training and testing sets | When device accuracy does not wane over time and want to generalize across population of interest
| Personalization (individual level calibration) | Subset of record level split with a temporal constraint, in which training data is selected as the first portion of records and testing data is selected as the latter portion with no overlap. | No generalization across subjects. Device accuracy wanes over time due to physiological changes.