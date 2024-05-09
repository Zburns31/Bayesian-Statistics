# Prior Elicitation

- Priors are one of the strengths of Bayesian inference. They’re also a source of criticism. Critics say that prior choice is essentially subjective and can make the resulting models too easy to manipulate into supporting whatever the creator of the model wants to say
    - But those criticisms apply to classical statistics as well; arguably, the explicitly defined prior distributions of Bayesian models are more transparent than the hidden assumptions made in many frequentist models
    - Priors ideally would be based on expert beliefs about whatever parameter you’re putting them on. In reality, we don’t always have a strong belief about something, so we might use weak or non–informative priors

# What is it?

- Prior elicitation is a crucial step in Bayesian statistics that involves incorporating existing knowledge, beliefs, or information into the statistical analysis before observing new data
    - In Bayesian statistics, you start with a prior distribution, which represents your beliefs about the parameters of the model before taking any data into account
    - Prior elicitation is the process of selecting or specifying this prior distribution based on your prior knowledge or subjective judgment
- Often, one has a belief about the distribution of one’s data
    - You may think that your data come from a binomial distribution and in that case you typically know the n, the number of trials but you usually do not know p, the probability of success
    - Or you may think that your data come from a normal distribution
        - But you do not know the mean $\mu$ or the standard deviation $\sigma$ of the normal
        - Beside to knowing the distribution of one’s data, you may also have beliefs about the unknown $p$ in the binomial or the unknown mean $\mu$ in the normal

# How does it work?

- Bayesian’s express their uncertainty through probability distributions
- One can think about the situation and self-elicit a probability distribution that approximately reflects his/her personal probability
- One’s personal probability should change according Bayes’ rule, as new data are observed

# How do we choose a prior?

- **Computational ease**
    - Especially if we don’t have access to computing power, it is helpful if the posterior model is easy to build
- **Interpretability**
    - We’ve seen that posterior models are a compromise between the data and the prior model
    - A posterior model is interpretable, and thus more useful, when you can look at its formulation and *identify* the contribution of the data relative to that of the prior
- [Suggestions](https://github.com/stan-dev/stan/wiki/Prior-Choice-Recommendations)

# Normal Likelihood + Normal Prior

- We complete the square in the exponent to simplify the joint distribution $h(x,\theta)$
    - Below is the slide from unit 4, lecture 4. The expressions in the red circles are equivalent after some unpleasant but straightforward algebra

        ![Untitled](./Prior%20Elicitation/Untitled.png)

- [Good Reference](https://math.stackexchange.com/questions/3692200/posterior-for-normal-likelihood-normal-prior)

# Interpretation as Weights

- Notice that the posterior distribution $\theta | X$ has mean (median and mode) of $\frac{\tau^2}{\sigma^2 + \tau^2}x + \frac{\tau^2}{\sigma^2 + \tau^2}\mu$ where:
    - $x$ is observed
    - $\mu$ is elicited (believed)
- This is a weighted average
    - $\frac{\tau^2}{\sigma^2 + \tau^2}x + \frac{\sigma^2}{\sigma^2 + \tau^2}\mu = w \cdot x + (1-w) \cdot \mu$ where:
    - $w = \frac{\tau^2}{\sigma^2 + \tau^2} \text{ and } \mu = \frac{\sigma^2}{\sigma^2 + \tau^2}$
- Notice that
    - $\tau^2 \gg \sigma^2 \implies w \approx 1 \text{ the posterior mean is close to x}$
    - $\sigma^2 \gg \tau^2 \implies w \approx 0 \text{ the posterior mean is close to } \mu$
- Also notice that if our likelihood and prior are normal, that our posterior is normal
    - This means that our likelihood and prior are **conjugate**, the subject of the next lecture

# Elicitation of Priors

- Given a family of distributions and some numerical characteristics (mean, variance, higher moments, quantiles, mode, ..) specify the prior

## Example

- Family - Exponential, $\theta \approx Exp(\lambda) \space \text{and} \space E \theta = 2 \Rightarrow \dfrac{1}{\lambda} = 2, \space \text{that is }\lambda = \dfrac{1}{2}$
- Family exponential and median is equal to 4


$$
\dfrac{1}{2} = 1 - e^{-4\lambda} \Rightarrow e^{-4\lambda} = \dfrac{1}{2} \Rightarrow \lambda = \dfrac{\log2}{4} = 0.1733
$$

- Notes:
    - Median of 4 tells us that 50% of the time we see $\lambda$ less than 4 and 50% of the time greater than 4

## Invariance Principle in Selecting Priors

- Let $X|\theta \text{\textasciitilde}f(x-\theta)$  ; density is a function of $(x-\theta)$; $\theta$ is the location parameter
    - Invariant prior with respect to translation $\pi(\theta) = \pi(\theta - \theta_0)$, for any $\theta_0$
    - Solution is $\pi(\theta)$ = constant
        - Often called a flat prior
    - If the parameter of interest is the scale parameter, $X|\theta \text{\textasciitilde} \dfrac{1}{\theta}. f(\dfrac{x}{\theta})$, then the invariance principle suggests $\pi(\theta) \text{\textasciitilde} \dfrac{1}{c}. \pi(\dfrac{\theta}{c})$
- This basically just says
- If we have absolutely no knowledge of the location of the distribution, the principle of indifference states that we should assign equal probability to any location.  This is equivalent to translation-invariance of our prior
    - Put another way: if our prior were *not* translation-invariant, that would be equivalent to expressing some amount of knowledge about the location of the distribution (in particular, we'd know that the distribution is more likely to be located in some region than in some other identically-sized region)
    - [Reference](https://math.stackexchange.com/questions/4279700/what-is-the-intuition-or-motivation-about-translation-invariant-priors)

## Non-Informative Priors

- Priors ideally would be based on prior beliefs or knowledge about the parameter in question. But in reality, we don’t always have a strong belief about something, so we might use non-informative priors. That, and criticism from frequentist statisticians, led to people looking for the “objective” best non-informative priors, for some definition of objective
    - These are also sometimes called reference priors
- In Bayesian statistics, an uninformative (or non-informative) prior is a **prior that has minimal influence on the inference**
    - the distribution is called an “informative prior”, if it biases the parameter towards particular values
    - the distribution is called a “weakly informative prior”, if it mildly [influences the posterior distribution](https://statproofbook.github.io/P/post-jl)
    - the distribution is called a “non-informative prior”, if it does not [influence](https://statproofbook.github.io/P/post-jl) the [posterior hyperparameters](https://statproofbook.github.io/D/post)

## Improper Priors

- An improper prior is a prior distribution whose integral does not integrate to a finite number
- Despite their mathematical irregularity, improper priors can often be used in Bayesian analysis without issue
    - This is because we seldom integrate priors by themselves; instead, our requirement is that the product of the prior and likelihood function result in a proper posterior distribution

# Resources

- [Prior Choice Recommendations](https://github.com/stan-dev/stan/wiki/Prior-Choice-Recommendations)
- [https://math.mit.edu/~dav/05.dir/class15-slides-all.pdf](https://math.mit.edu/~dav/05.dir/class15-slides-all.pdf)
- [https://statswithr.github.io/book/bayesian-inference.html#elicitation](https://statswithr.github.io/book/bayesian-inference.html#elicitation)