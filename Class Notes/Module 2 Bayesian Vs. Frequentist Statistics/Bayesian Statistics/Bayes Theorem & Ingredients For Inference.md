# Bayes Theorem & Ingredients For Inference

# What is it?

- Bayes' theorem is a fundamental concept in probability theory and statistics that describes the relationship between conditional probabilities of events
    - It allows us to update our beliefs or knowledge about a hypothesis or event based on new evidence or information
- **Bayes’ rule lets you “invert” a conditional probability distribution over an effect, given a cause, into a conditional probability distribution over the cause, given the effect**

# Bayesian Learning & Bayes Rule

- There are 4 components to the Bayes Rule:
    1. **Posterior probability** (updated probability after the evidence is considered)
    2. **Prior probability** (the probability before the evidence is considered)
    3. **Likelihood** (probability of the evidence, given the belief is true)
    4. **Marginal probability** (probability of the evidence, under any circumstance)

$$
\underbrace{P(H_i)}_{\text{prior prob}} \rightarrow  P(H_i|A) = \underbrace{\dfrac{P(A|H_i)}{P(A)}}_{\text{Posterior}} \cdot P(H_i)
$$

$$
\underbrace{P(A|B)}_{\text{posterior}} = \underbrace{P(A)}_{\text{Prior}} \space * \space \dfrac{\underbrace{P(B|A)}_{\text{likelihood}}}{\underbrace{P(B)}_{\text{marginal}}}
$$

- Other Notes
    - The posterior is sometimes known as the ***Bayes Factor***
    - $P(B|A)$ is known as the likelihood
        - This is another conditional probability. It is the probability of the evidence being present, given the hypothesis is true
    - $P(A)$ is the prior distribution (also known as the evidence)
        - This is the normalization factor. This is necessary to normalize the updated sampling probability; otherwise, the posterior will not be limited to between 0 and 1
    - $P(A \mid B)$ is the ***posterior probability***, which is the prior updated by $\dfrac{P(B \mid A)}{P(B)}$
- More generally, we can write Bayes Rule as:

$$
P(Hypothesis|Evidence) = P(Hypothesis) * \dfrac{P(Evidence|Hypothesis)}{P(Evidence)}
$$

# Likelihood Principle

