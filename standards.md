---
layout: page
title: Standards
permalink: /standards/
---

| | [Universal Standard](https://journals.lww.com/jhypertension/Abstract/2018/03000/A_universal_standard_for_the_validation_of_blood.4.aspx) | [IEEE Standard](https://ieeexplore.ieee.org/document/6882122)
Procedure (Static) | 3 pairs of measurements for each subject | 3 pairs of measurements for each subject OR the mean of all beats over a 20 s period for beat-to-beat devices
| Procedure (Test with BP change from calibration point) | Not specified | Dataset must include SBP changes of: -30 to -15 (13.6%), -15 to 0 (34.1%), 0-15 (34.1%), 15-30 (13.6%), and DBP changes of: -20 to -10 (13.6%), -10 to 0 (34.1%), 0-10 (34.1%), 10-20 (13.6%) 
| Procedure (Test after certain period of time) | Not specified | Not specified
| Number of Subjects Required	| 85 | 20 (phase 1), 25 additional (phase 2)
| Demographics (healthy+diseased)	| adults study shall include ≥30% males and ≥30% females and shall have ≥5% of the reference systolic BP readings ≤100 mm Hg, ≥5% with ≥160 mmHg, and ≥20% with ≥140 mmHg and ≥5% of reference diastolic BP readings ≤60 mmHg, ≥5% with ≥100 mmHg, and ≥20% with ≥85 mmHg | equal distribution (5, ≥6) of healthy, Prehypertension, Stage 1 Hypertension and Stage 2 Hypertension. Equal number of male and female subjects (≥22). All subjects between 18 and 65 years old.
| Evaluation Metric | Mean Error ± Standard Deviation (mmHg) | Mean Absolute Error (mmHg)

<h4> Relationship between Evaluation Metrics </h4>
<div style="text-align: center"><img src="/images/evalstandards.png" style="width: 100%; height: 100%"/></div>
Assuming zero-mean gaussian distribution, a Mean Absolute Error of ≤5mmHg guarantees meeting the Universal Standard.

<br> 
<h4> Publicly Available Datasets vs Standards </h4>

| | [Universal Standard](https://journals.lww.com/jhypertension/Abstract/2018/03000/A_universal_standard_for_the_validation_of_blood.4.aspx) | [IEEE Standard](https://ieeexplore.ieee.org/document/6882122) | MIMIC Waveform Subset from [Kauchee et al., 2015](https://archive.ics.uci.edu/ml/datasets/Cuff-Less+Blood+Pressure+Estimation) | [University of Queensland Vital Signs Dataset](https://journals.lww.com/anesthesia-analgesia/Fulltext/2012/03000/University_of_Queensland_Vital_Signs_Dataset_.15.aspx) | [PPG-BP Dataset](https://www.nature.com/articles/sdata201820)
| Procedure (Static) | 3 pairs of measurements for each subject | 3 pairs of measurements for each subject OR the mean of all beats over a 20 s period for beat-to-beat devices | Continuous beat-to-beat BP from arterial line | Continuous beat-to-beat BP from arterial line | 3 pairs of measurements for each subject
| Procedure (Test with BP change from calibration point) | Not specified | Dataset must include SBP changes of: -30 to -15 (13.6%), -15 to 0 (34.1%), 0-15 (34.1%), 15-30 (13.6%), and DBP changes of: -20 to -10 (13.6%), -10 to 0 (34.1%), 0-10 (34.1%), 10-20 (13.6%) | Subset dependent| Subset dependent | None
| Procedure (Test after certain period of time) | Not specified | Not specified | Subset dependent | Subset dependent | None
| Number of Subjects Required | 85 | 20 (phase 1), 25 additional (phase 2) | | 32 | 219
| Demographics (healthy+diseased) | adults study shall include ≥30% males and ≥30% females and shall have ≥5% of the reference systolic BP readings ≤100 mm Hg, ≥5% with ≥160 mmHg, and ≥20% with ≥140 mmHg and ≥5% of reference diastolic BP readings ≤60 mmHg, ≥5% with ≥100 mmHg, and ≥20% with ≥85 mm Hg | equal distribution (5, ≥6) of healthy, Prehypertension, Stage 1 Hypertension and Stage 2 Hypertension. Equal number of male and female subjects (≥22). All subjects between 18 and 65 years old. | | | Subsets that meet Universal and IEEE Standards exist 