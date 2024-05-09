# What is it?

- The **negative binomial distribution** is a [discrete probability distribution](https://en.wikipedia.org/wiki/Discrete_probability_distribution) that models the number of failures in a sequence of independent and identically distributed [Bernoulli trials](https://en.wikipedia.org/wiki/Bernoulli_trial) before a specified (non-random) number of successes (denoted $r$) occurs
    - The negative binomial distribution helps in finding r success in x trials
- For example, we can define rolling a 6 on a die as a success, and rolling any other number as a failure, and ask how many failure rolls will occur before we see the third success ($r=3$)

# Similarities to the Binomial Distribution

- The **negative binomial** is similar to the binomial with two differences:
    - The number of trials, $n$ **is not fixed**
    - A [random variable](https://www.statisticshowto.com/random-variable/) $Y$ = the number of trials needed to make $r$ successes

# Criteria

- The experiment consists of *x* repeated trials
- Each trial can result in just two possible outcomes
    - We call one of these outcomes a success and the other, a failure
- The probability of success, denoted by $P$, is the same on every trial
- The trials are [independent](https://stattrek.com/statistics/dictionary?definition=Independent); that is, the outcome on one trial does not affect the outcome on other trials
- The experiment continues until $r$ successes are observed, where $r$ is specified in advance

# Binomial Distribution Function

$$
f(k;r,p) \equiv P(X=x) = \begin{pmatrix}
   k + r - 1 \\
   k
\end{pmatrix} (1-p)^k p^r
$$

The binomial coefficient can be re-written as:

$$
\begin{pmatrix}
   k + r - 1 \\
   k
\end{pmatrix}  = \dfrac{(k+r-1)!}{(r-1)!(k)!}
$$

- Where:
    - $r$ is the number of successes
    - $k$ is the number of failures
    - $p$ is the probability of success on each trial
- Notes
    - There are $k$ failures chosen from $k + r − 1$ trials rather than $k + r$ because the last of the $k + r$ trials is by definition a success

# Likelihood Function

$$
L(\pi|x_i) = \prod_{i=1}^n \begin{pmatrix}
   k + r - 1 \\
   k
\end{pmatrix} (1-p)^k p^r
$$

# Numerical Characteristics

- **PMF:**
- **CDF:**
- **Mean:**
- **Variance:**
- **Support:** $\{0, 1, 2, ..., n\}$
- **Parameters:**
- **Notation: $X \sim NB(r,p)$**

# Resources

- [https://en.wikipedia.org/wiki/Negative_binomial_distribution](https://en.wikipedia.org/wiki/Negative_binomial_distribution)
- [https://www.statisticshowto.com/negative-binomial-experiment/](https://www.statisticshowto.com/negative-binomial-experiment/)
- [https://online.stat.psu.edu/stat414/lesson/11/11.5](https://online.stat.psu.edu/stat414/lesson/11/11.5)