- The first building block of a parametric Bayesian model is the likelihood $p(x|\theta)$
- The likelihood is equal to the [probability density](https://www.statlect.com/glossary/probability-density-function) of $x$ when the parameter of the data generating distribution is equal to $\theta$
- The Likelihood Principle is a concept in statistics that basically states that all the information you need to draw conclusions from data is contained in the likelihood function. In simpler terms, it means that when you're trying to figure out something from the data you've collected, the best way to do it is by looking at the probability of getting the data you have, given different possible explanations or models
    - Imagine you're trying to find out how likely it is for a coin to be biased based on a series of coin tosses
    - The Likelihood Principle suggests that you should focus on how probable the observed sequence of heads and tails is under different bias levels, rather than making assumptions beforehand about the bias
- Mathematically, if we have a statistical model with parameters represented by $\theta$ (theta) and we have observed data $x$, the likelihood function $L(\theta|x)$ is defined as:

$$
L(\theta|x) = P(x|\theta)
$$

- In words, this equation says: "The likelihood of the parameters $\theta$ given the observed data x is equal to the probability of observing data x given those parameters $\theta$
- In frequentist methods we have an unknown parameter, and we observe some data
    - Furthermore, we know the probability that such data might have arisen under any value of the parameter
    - We want to make inference about the value of the parameter given the data, so it makes sense to multiply the probability that the data emerged as a result of some parameter value by some weighting on the set of parameter values

## Mathematical Breakdown

- We have several observations $X_1,...,X_n$ of a random variable that are independent and identically distributed (IID)
    - We suppose they come from a distribution parameterized by $\theta$
    - $X_i \sim f(x_i| \theta), \text{ for } i=1,...,n$
- The joint distribution is

$$
\begin{align}f(x_1,x_1,...x_n|\theta) &= f(x_1|\theta) \cdot f(x_2 | \theta) ... f(x_n|\theta) \text{ by independence}\\ &= \prod_{i=1}^nf(x_i|\theta)\end{align}
$$

- The **likelihood** function $L$ is a measure of how likely an outcome is for a particular value of $\theta$

$$
    \begin{align}
        L(\theta|x_1,...,x_n) = \prod_{i=1}^n f(x_i| \theta)
    \end{align}
$$

## Invariance Property

- The invariance property of maximum likelihood estimators (MLEs) is a helpful feature in statistics
    - In simple terms, it means that if you use the MLE to estimate one parameter in a problem and then use the estimated value to calculate another parameter, the MLE of the second parameter will be the same as if you had calculated it directly using the likelihood function
- Here's an example to illustrate the invariance property:
    - Imagine you're trying to estimate two things about a population: the mean ($μ$) and the variance ($σ²$). You use the MLE method to estimate the mean, and let's say you find that the MLE of $μ$ is 10. Now, you want to estimate the variance
    - With the invariance property, you can calculate the MLE of the variance ($σ²$) using the estimated mean ($μ = 10$) without redoing the whole likelihood maximization process. This is possible because the MLE of the variance is a function of the MLE of the mean, and the invariance property tells us that this function will give you the correct answer

### Example

- $X_i$ have exponential distributions $\text{Exp}(\lambda)$ and are independent

$$
    \begin{align}
        X_1=2, X_2=3, X_3=1 \implies \\L(\lambda|x_1,x_2,x_3) = \lambda e^{-2\lambda} \cdot \lambda e^{-3\lambda} \cdot \lambda e^{-\lambda} = \lambda ^3 e^{-6\lambda}
    \end{align}
$$

- In general for $n$ independent exponential distributions with parameter $\lambda$

$$
    \begin{align}
        L(\lambda|x_1,x_2,...,x_n) = \lambda^ne^{-\lambda\sum_{i=1}^nx_i}
    \end{align}
$$

# Generalization of Bayes Theorem

- Recall the discrete form of the Bayes’ rule:

    $$
    P(A_i|B)=\dfrac{P(B|A_i)P(A_i)}{\underbrace{\sum_{j=1}^n=P(B|A_j)P(A_j)}_{P(B)}}
    $$

- However, this formula does not apply to continuous random variables, such as the $p$ which follows a beta distribution, because the denominator sums over all possible values (must be finitely many) of the random variable
- But the good news is that the $p$ has a finite range – it can take any value **only** between 0 and 1
    - Hence we can perform integration, which is a generalization of the summation. The Bayes’ rule can also be written in continuous form as:

    $$
    \pi(p|x)=\dfrac{P(x|p)π(p)}{\int_0^1 P(x|p)π(p)dp}
    $$

- This is analogous to the discrete form, since the integral in the denominator will also be equal to some constant, just like a summation
    - This constant ensures that the total area under the curve, i.e. the posterior density function, equals 1

# Ingredients for Bayesian Inference

- Let's start with Bayes' theorem again:

$$
    \begin{align}
        \pi(\theta \mid x) = \frac{f(x \mid \theta) \pi(\theta)}{m(x)}
    \end{align}
$$

- This is the notation we'll use when talking about probability distributions rather than events as we've done in Unit 3

## The Posterior distribution: $\pi(\theta \mid x)$

- This is the prior updated by the data and normalized

## The Likelihood: $f(x \mid \theta)$

- Contains all the information about our experiment
    - It's an observed variable, so we describe it with $f(\cdot)$ rather than $\pi(\cdot)$ like the posterior and prior. The likelihood is:

        $$
        \begin{align}
            L(\theta|x_1, ..., x_n) = \prod_{i=1}^{n} f(x_i|\theta)
        \end{align}
        $$

    - Where $n$ is the number of datapoints. ***As the sample size increases, the likelihood tends to dominate the prior, leading to a posterior more influenced by the data***
    - Put another way, as we get more data, our prior beliefs become less important, so the data drives our conclusions

## The Prior: $\pi(\theta)$

- Usually we use this to describe the state of our knowledge or expert opinion prior to the experiment
- ***Every unobserved variable in your model is a parameter***
    - For each parameter, you will need to elicit a prior
    - Some students have criticized using $\pi(\cdot)$ to describe both the posterior and the prior, but that is intentional. It's accurately describing what we're doing with Bayes' theorem—updating our priors with new information to form our posterior

## The Marginal Distribution (Normalizing Constant): $m(x)$

- Obtain it by integrating the joint distribution of $x$ and $\theta$ over all possible values of $\theta$:

    $$
    \begin{align}
        m(x) = \int_{\Theta} f(x|\theta) \pi(\theta) d\theta
    \end{align}
    $$

    - This integral is often intractable, which is why a large portion of this course is devoted to strategies to avoid calculating it
        - More on that later; but because of this situation, we often just write Bayes' theorem in its proportional form:

            $$
            \begin{align}
                \pi(\theta|x) \propto f(x|\theta) \pi(\theta)
            \end{align}
            $$

    - The $\propto$ means "proportional to"
        - Often this is all you need, whether you're going for a ratio (where the marginal cancels out) or you can recognize the kernel of the posterior

## Sample Size Considerations

- First, when samples are small, priors have a relatively larger impact on the posterior than when samples are large
    - The posterior can be seen as a compromise between the prior and the likelihood
- With a larger sample size, the likelihood dominates the posterior (see [Figure 1C](https://www.frontiersin.org/articles/10.3389/fpsyg.2020.611963/full#F1)). However, with a small sample size, the likelihood has relatively less weight on the posterior
    - Accordingly, the prior has relatively more weight on the posterior

![Untitled](./Bayes%20Theorem%20&%20Ingredients%20For%20Inference/Untitled.png)

- Notes:
    - This shows examples of prior, likelihood and posterior distributions under small (A), medium (B) and large (C) sample sizes
        - The posterior is dominated by the prior under the small sample size (A)
        - The posterior is dominated by the likelihood under the large sample size
- [Reference](https://www.frontiersin.org/articles/10.3389/fpsyg.2020.611963/full)
- [SO Thread](https://stats.stackexchange.com/questions/200982/do-bayesian-priors-become-irrelevant-with-large-sample-size)

# Notational Summary

- Likelihood Model: $f(x|\theta)$
- Prior Distribution: $\pi(\theta)$
- Joint Distribution: $h(x, \theta) = f(x|\theta)\pi(\theta)$
- Marginal Distribution: $m(x) = \int_\Theta f(x|\theta)\pi(\theta)d\theta$
- Posterior Distribution: $\pi(\theta|x) = \dfrac{f(x|\theta)\pi(\theta)}{m(x)}$

# Resources

- [https://areding.github.io/6420-pymc/unit3/Unit3-Bayes-theorem.html](https://areding.github.io/6420-pymc/unit3/Unit3-Bayes-theorem.html)
- [https://statswithr.github.io/book/the-basics-of-bayesian-statistics.html#bayes-rule](https://statswithr.github.io/book/the-basics-of-bayesian-statistics.html#bayes-rule)
- [https://oscarbonilla.com/2009/05/visualizing-bayes-theorem/](https://oscarbonilla.com/2009/05/visualizing-bayes-theorem/)
- [https://towardsdatascience.com/bayes-theorem-clearly-explained-with-visualization-5083ea5e9b14](https://towardsdatascience.com/bayes-theorem-clearly-explained-with-visualization-5083ea5e9b14)
- [https://www.freecodecamp.org/news/bayes-rule-explained/](https://www.freecodecamp.org/news/bayes-rule-explained/)
- [https://towardsai.net/p/l/understand-bayes-theorem-through-visualization](https://towardsai.net/p/l/understand-bayes-theorem-through-visualization)

### Likelihood

- [https://stats.stackexchange.com/questions/491317/what-is-likelihood-principle](https://stats.stackexchange.com/questions/491317/what-is-likelihood-principle)
- [https://statswithr.github.io/book/bayesian-inference.html](https://statswithr.github.io/book/bayesian-inference.html)
- [https://bookdown.org/aramir21/IntroductionBayesianEconometricsGuidedTour/sec24.html](https://bookdown.org/aramir21/IntroductionBayesianEconometricsGuidedTour/sec24.html)
- [https://bookdown.org/jkang37/stat205b-notes/lecture08.html](https://bookdown.org/jkang37/stat205b-notes/lecture08.html)
- [https://www.quora.com/What-does-Invariance-Principle-of-Properties-of-Maximum-Likelihood-estimation-mean](https://www.quora.com/What-does-Invariance-Principle-of-Properties-of-Maximum-Likelihood-estimation-mean)
- [https://towardsdatascience.com/maximum-likelihood-estimation-how-it-works-and-implementing-in-python-b0eb2efb360f](https://towardsdatascience.com/maximum-likelihood-estimation-how-it-works-and-implementing-in-python-b0eb2efb360f)