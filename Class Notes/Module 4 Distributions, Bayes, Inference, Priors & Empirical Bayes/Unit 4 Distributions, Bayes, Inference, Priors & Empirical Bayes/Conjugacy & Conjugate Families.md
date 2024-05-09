# What is it?

- In Bayesian inference, a prior $p(θ)$ is ***conjugate*** to the likelihood function $p(x∣θ)$ when the posterior has the same functional form as the prior
    - This means that the two boxed terms in Bayes’ formula below have the same functional form:

$$
\boxed{p(\theta|x)} = \dfrac{p(x|\theta) \boxed{p(\theta)}}{\int p(x|\theta')p(\theta')d\theta'}
$$

- **For certain likelihood functions, selecting a specific prior results in** the posterior sharing the same distribution as the prior
    - This type of prior is then called a conjugate prior
- In other words, if you choose a prior distribution from a conjugate family, the resulting posterior distribution will also be from that same family, which makes the computation of Bayesian updates more convenient
    - The advantage of using conjugate families is that the algebraic manipulation required to obtain the posterior distribution is often straightforward
        - This simplifies the process of updating your beliefs with new data
- Conjugate families are often used when there is no strong prior information available, and you want to choose a prior that works well with the likelihood function to achieve computational efficiency
- [Good Reference](https://stats.stackexchange.com/questions/176668/can-anyone-explain-conjugate-priors-in-simplest-possible-terms)

# Why use them?

- There are basically two reasons why models with conjugate priors are popular (e.g.,  [Robert 2007](https://www.statlect.com/fundamentals-of-statistics/conjugate-prior#Robert),  [Bernardo and Smith 2009](https://www.statlect.com/fundamentals-of-statistics/conjugate-prior#Bernardo)):
    1. They usually allow us to derive a closed-form expression for the posterior distribution
    2. They are easy to interpret, as we can easily see how the parameters of the prior change after the Bayesian update
- When you know that your prior is a conjugate prior, you can skip the `posterior = likelihood * prior` computation
    - Moreover, if your prior distribution has a closed-form form expression, you can determine the maximum posterior directly

# Definition

- In our previous example we saw that with a normal likelihood and a normal prior:
    - $x|\theta \sim N(\theta, \sigma^2) \text{ with } \sigma^2 \text{ known }$
    - $\theta \sim N(\mu, \tau^2)\text{ with } \mu,\tau^2 \text{ elicited }$
- That the posterior was also normally distributed $\theta|x \sim N(\frac{\tau^2}{\sigma^2 + \tau^2}x + \frac{\sigma^2}{\sigma^2 + \tau^2}\mu, \frac{\sigma^2\tau^2}{\sigma^2 + \tau^2})$
- Generally if for a likelihood function $f$, the prior $\theta$ and posterior $\theta | x$ have the same distribution, then the pair $(f, \pi)$ **is conjugate**

# Normalizing

- If we know that $(f, \pi)$ is conjugate we do not need to calculate the ***normalizing constant***
    - $m(x) = \int_\Theta h(x,\theta)d\theta$
- This integral can be difficult, and since we know the form of $\pi(\theta|x)$ (even if it isn't normalized)
    - $\pi(\theta|x) = \frac{f(x|\theta)\pi(\theta)}{m(x)} \propto f(x|\theta)\pi(\theta)$
- we can ignore $m(x)$ altogether and choose the correct normalizing constant for the distribution proportional to $f(x|\theta)\pi(\theta)$

# How it works - Binomial Likelihood & Beta Prior

- $X|p \space \text{\textasciitilde} \space Bin(n,p); \space f(x|p) = {n \choose x}p^x(1-p)^x$
    - Where:
        - $n$ is the number of experiments (Bernoulli trials)
        - $x$ is the number of successes
        - $p$ is the probability
- $p \space \text{\textasciitilde} \space Beta(\alpha, \beta); \space \pi(p) = \dfrac{1}{B(\alpha, \beta)}p^{\alpha - 1}(1-p)^{\beta - 1}$
- $\pi(p|x) \propto f(x|p)\pi(p) = C \cdot p^{x+\alpha-1} (1-p)^{n-x+\beta-1}$
- We know this is a Beta distribution given the functional form of the equation
    - It’s just shifted by a constant
- $\Rightarrow p|X \text{\textasciitilde}Be(x+\alpha, n-x + \beta)$
- $E(p|X) = \dfrac{x+a}{n+\alpha+\beta}$

# Conjugate Families

[Wikipedia Lookup Table](https://en.wikipedia.org/wiki/Conjugate_prior#Table_of_conjugate_distributions)

| Likelihood | Prior | Posterior |
| --- | --- | --- |
| $X_i \mid  \theta \sim \mathcal{N} (\theta, \sigma^2)$ | $\theta \sim\mathcal{N}(\mu, \tau^2)$ | $\theta\mid X\sim \mathcal{N}\left(\frac{\tau^2}{\tau^2 +\sigma^2/n}\bar{X} + \frac{\sigma^2/n}{\tau^2 + \sigma^2/n}\mu, \frac{\tau^2\sigma^2/n}{\tau^2+ \sigma^2/n}\right)$ |
| $X_i\mid \theta \sim Bin(m,\theta)$ | $\theta \sim Be(\alpha,\beta)$ | $\theta\mid X \sim Be\left(\alpha + \sum_{i=1}^{n}X_i,\beta + mn - \sum_{i=1}^{n}X_i\right)$ |
| $X_i\mid \theta \sim Poi(\theta)$ | $\theta \sim Ga(\alpha,\beta)$ | $\theta\mid X \sim Ga\left(\alpha+\sum_{i=1}^{n}X_i,\beta+n\right)$ |
| $X_i\mid \theta \sim \mathcal{NB}(m,\theta)$ | $\theta \sim Be(\alpha,\beta)$ | $\theta\mid X \sim Be\left(\alpha+mn,\beta+\sum_{i=1}^{n}X_i\right)$ |
| $X_i\mid \theta \sim Ga\left(1/2,1/2\theta\right)$ | $\theta \sim IG(\alpha, \beta)$ | $\theta \mid  X \sim IG\left(\alpha + n/2, \beta + \frac{1}{2}\sum_{i=1}^{n}X_i\right)$ |
| $X_i\mid \theta \sim U(0,\theta)$ | $\theta \sim Pa(\theta_0,\alpha)$ | $\theta\mid X \sim Pa\left(\max\{\theta_0,X_1,...,X_n\},\alpha+n\right)$ |
| $X_i\mid \theta \sim \mathcal{N}(\mu,\theta)$ | $\theta \sim IG(\alpha, \beta)$ | $\theta\mid X \sim IG\left(\alpha+n/2,\beta+\frac{1}{2}\sum_{i=1}^{n}(X_i - \mu)^2\right)$ |
| $X_i\mid \theta \sim Ga(\nu,\theta)$ | $\theta \sim Ga(\alpha,\beta)$ | $\theta \mid  X \sim Ga\left(\alpha +n\nu, \beta + \sum_{i=1}^{n}X_i\right)$ |
| $X_i\mid \theta \sim Pa(c,\theta)$ | $\theta \sim Ga(\alpha,\beta)$ | $\theta \mid  X \sim Ga\left(\alpha + n, \beta + \sum_{i=1}^{n}\log\left(X_i/c\right)\right)$ |
- **Beta-Binomial Conjugate Pair:**
    - Prior: Beta distribution
    - Likelihood: Binomial distribution
    - Posterior: Beta distribution
- **Normal-Normal Conjugate Pair:**
    - Prior: Normal distribution
    - Likelihood: Normal distribution
    - Posterior: Normal distribution
- **Gamma-Poisson Conjugate Pair:**
    - Prior: Gamma distribution
    - Likelihood: Poisson distribution
    - Posterior: Gamma distribution
- Beta Posterior
    - Beta prior * Bernoulli likelihood → Beta posterior
    Beta prior * Binomial likelihood → Beta posterior
    Beta prior * Negative Binomial likelihood → Beta posterior
    Beta prior * Geometric likelihood → Beta posterior
- Gamma Posterior
    - Gamma prior * Poisson likelihood → Gamma posterior
    - Gamma prior * Exponential likelihood → Gamma posterior[Normal posterior]
- Normal Posterior
    - Normal prior * Normal likelihood (mean) → Normal posterior

# Resources

- [https://gregorygundersen.com/blog/2019/03/16/conjugacy/](https://gregorygundersen.com/blog/2019/03/16/conjugacy/)
- [https://towardsdatascience.com/conjugate-prior-explained-75957dc80bfb](https://towardsdatascience.com/conjugate-prior-explained-75957dc80bfb)
- [https://www.statlect.com/fundamentals-of-statistics/conjugate-prior](https://www.statlect.com/fundamentals-of-statistics/conjugate-prior)
- [https://archive.ph/vcUtt](https://archive.ph/vcUtt)
- [https://www.bayesrulesbook.com/chapter-8#](https://www.bayesrulesbook.com/chapter-8#)
- [https://vioshyvo.github.io/Bayesian_inference/conjugate-distributions.html](https://vioshyvo.github.io/Bayesian_inference/conjugate-distributions.html)
- [https://halweb.uc3m.es/esp/personal/personas/mwiper/docencia/English/PhD_Bayesian_Statistics/ch3_2009.pdf](https://halweb.uc3m.es/esp/personal/personas/mwiper/docencia/English/PhD_Bayesian_Statistics/ch3_2009.pdf)
- [https://www.bayesrulesbook.com/chapter-5](https://www.bayesrulesbook.com/chapter-5)
- [https://archive.ph/w19kx](https://archive.ph/w19kx)