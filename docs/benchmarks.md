---
layout: page
title: Benchmarks
permalink: /benchmarks/
nav_order: 4
---

{% include replicated_ed_scatter.html %}

<h2> Open Contribution Benchmarking </h2>

It is important for a study to have reproducible results so the algorithms can be tested on other datasets for validity. Not only do these algorithms include estimation models, but they also include the data filtering algorithms that may shift the training and testing set distributions. We benchmark the data filtering algorithms and model combinations on publically available datasets. The implementation was done based on the code provided (on GitHub) and/or the details of the algorithms presented in the paper.

Moreover, reproducibility is not only limited to software. Some studies involve using unconventional sensors. Although developing new devices is important for exploratory research, these devices are not verifiable by an external party. In addition to transparent hardware, there needs to be more transparency in experimental protocols. For example, the contact pressure is known to affect waveform morphology. Since feature extraction techniques rely on waveform morphology to detect key points, devices used in one study may not yield the same results without standardization of experimental protocols. Some studies may use a PPG sensor with a different spring constant.

To tackle this, we referee a a table of benchmarks for wearable BP montoring and provide a machine learning pipeline for BP estimation. A diagram of the pipline is shown below in Fig. .

{% include benchmark_diagram.svg %}

Every benchmark that will be reported here will follow strict guidelines on sharing code and reporting results. We provide an update form for researchers to improve upon existing benchmarks and add new benchmarks. Finally, the benchmarks currently only cover ECG and PPG. However, as wearable sensors become cheaper and more ubiquitous, the benchmarks will be expanded to include them.