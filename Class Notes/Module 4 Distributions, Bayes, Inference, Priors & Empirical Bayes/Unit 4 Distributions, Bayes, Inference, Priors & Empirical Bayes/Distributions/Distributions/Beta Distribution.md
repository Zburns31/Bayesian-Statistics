# What is it?

- The Beta distribution is **a probability distribution *on probabilities***
    - For example, we can use it to model the probabilities: the Click-Through Rate of your advertisement, the conversion rate of customers actually purchasing on your website, how likely readers will clap for your blog, how likely it is that Trump will win a second term, the 5-year survival chance for women with breast cancer, and so on
- The standard beta distribution uses the interval [0,1]
    - This range is ideal for modelling probabilities, particularly for experiments with only two outcomes
        - However, other intervals are possible
- The difference between the binomial and the beta distribution is that **the former models the number of successes (x), while the latter models the probability (p) of success**
    - In other words, the probability is **a** **parameter** in the binomial distribution. In contrast, in the Beta distribution, the probability is **a** **random variable**

# When to use it?

The Beta distribution can be used to analyze probabilistic experiments that have only two possible outcomes:

1. success, with probability X
2. Failure, with probability X - 1
- These experiments are called Bernoulli experiments

# How it works

- The Beta distribution takes two parameters, *α* and *β*
    - In the simplest terms these parameters can be thought of as respectively the count of successes and failures
- A Beta distribution has a mean value defined by $\dfrac {\alpha} {\alpha + \beta} = \dfrac {number \space of \space successes} {number \space of \space trials}$

![Untitled](./Beta%20Distribution/Untitled.png)

# Probability Density Function (PDF)

$$
f(x) = \dfrac{1}{B(a,b)} x^{a-1}(1-x)^{b-1}, 0 \le x \le 1
$$

- Where:
    - $x$ represents the probability. I.e. $P(X = x)$
    - $B(\alpha, \beta)= \dfrac{\Gamma(\alpha) \Gamma(\beta)}{\Gamma(\alpha + \beta)}$
    - $\Gamma(\alpha) = \int_0^\infty t^{\alpha -1} e^{-\alpha } dt$

We can also define the Beta function via integral

$$
\int_0^1 x^{a-1}(1-x)^{b-1}
$$

# Likelihood Function

$$
L(\alpha, \beta | X) = \prod_{i=1}^n \left( \dfrac{\Gamma(\alpha) \Gamma(\beta)}{\Gamma(\alpha + \beta )} x_i^{\alpha-1} \right )
$$

# Numerical Characteristics

- **PDF:** $f(x|\alpha,\beta) = \frac{x^{\alpha-1} (1-x)^{\beta-1}}{B(\alpha,\beta)}$
- **CDF:** $I_x(\alpha,\beta)$
- **Mean:** $\frac{\alpha}{\alpha+\beta}$
- **Variance:** $\frac{\alpha \beta}{(\alpha+\beta)^2(\alpha+\beta+1)}$
- **Support:** $(0, 1)$
- **Parameters:** $\alpha,\beta\text{(shape parameters)}$
- **Notation:** $X \sim Be(\alpha, \beta)$

# Resources

- [https://byjus.com/maths/beta-distribution/](https://byjus.com/maths/beta-distribution/)
- [https://www.statlect.com/probability-distributions/beta-distribution](https://www.statlect.com/probability-distributions/beta-distribution)
- [https://statisticsbyjim.com/probability/beta-distribution/](https://statisticsbyjim.com/probability/beta-distribution/)
- [https://archive.ph/3HTCm#selection-675.0-689.15](https://archive.ph/3HTCm#selection-675.0-689.15)
- [https://towardsdatascience.com/beta-distribution-intuition-examples-and-derivation-cf00f4db57af](https://towardsdatascience.com/beta-distribution-intuition-examples-and-derivation-cf00f4db57af)
