# Numerical Characteristics

## What are Moments?

- Moments in statistics are quantitative measure that describes the specific characteristics of a [probability distribution](https://www.shiksha.com/online-courses/articles/probability-distributions-used-in-data-science/). It helps to understand the data set’s shape, spread, and [central tendency](https://www.shiksha.com/online-courses/articles/measures-of-central-tendency-mean-median-and-mode/)
- In simple terms, the moment is a way to measure how spread out or concentrated the number in a dataset is around the central value, such as the mean

## Key Moments

1. **First Moment - Expectation (Expected Value)**
    1. Mean is the most commonly used measure of central tendency. It gives us an idea of where the data is centered in a distribution
2. **Second moment - Variance (Central Moment)**
    1. Variance measures how to spread out or dispersed the data is around its mean value

    $$
    Var(X) = E(X-EX)^2 = EX^2 - (EX)^2
    $$

3. **Third moment - Skewness**
    1. Skewness measures the asymmetry of a distribution; it tells us if there are more values on one side than another side of the distribution (positively skewed, negatively skewed, or symmetric)
        1. A positive value of skew represents right-skewed distributions, a negative value of skew represents left-skewed distributions and a zero value of skewness indicates that the distribution is symmetric
4. **Fourth moment - Kurtosis**
    1. Kurtosis measures the peakedness or flatness of a distribution; it tells us how much weight is at the center and tail ends of the distribution (leptokurtic, platykurtic, or mesokurtic)
        1. Positive kurtosis indicates that the data is more concentrated near the mean than in a normal distribution, while negative kurtosis indicates that the data is spread out more than in a normal distribution
5. **Standard Deviation (SD): $\sigma = \sqrt{Var(X)}$**
6. **Quantiles**
    1. $\varepsilon_p$ is the $p^{th}$ quantile of distribution F if $F(\varepsilon_p) = p$
        1. $\varepsilon_p = \inf \lbrace x| \sum_{x_i \le x} p_i \ge p \rbrace$ —> Discrete
        2. $\int^{\varepsilon_p}_0 f(x)dx = p \space \text{or} \space F^{-1}(p) = \varepsilon_p$
    2. Median —> 50% percentile
    3. $Q_1, Q_3$ are the first and 3 quantiles
    4. Mode: Most frequent/likely
        1. Continuous: Value that maximizes density
        2. Discrete: Value $x_i$ for which $p_i = P(X = x)$ is maximum

## Kth Moment

- Discrete: $EX^k = x_1^kp_1 + x_2^kp_2 + ... + x_n^kp_n$
- Continuous: $\int_\real x^k \cdot f(x)dx$

## General Function

- Discrete: $E\phi(X) = \phi(x_1)p_1 + \phi(x_2)p_2 + ... + \phi(x_n)p_n$
- Continuous: $\int_\real \phi(x) \cdot f(x)dx$

## Different Types of Moments

- **Raw Moments**
    - The raw moment or the nth moment about zero of a probability density function f(x) is the expected value of $X^n$
        - It is also known as the Crude moment
- **Centred Moments**
    - A central moment is a moment of a probability distribution of a random variable defined about the mean of the random variable’s
        - i.e, it is the expected value of a specified integer power of the deviation of the random variable from the mean
- **Standardized Moments**
    - A standardized moment of a probability distribution is a moment that is normally a higher degree central moment, but it is normalized typically by dividing the standard deviation which renders the moment scale-invariant

## Resources

- [https://gregorygundersen.com/blog/2020/04/11/moments/](https://gregorygundersen.com/blog/2020/04/11/moments/)
- [https://vitalflux.com/types-uses-of-moments-in-statistics/](https://vitalflux.com/types-uses-of-moments-in-statistics/)
- [https://www.shiksha.com/online-courses/articles/moments-in-statistics/](https://www.shiksha.com/online-courses/articles/moments-in-statistics/)
- [https://matthewcaseres.github.io/omscs_bayesian_statistics/u4l1-random-variable-properties.html](https://matthewcaseres.github.io/omscs_bayesian_statistics/u4l1-random-variable-properties.html)