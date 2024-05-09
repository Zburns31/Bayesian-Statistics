# Empirical CDF & Probability Integral Transform

- If you have a random variable $X$ and you apply its own cumulative distribution function (CDF) to it:

$$
Y = F_X(X)
$$

- The resulting random variable $Y$ will be $U(0, 1)$ distributed. We can use this idea to check our model's fit by taking our sample's response variable values and running them through the posterior CDF
    - We only have samples from our posterior rather than an actual CDF function, so we'll need to use the ***Empirical CDF (ECDF)***

## The Empirical CDF

- Remember the CDF is the function that maps a maps a number $x$ to the probability that the random variable $X$ takes on a value less than or equal to $x$:

$$
F_X(x) = p(X \le x)
$$

- So the ECDF is just the probability that some number $x$ is less than

$$
F_X(X=x) = \frac{1}{n}\sum\limits_{i=1}^{n}\mathbf{1}(X_i \le x)
$$

- where $\mathbf{1}(X_i \le x)$ is an indicator function that evaluates to 1 if $(X_i \le x)$ is true, otherwise 0
    - In other words, we count the number of samples less than $x$ and divide by $n$ to get the probability

## The test(s)

- Once we've evaluated the ECDF at each original $y$ value from our sample's response variable, we need some way to compare the output of $F_X(x)$ to a standard uniform distribution
    - Values extremely close to 0 or 1 will indicate outliers
    - We can also apply a transformation to the values to make the outliers stand out more:

        $$
         \log\left(\frac{p}{1-p}\right)^2
        $$

        - This is the square of the logit function. ***The purpose of the logit function is to map probabilities to real values***
        - We then square that to make extreme values stand out more

# Leave-One-Out Cross Validation: Pareto K Estimates

- [The Pareto K diagnostic estimates how much the individual leave-one-out distribution deviates from the full distribution2](https://mc-stan.org/loo/reference/loo-glossary.html). [If leaving out an observation changes the posterior too much, then importance sampling is not able to give a reliable estimate](https://mc-stan.org/loo/reference/loo-glossary.html)
- [The interpretation of the Pareto K values is as follows3](https://cran.r-project.org/web/packages/loo/vignettes/loo2-weights.html)[4](https://mc-stan.org/loo/articles/loo2-moment-matching.html):
    - **(-Inf, 0.5]**: The estimates are good
        - [The corresponding component of elpd_loo is estimated with high accuracy](https://mc-stan.org/loo/reference/loo-glossary.html)
    - **(0.5, 0.7]**: The estimates are okay](https://arxiv.org/pdf/1507.04544.pdf)
    - **(0.7, 1]**: The estimates are bad](https://arxiv.org/pdf/1507.04544.pdf)
    - **(1, Inf)**: The estimates are very bad](https://arxiv.org/pdf/1507.04544.pdf)
- In other words, if the Pareto K value is less than 0.5, the corresponding component of elpd_loo is estimated with high accuracy
    - If the K value is between 0.5 and 0.7, the estimates are considered okay. [If the K value is greater than 0.7, the estimates are considered unreliable](https://mc-stan.org/loo/reference/loo-glossary.html)