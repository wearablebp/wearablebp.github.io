---
layout: page
title: Key
permalink: /key/
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>


<h4> Performance Metric Equations </h4>

<b> See <a href="{{site.baseurl}}/meta/">Meta</a> for more info </b>

| Metric | Description |
|--------|------------|
| Explained Deviation ($$ED$$) | $$ ED = \frac{\sigma_{pop}}{\sigma_\epsilon}$$ for estimation error parameterized by ($$\mu_\epsilon, \sigma_\epsilon$$) on a population parameterized by ($$\mu_{pop}, \sigma_{pop}$$), where $$\mu$$ represents the mean and $$\sigma$$ represents the standard deviation |
| Margin of Error ($$MOE$$) | $$MOE=z_\alpha \frac{\sigma}{\sqrt{n}}$$ where $$\alpha$$ is the confidence level, $$z_\alpha$$ is the quantile, $$\sigma$$ is the standard deviation, and $$n$$ is the sample size |
| Power ($$P$$) | $$P=1-\beta=\phi(ES \sqrt{\frac{n}{2}}-z_{1-\alpha/2}))$$ where $$ES$$ (effect size) is given by error bias/error standard deviation=$$\frac{5}{8}$$, $$\alpha$$ is the selected level of significance, $$\beta=1-P$$, and $$\phi$$ is the cumulative distribution function of a normal distribution |

<h4> Extracted Data Key </h4>

{% include key_descriptions.md %}

<h4> Exclusion Reason Key </h4>

{% include exclude_key.md %}