---
layout: default
header-includes:
  - \usepackage[ruled,vlined,linesnumbered]{algorithm2e}
---

*   **Principle investigator:** Sinan Yıldırım, Sabanci University
*   **Graduate researcher:** Baris Alparslan, Sabanci University
*   **Contributor:** Ilker Birbil, University of Amsterdam
*   **Project Type:** TUBITAK 3501
*   **People:**  [See people working on the project](./another-page.html).

### Research output 

*   **(1) Published:** Alparslan B., Yıldırım S., Statistic Selection and MCMC for Differentially Private Bayesian Estimation, Statistics and Computing, 2022
*   **(2) Submitted:** Yıldırım S. Differentially Private Online Bayesian Estimation with Adaptive Truncation, submitted to Turkish Journal of Electrical and Computer Sciences, 2023
*   **(3) Submitted:** Alparslan B., Yıldırım S., Birbil, S.I. , Differentially Private Distributed Bayesian Linear Regression with MCMC, submitted to International Conference on Machine Learning (ICML) 2023

## Summary of (1)

> **Title:** Statistic Selection and MCMC for Differentially Private Bayesian Estimation
>
> **Publication link:** https://doi.org/10.1007/s11222-022-10129-8
> 
> **Pre-print**: https://arxiv.org/abs/2203.13377
>
> Keywords: Differential privacy, Markov chain Monte Carlo, Fisher information, statistic selection; Bayesian statistics.

### Main contributions of the published paper

* Statistic selection based on Fisher Information.
* Sampling from the true posterior based on the noisy statistic (Bayesian Inference using MCMC).

This work mainly addresses two problems: (1) What statistic of the sample should be shared privately? For the first question, i.e., the one about statistic selection, we promote using the Fisher information. We find out that, the statistic that is most informative in a non-privacy setting may not be the optimal choice under the privacy restrictions. We provide several examples to support that point. We consider several types of data sharing settings and propose several Monte Carlo-based numerical estimation methods for calculating the Fisher information for those settings. The second question concerns inference: (2) Based on the shared statistics, how could we perform effective Bayesian inference? We propose several Markov chain Monte Carlo (MCMC) algorithms for sampling from the posterior distribution of the parameter given the noisy statistic.

#### Statistic selection based on Fisher Information

<img src="assets/img/privacy_settings.png"  style="width:300px;height:220px;"/>

| Model         | Type                                                                         | 
|:--------------|:-----------------------------------------------------------------------------|
| (1)           | Additive statistic, Gaussian noise                                           | 
| (2)           | Additive statistic, Non-Gaussian noise (Laplace)                             | 
| (3)           | Non-additive statistic, Non-Gaussian noise (Laplace)                         |
| (4)           | No summary statistic instead sequential release, Non-Gaussian noise (Laplace)| 

#### Bayesian Inference using MCMC

MCMC algorithms used in the project:

* Metropolis-Hastings (MH)
* Pseudo-Marginal Metropolis-Hastings (PMMH)
* Metropolis-Hastings with Averaged Acceptance Ratios (MHAAR)

| Model         | Algorithm                                                                         | 
|:--------------|:----------------------------------------------------------------------------------|
| Additive statistic, Gaussian noise                                           |  MH (Algorithm 4)  | 
| Additive statistic, Non-Gaussian noise (Laplace)                             |PMMH (Algorithm 5), MHAAR (Algorithm 6| 
| Non-additive statistic, Non-Gaussian noise (Laplace)                         |MHAAR (Algorithm 7)|
| No summary statistic instead sequential release, Non-Gaussian noise (Laplace)|MHAAR (Algorithm 8)| 

## Summary of (2)
> **Title:** Differentially Private Online Bayesian Estimation with Adaptive Truncation
> 
> **Pre-print**: https://arxiv.org/abs/2203.13377
>
> Keywords: Differential privacy, Bayesian statistics, Sequential Monte Carlo, online learning

We propose a novel online and adaptive truncation method for differentially private Bayesian online estimation of a static parameter regarding a population. We assume that sensitive information from individuals is collected sequentially and the inferential aim is to estimate, on-the-fly, a static parameter regarding the population to which those individuals belong. We propose sequential Monte Carlo to perform online Bayesian estimation. When individuals provide sensitive information in response to a query, it is necessary to perturb it with privacy-preserving noise to ensure the privacy of those individuals. The amount of perturbation is proportional to the sensitivity of the query, which is determined usually by the range of the queried information. The truncation technique we propose adapts to the previously collected observations to adjust the query range for the next individual. The idea is that, based on previous observations, we can carefully arrange the interval into which the next individual's information is to be truncated before being perturbed with privacy-preserving noise. In this way, we aim to design predictive queries with small sensitivity, hence small privacy-preserving noise, enabling more accurate estimation while maintaining the same level of privacy. To decide on the location and the width of the interval, we use an exploration-exploitation approach a la Thompson sampling with an objective function based on the Fisher information of the generated observation. We show the merits of our methodology with numerical examples.

#### Differentially private online learning - general scheme (pseudocode)
1. Initialise the estimation system $\Theta_{0}$ and $s_{1}(\cdot)$.\\

2. For{$t = 1, 2, \ldots$}
  2.1.The function $s_{t}$ is revealed to individual $t$, which shares his/her data $X_{t}$ as  $$Y_{t} = s_{t}(X_{t}) + \Delta s_{t} V_{t}, \quad V_{t} \sim \textup{Laplace}\left( 1/ \epsilon \right)$$

  2.2 Update the estimation system $\Theta_{t}$ as $$\Theta_{t} = G(\Theta_{t-1}, Y_{1:t}, s_{1:t}) $$ **(3)**

  2.3.Update the new function $$s_{t+1} = H(\Theta_{t}) $$                                             **(4)**
**Sequential Monte Carlo method for (3)
**Adaptive truncation for (4)

## Summary of (3)
