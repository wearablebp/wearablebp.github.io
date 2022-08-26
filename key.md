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
| Explained Deviation ($$ED$$) | $$ED$$ is our proposed method presented in <a href="{{site.baseurl}}/meta/">Meta</a> to measure device performance.  It is computed as $$ ED = \frac{\sigma_{pop}}{\sigma_\epsilon}$$ and is parameterized by ($$\mu_\epsilon, \sigma_\epsilon$$) on a population parameterized by ($$\mu_{pop}, \sigma_{pop}$$), where $$\mu$$ represents the mean and $$\sigma$$ represents the standard deviation |
| Explained Deviation ($$ED$$) Confidence Interval | $$ED$$ confidence intervals are the $$1-\alpha$$ confidence intervals for $$ED$$. They can be computed using the F-distribution by determining the intervals at which $$P(\sqrt{F_{\alpha/2}(n-1, n-1)} ED_{est} < ED_{true} < \sqrt{F_{1-\alpha/2}(n-1, n-1)} ED_{est})  = 1-\alpha $$ where $$\alpha$$ is the level of significance, $$P$$ is the probability, $$F$$ is the F-distribution, $$ED_{est}$$ is the estimated Explained Deviation, and $$ED_{true}$$ is the true Explained Deviation. This can be dervied by considering: 1. $$n_1$$ in dependent observations from a normally distributed popoulation with variance $$\sigma_1^2$$ and 2. $$n_2$$ independent observations from a normall distributed population with variance $$\sigma_2^2$$. Then: <br> <br> Given sample variance $$s_1^2$$ and $$s_2^2$$, we can write $$\frac{(n_1 - 1)s_1^2}{\sigma_1} \sim \chi_{n_1-1}^2$$ and $$\frac{(n_2 - 1)s_2^2}{\sigma_2} \sim \chi_{n_2-1}^2$$ <br> The ratio of these two distributions is a F-distribution and can be written in the form $$F=\frac{s_1^2/\sigma_1^2}{s_2^2/\sigma_2^2}$$ <br> The $$1-\alpha$$ confidence interval can be written as $$P(F_{\alpha/2}(n_1-1, n_2-1) \lt \frac{s_1^2/\sigma_1^2}{s_2^2/\sigma_2^2} \lt F_{1-\alpha/2}(n_1-1, n_2-1)$$ <br> Simplying the expression, using the identity $$F_{1-\alpha/2}(n_1-1, n_2-1) = \frac{1}{F_{\alpha/2}(n_2-1, n_1-1)}$$, and substituting $$\frac{s_1}{s_2}=ED_{est}$$ and $$\frac{\sigma_1}{\sigma_2}=ED_{true}$$ gives $$P(\sqrt{F_{\alpha/2}(n-1, n-1)} ED_{est} < ED_{true} < \sqrt{F_{1-\alpha/2}(n-1, n-1)} ED_{est})  = 1-\alpha $$| 
| Power ($$p$$) | $$p=1-\beta=\phi(ES \sqrt{\frac{n}{2}}-z_{1-\alpha/2}))$$ where $$ES$$ (effect size) is given by error bias/error standard deviation=$$\frac{5}{8}$$, $$\alpha$$ is the selected level of significance, $$\beta=1-P$$, and $$\phi$$ is the cumulative distribution function of a normal distribution |

<h4> Extracted Data Key </h4>

{% include key_descriptions.md %}

<h4> Exclusion Reason Key </h4>

{% include exclude_key.md %}