---
layout: default
---

Text can be **bold**, _italic_, or ~~strikethrough~~.

*   **Principle investigator:** Sinan Yıldırım
*   **Project Type:** TUBITAK 3501

[See people working on the project](./another-page.html).

### Research output 

*   **Submitted:** Statistic Selection and MCMC for Differentially Private Bayesian Estimation, B.Alparslan, S.Yıldırım, submitted to Statistics and Computing, 2022
*   **Work in progress:** Differentially Private Linear Regression with Gibbs Sampling, B.Alparslan, S.Yıldırım, 2022

## Summary of the work

> **Title:** Statistic Selection and MCMC for Differentially Private Bayesian Estimation
>
> **Arxiv link:** (https://arxiv.org/abs/2203.13377) 
>
> Differentially private Bayesian estimation of the parameters of a population distribution when a noisy statistic of a sample from that population is shared.

### Main contributions

* Statistic selection based on Fisher Information.
* Sampling from the true posterior based on the noisy statistic (Bayesian Inference using MCMC).

This work mainly addresses two problems: (1) What statistic of the sample should be shared privately? For the first question, i.e., the one about statistic selection, we promote using the Fisher information. We find out that, the statistic that is most informative in a non-privacy setting may not be the optimal choice under the privacy restrictions. We provide several examples to support that point. We consider several types of data sharing settings and propose several Monte Carlo-based numerical estimation methods for calculating the Fisher information for those settings. The second question concerns inference: (2) Based on the shared statistics, how could we perform effective Bayesian inference? We propose several Markov chain Monte Carlo (MCMC) algorithms for sampling from the posterior distribution of the parameter given the noisy statistic.

#### Statistic selection based on Fisher Information

<img src="assets/img/privacy_settings.png"  style="width:300px;height:250px;"/>

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

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
