---
layout: page
title: Systematic Review Method
permalink: /methods/
nav_order: 7
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

<div style="text-align: left"><img src="/images/systematic.png" style="width: 35%"/></div>
<i> Summary of the review process. N indicates the number of records and n indicates the number of studies. Some articles report multiple studies. </i>

To improve transparency of our analysis, we provide detailed information about the systematic review process. See the Wearable BP on [GitHub](https://github.com/wearablebp/) for code to reproduce Systematic Review results and visuals. To access the raw data used in our systematic review, please fill out this [form](https://forms.gle/3g2yTkPNVmJFB2it6).

<h2> Protocol and Registration, Information Sources, and Search </h2>
Keywords "wearable", "blood pressure", "monitoring", "estimation", "systolic", "diastolic", and "cuffless" were entered into the search tool [Publish or Perish](https://harzing.com/resources/publish-or-perish) on 5/10/2022 which retrieves and analyzes academic citations from external data sources, including Crossref, Google Scholar, PubMed, Scopus, and Semantic Scholar. The Maximum number of results was specified as 1000 and the articles were specified in the time frame of 1979-2022. Additional studies were included from Google Scholar alerts of "blood pressure device" and from article references.

<h2> Eligibility Criteria </h2>
1. Report a mean absolute error (MAE) or mean difference ± standard deviation of the error (ME) for SBP and DBP estimation
2. Are written in the English language
3. Claim to perform subject split or personalization
4. Do not temporally update models
5. Perform experiments on human subjects
6. Have number of test subjects greater than 1

<h2> Data Collection Process and Data Items </h2>

A single author performed an extraction of predefined data parameters. For studies that had multiple protocols and reported multiple results, multiple entries were made in the compiled database. The predefined data fields include: Key Devices and Measurements, Calibration Technique, Algorithm,	Dataset, Number of Test Subjects, Training Subject Characteristics, Testing Subject Characteristics, Study Characteristics (observational or interventional study), BP Distribution, Evaluation Metric, and Reported Result. For personalization articles, we report the Time between Calibration and Test. To estimate the SBP and DBP population standard deviation when the BP distribution was not provided in the code, we used (if available) figures that had an axis with Reference SBP or DBP values, specifically correlation plots (Reference vs Estimated) and error plots (Reference vs Error). The implementation can be found on [GitHub](https://github.com/wearablebp). Finally, for studies that were included in the analysis, we report the implementation availability and the dataset availability.

<h2> Study selection </h2> 
We identified a total of 2510 articles from our database search and 29 articles from other sources. For inclusion in this analysis. After adjusting for duplicates by code, 2180 remained. We inspected the full articles and excluded 2008 articles based on the inclusion criteria. Likewise, we included 173 unique articles and 67 additional studies (from articles that report multiple studies). From the 239 studies, we determined that 92 studies performed subject-level split and 147 studies performed personalization. Upon further examination, we identified the (change in) BP distribution of 59 and 10 studies for subject split and personalization respectively. Ultimately, we included 69 studies in the meta-analysis.

