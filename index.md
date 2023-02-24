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
> Keywords: Differential privacy, Markov chain Monte Carlo, Fisher information, statistic selection, Bayesian statistics

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
> **Pre-print**: https://arxiv.org/abs/2301.08202
>
> Keywords: Differential privacy, Bayesian statistics, Sequential Monte Carlo, online learning

We propose a novel online and adaptive truncation method for differentially private Bayesian online estimation of a static parameter regarding a population. We assume that sensitive information from individuals is collected sequentially and the inferential aim is to estimate, on-the-fly, a static parameter regarding the population to which those individuals belong. We propose sequential Monte Carlo to perform online Bayesian estimation. The idea is that, based on previous observations, we can carefully arrange the interval into which the next individual's information is to be truncated before being perturbed with privacy-preserving noise. In this way, we aim to design predictive queries with small sensitivity, hence small privacy-preserving noise, enabling more accurate estimation while maintaining the same level of privacy.

#### Differentially private online learning - general scheme (pseudocode)
1. Initialise the estimation system $\Theta_{0}$ and $s_{1}(\cdot)$.

2. For $t = 1, 2, \ldots$
  - The function $s_{t}$ is revealed to individual $t$, which shares his/her data $X_{t}$ as \\[ Y_{t} = s_{t}(X_{t}) + \Delta s_{t} V_{t}, \quad V_{t} \sim \text{Laplace}\left( 1/ \epsilon \right) \\]
  - (3) Update the estimation system $\Theta_{t}$ as \\[ \Theta_{t} = G(\Theta_{t-1}, Y_{1:t}, s_{1:t}) \\]
  - (4) Update the new function \\[ s_{t+1} = H(\Theta_{t}) \\]   
                                             
**The method employs Sequential Monte Carlo algorithm for step (3)**

**The method utilizes adaptive truncation based on exploration-exploitation and Thomson sampling using Fisher information for step (4)**

## Summary of (3)
> **Title:** Differentially Private Distributed Bayesian Linear Regression with MCMC
> 
> **Pre-print**: https://arxiv.org/abs/2301.13778
>
> Keywords: Differential privacy, linear regression, distributed learning, MCMC

We propose a novel Bayesian inference framework for distributed differentially private linear regression. We consider a distributed setting where multiple parties hold parts of the data and share certain summary statistics of their portions in privacy-preserving noise. We develop a novel generative statistical model for privately shared statistics, which exploits a useful distributional relation between the summary statistics of linear regression. Bayesian estimation of the regression coefficients is conducted mainly using Markov chain Monte Carlo algorithms, while we also provide a fast version to perform Bayesian estimation in one iteration. The proposed methods have computational advantages over their competitors which are state-of-art algorithms adopted for the distributed case.

#### Basic model and setup

#### Distributed setting 
Model:
\\[
y_{i} = x_{i}^{T}\theta + e_{i}, \quad e_{i} \overset{\text{i.i.d.}}{\sim} \mathcal{N}(0, \sigma_{y}^{2}), \quad i = 1, \ldots, n,
 \\]

Summary statistics are shared with noise as
\\[
S := X^{T}X, \quad z := X^{T}y, %  = S\theta + X^{T} e.
\\]
\\[
\hat{S} &= S + \sigma_{s}M, \\]
\\[
\hat{z} &= z + \sigma_{z} v, \quad v \sim \mathcal{N}(0,I_{d}), \\]
 
#### Differentially private distributed linear regression model 


#### Algorithm-model matching
| Model         | Type                                                                         | 
|:----------------------------------|:-----------------------------------------------------------------------------|
| Normally distributed features| MCMC-NormalX                                           | 
| Features with general distribution| MCMC-fixedS, Bayes-fixedS-fast                            | 
| Extended state-of-art algorithms| MCMS-B&S, adaSSP                        |
