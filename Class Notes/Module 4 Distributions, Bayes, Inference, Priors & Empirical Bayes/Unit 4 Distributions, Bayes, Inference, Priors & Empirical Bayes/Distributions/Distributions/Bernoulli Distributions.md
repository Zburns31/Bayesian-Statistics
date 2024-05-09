# What is it?

- A **Bernoulli distribution** is a [discrete probability distribution](https://www.statisticshowto.com/discrete-probability-distribution/) for a [Bernoulli trial](https://www.statisticshowto.com/bernoulli-trials/) — a random experiment that has only two outcomes  (usually called a “Success” where $n = 1$ or a “Failure” where $n = 0$)
- For example, the probability of getting a heads (a “success”) while flipping a coin is 0.5
    - The probability of “failure” is 1 – P (1 minus the probability of success, which also equals 0.5 for a coin toss)
- It is a special case of the [binomial distribution](https://www.statisticshowto.com/probability-and-statistics/binomial-theorem/binomial-distribution-formula/) for n = 1. In other words, it is a binomial distribution with a single trial (e.g. a single coin toss)

    ![Untitled](./Bernoulli%20Distributions/Untitled.png)


# Probability Density Function

$$
P(n) = \begin{cases}
   1-p &\text{for n = 0} \\
   p &\text{for n = 1}
\end{cases}
$$

This can also be written as $P(n) = p^n(1-p)^{1-n}$

# Numerical Characteristics

- **PMF:** $P(X=k|p) = p^k(1-p)^{1-k} \space \text{for k} \in \{0, 1\}$
- **CDF:** $F(k|p) = \begin{cases}
0 & \text{for } k < 0 \\
1-p & \text{for } 0 \leq k < 1 \\
1 & \text{for } k \geq 1
\end{cases}$
- **Mean:** $p$
- **Variance:** $p(1-p)$
- **Support:** $\{0, 1\}$
- **Parameters:** $p$ (probability of success)
- **Notation:** $X \sim Bernoulli(p)$

# Resources

- [https://mathworld.wolfram.com/BernoulliDistribution.html](https://mathworld.wolfram.com/BernoulliDistribution.html)