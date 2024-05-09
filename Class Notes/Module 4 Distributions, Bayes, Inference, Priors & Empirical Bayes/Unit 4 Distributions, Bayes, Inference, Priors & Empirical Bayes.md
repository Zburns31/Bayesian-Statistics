# Basic Distributions & Numerical Characteristics

- [Distributions](./Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Distributions/Distributions.md)
- [Numerical Characteristics](./Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Numerical%20Characteristics.md)
- [Joint & Conditional Distributions](./Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Joint%20&%20Conditional%20Distributions.md)

## Models & Parameters

- A random variable is a variable whose numerical value is determined by the outcome of a random experiment
    - Can be both Discrete and Continuous
        - Discrete

        | X | x1 | x2 | … | xn |
        | --- | --- | --- | --- | --- |
        | Probabilities | p1 | p2 | … | pn |

        Where $P(X = x_i) = p_i; \sum p_i = 1$


    - Continuous: Realizations are all points in an interval. Need density $f(x)$

    ![Untitled](./Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Untitled.png)

    Where $P(X \in I) = \int_I f(x)dx$


# Distribution Functions

- Probability Mass Functions are used for discrete variables
- Probability Density Functions are used for continuous variables

# How the Probability Density Function works

- The  [probability](https://www.statlect.com/fundamentals-of-probability/probability) that a continuous random variable takes a value in a given interval is equal to the integral of its probability density function over that interval
    - In turn, the  [integral](https://www.statlect.com/mathematical-tools/integrals-review) is equal to the area of the region in the xy-plane bounded by:
        - the x-axis;
        - the pdf;
        - the vertical lines corresponding to the boundaries of the interval

## Cumulative Density Functions

- CDF —> Probability Distribution (Cumulative)
- The CDF for both discrete (top) and continuous (bottom) are defined below:

$$
F(x) = P(X=x) = \begin{cases}
   \sum_{x_i \le x} P(X=x_i) \\
\\
   \int_{-\infin}^x f(x)dx
\end{cases}
$$

# Bayes Theorem & Ingredients for Inference

Describes: Prior, Likelihood, Posterior & the Marginal distributions and how this plays into bayes theorem

- [Bayes Theorem & Ingredients For Inference](../Module%202%20Bayesian%20Vs.%20Frequentist%20Statistics/Bayesian%20Statistics/Bayes%20Theorem%20&%20Ingredients%20For%20Inference.md)

# Conjugacy

- [Conjugacy & Conjugate Families](./Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Conjugacy%20&%20Conjugate%20Families.md)

# Prior Elicitation

- [Prior Elicitation](./Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Prior%20Elicitation.md)

# Bayes Decision Theory

- [Bayesian Decision Theory](./Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Bayesian%20Decision%20Theory.md)

# Credible Sets

- [Credible Sets](./Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Credible%20Sets.md)

# Bayesian Testing

- [Bayesian Hypothesis Testing](./Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Bayesian%20Hypothesis%20Testing.md)

# Bayesian Inference

- [Bayesian Inference](./Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Bayesian%20Inference.md)

# Prior Sample Size

- The effective sample size refers to the size of a random sample that contains the same amount of information as the actual sample you have, particularly in the context of estimating statistical properties or conducting statistical analyses
    - It quantifies the efficiency of your sample in providing information about a population or a dataset
    - ***Samples that are highly correlated don’t count as individual samples***
    - Effective sample size, as defined in the lecture, is an informal measure of the strength of a prior as it interacts with a particular likelihood to contribute to the posterior
- How do we calibrate the amount of information carried by the prior?
    - Informally $\text{Information in the Prior} \equiv \text{Information in a sample of size } m$
    - $m = ESS \text{ (Effective Sample Size})$
- Community of Priors (Spieghalter)
    - vague, skeptical, and enthusiastic [[Spiegelhalter *et al.*, 1994](https://areding.github.io/6420-pymc/backmatter/bibliography.html#id21)]. These are similar to the five categories mentioned in the Stan [Prior Choice Recommendations](https://github.com/stan-dev/stan/wiki/Prior-Choice-Recommendations)

# Empirical Bayes

- [Empirical Bayes](./Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Empirical%20Bayes.md)

# Terms & Key Concepts

- **Variance:** The variance should be regarded as (something like) the average of the difference of the actual values from the average. A larger variance indicates a wider spread of values
- **Likelihood:** The relative number of ways that a value p can produce the data is usually called a likelihood
    - It is derived by enumerating all the possible data sequences that could have happened and then eliminating those sequences inconsistent with the data
- **Probability Distribution:** Let *Z* be some random variable. Then associated with *Z* is a *probability distribution function* that assigns probabilities to the different outcomes *Z* can take
- **Random Variables:** Z can be divided into three classifications: 1) Discrete, 2) Continuous and 3) Mixed
    - If Z is discrete, then its distribution is called a probability mass function which measures the probability that Z takes on the value k, denoted $P(Z=k)$
        - Note that the probability mass function completely describes the random variable Z
    - If Z is continuous, then Z has a probability density function
        - ***It’s important to know that the value of the probability density function at a point does not equal the probability of that point***
- **Cumulative Distribution Function (CDF)**
    - [Cumulative distribution function](https://en.wikipedia.org/wiki/Cumulative_distribution_function) is sometimes shortened as "distribution function", it's $𝐹(𝑥)=Pr(𝑋≤𝑥)$ the definition is the same for both discrete and continuous random variables
    - In dice case it's probability that the outcome of your roll
    will be $x$ **or smaller
- **Probability Mass Function (PMF)**
    - PMF is a statistical term that describes the probability distribution of the **Discrete** random variable
        - Probability mass function has no sense for continuous random variables since [Pr(*𝑋*=*𝑥*)=0 for continuous random variables](https://stats.stackexchange.com/questions/142730/px-x-0-when-x-is-continuous-variable) (check also [Why X=x is impossible for continuous random variables?](https://stats.stackexchange.com/questions/238058/why-x-x-is-impossible-for-continuous-random-variables/238062#238062)), because simply a point on real line is so "small" that has no mass and no area
        - The PDF is applicable for continues random variable while PMF is applicable for discrete random variable
- **Probability Density Function (PDF)**
    - PDF is a statistical term that describes the probability distribution of the **continuous** random variable
    - $f(x) = P(a\le x \le b) = \int_a^b f(x)dx$
    - On PDF graph the probability of single outcome is always zero, this happened because the single point represents the line which doesn’t cover the area under the curve
- **Elicited** means that some assumptions are made before hand using prior information
- **Conjunctive probability** (a.k.a. **joint probability**): The probability that all events happen
- **Disjunctive probability**: The probability that at least one event happens
- **Mutually exclusive events:** If one event happens, then the other event cannot happen (e.g., you cannot roll a dice that is both 5 and 1)
- **Kernel:** essentially represents the functional form (variables of interest) in a function
- **Likelihood Function:** The *Likelihood* function is just the probability density (or mass) function $f(x|θ)$ re-interpreted to be a function where the data is the known quantity and we are looking to see what parameter values are consistent with the data
    - **Likelihood** is often interchangeably used with probability, but they are not the same
    - Likelihood is not a probability density function, meaning that integrating over a specific interval would not result in a “probability” over that interval
        - Rather, it talks about how likely a distribution with certain values for its parameters fits our data
- **Biased Vs. Unbiased Estimators**
    - The **bias of an estimator** (or **bias function**) is the difference between this [estimator](https://en.wikipedia.org/wiki/Estimator)'s [expected value](https://en.wikipedia.org/wiki/Expected_value) and the [true value](https://en.wikipedia.org/wiki/True_value) of the parameter being estimated. An estimator or decision rule with zero bias is called ***unbiased***
    - [Good Resource](https://medium.com/@kandemirr.irem/biased-or-unbiased-bfb68aefa3e3)

# Resources

- [Probability Distributions](https://medium.com/analytics-vidhya/pdf-pmf-and-cdf-in-machine-learning-225b41242abe)
- [https://bookdown.org/johnnydoorn/bayesbookdown/](https://bookdown.org/johnnydoorn/bayesbookdown/)

## Problem Specific Resources

- [Find the Expected Value and Variance of a given density function](https://math.berkeley.edu/~scanlon/m16bs04/ln/16b2lec30.pdf)
- Compute the marginal distribution given the joint
    - U4L3

## Maximum Likelihood Estimation

- [https://bookdown.org/dereksonderegger/571/13-maximum-likelihood-estimation.html](https://bookdown.org/dereksonderegger/571/13-maximum-likelihood-estimation.html)
- [https://polaris000.medium.com/understanding-maximum-likelihood-estimation-e63dff65e5b1](https://polaris000.medium.com/understanding-maximum-likelihood-estimation-e63dff65e5b1)

## Effective Sample Size

- [https://www.displayr.com/what-is-effective-sample-size/](https://www.displayr.com/what-is-effective-sample-size/)
- [https://andrewcharlesjones.github.io/journal/21-effective-sample-size.html](https://andrewcharlesjones.github.io/journal/21-effective-sample-size.html)
- [https://mc-stan.org/docs/2_19/reference-manual/effective-sample-size-section.html](https://mc-stan.org/docs/2_19/reference-manual/effective-sample-size-section.html)