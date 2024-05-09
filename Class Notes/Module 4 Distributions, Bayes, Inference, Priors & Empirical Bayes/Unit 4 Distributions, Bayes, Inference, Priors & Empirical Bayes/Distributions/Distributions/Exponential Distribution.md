# What is it?

- In Probability theory and statistics, the exponential distribution is a continuous [probability distribution](https://byjus.com/maths/probability-distribution/) that often concerns the amount of time until some specific event happens
    - It is a process in which events happen continuously and independently at a constant average rate. The exponential distribution has the key property of being memoryless
    - The exponential random variable can be either more small values or fewer larger variables
        - For example, the amount of money spent by the customer on one trip to the supermarket follows an exponential distribution
- Just so, the Poisson distribution deals with the number of occurrences in a fixed period of time, and the exponential distribution deals with the time between occurrences of successive events as time flows by continuously
- The exponential distribution is frequently used to provide probabilistic answers to questions such as:
    - How much time will elapse before an earthquake occurs in a given region?
    - How long do we need to wait until a customer enters our shop?
    - How long will it take before a call centre receives the next phone call?
    - How long will a piece of machinery work without breaking down?

![Untitled](./Exponential%20Distribution/Untitled.png)

![Untitled](./Exponential%20Distribution/Untitled%201.png)

# When to use?

- The exponential distribution assumes that small values occur more frequently than large values
    - Consequently, it can model things like wait times, transaction times, and failure times
    - It can also model other variables, such as the size of orders at convenience stores
- This distribution assumes that the average time between events remains constant
    - Consequently, you cannot use the exponential distribution when the expected time for events increases or decreases as time passes
    - For instance, machines tend to wear out over time, causing failure rates to increase as time passes

# Probability Density Function

$$
f(x) = \begin{cases}
   \lambda e^{-\lambda x} & x \ge 0 \\
   0 & x < 0
\end{cases}
$$

- Where:
    - $\lambda$ is the distribution (Or also known as rate) parameter
- The exponential distribution is sometimes parametrized in terms of the [scale parameter](https://en.wikipedia.org/wiki/Scale_parameter) $*β = 1/λ*$, which is also the mean

$$
f(x) = \begin{cases}
   \dfrac{1}{\beta} e^{-\frac{x}{\beta}} & x \ge 0 \\
   0 & x < 0
\end{cases}
$$

# Likelihood Function

- Likelihood function for multiple data points

$$
L(\lambda|x_1, x_2, ..., x_n) = \lambda^ne^{-\lambda \sum_{i=1}^n x_i}
$$

- Due to the logarithm being strictly increasing, the maximum of $L$ occurs at the same location as the maximum of $log(L)$. So we take the logarithm first to make the algebra easier:

$$
n \ln(\lambda) -\sum_{i=1}^n t_i
$$

# Maximum Likelihood Estimate

$$
\begin{align*}
E(\hat \lambda) &= \dfrac{n}{\sum_{i=1}^{n} x_i} \\
&= \dfrac{1}{\bar X} \\
\end{align*}
$$

- Where $\bar X$ represents the sample mean

# Numerical Characteristics

- **PDF:** $f(x|\lambda) = \lambda e^{-\lambda x}$
- **CDF:** $F(x|\lambda) = 1 - e^{-\lambda x}$
- **Mean:** $\frac{1}{\lambda}$
- **Variance:** $\frac{1}{\lambda^2}$
- **Support:** $(0, \infty)$
- **Parameters:** $\lambda$ (rate)
- **Notation:** $X \sim Exp(\lambda)$

# Files

- [OH3.pdf](./Exponential%20Distribution/OH3.pdf)

# Resources

- [https://en.wikipedia.org/wiki/Exponential_distribution](https://en.wikipedia.org/wiki/Exponential_distribution)
- [https://byjus.com/maths/exponential-distribution/](https://byjus.com/maths/exponential-distribution/)
- [https://www.statlect.com/probability-distributions/exponential-distribution](https://www.statlect.com/probability-distributions/exponential-distribution)
- [https://statisticsbyjim.com/probability/exponential-distribution/](https://statisticsbyjim.com/probability/exponential-distribution/)
- [https://www.probabilitycourse.com/chapter4/4_2_2_exponential.php](https://www.probabilitycourse.com/chapter4/4_2_2_exponential.php)
- [https://www.kellogg.northwestern.edu/faculty/weber/decs-430/Notes on the Poisson and exponential distributions.pdf](https://www.kellogg.northwestern.edu/faculty/weber/decs-430/Notes%20on%20the%20Poisson%20and%20exponential%20distributions.pdf)
- [https://www.statlect.com/fundamentals-of-statistics/exponential-distribution-maximum-likelihood](https://www.statlect.com/fundamentals-of-statistics/exponential-distribution-maximum-likelihood)

### MLE

- [https://math.stackexchange.com/questions/101481/calculating-maximum-likelihood-estimation-of-the-exponential-distribution-and-pr](https://math.stackexchange.com/questions/101481/calculating-maximum-likelihood-estimation-of-the-exponential-distribution-and-pr)
- [https://www.quantrocket.com/code/?repo=quant-finance-lectures&path=%2Fcodeload%2Fquant-finance-lectures%2Fquant_finance_lectures%2FLecture13-Maximum-Likelihood-Estimation.ipynb.html](https://www.quantrocket.com/code/?repo=quant-finance-lectures&path=%2Fcodeload%2Fquant-finance-lectures%2Fquant_finance_lectures%2FLecture13-Maximum-Likelihood-Estimation.ipynb.html)
- [https://stats.stackexchange.com/questions/497086/how-to-find-a-good-estimator-for-lambda-in-exponential-distibution](https://stats.stackexchange.com/questions/497086/how-to-find-a-good-estimator-for-lambda-in-exponential-distibution)
- [Computing in Python](https://radzion.com/blog/probability/maximum)

### Conjugacy

- [https://people.eecs.berkeley.edu/~jordan/courses/260-spring10/other-readings/chapter9.pdf](https://people.eecs.berkeley.edu/~jordan/courses/260-spring10/other-readings/chapter9.pdf)
- [https://seor.vse.gmu.edu/~klaskey/SYST664/Bayes_Unit3.pdf](https://seor.vse.gmu.edu/~klaskey/SYST664/Bayes_Unit3.pdf)
- [https://math.stackexchange.com/questions/4709192/numerical-values-of-parameters-of-posterior-distribution](https://math.stackexchange.com/questions/4709192/numerical-values-of-parameters-of-posterior-distribution)
- [https://bookdown.org/aramir21/IntroductionBayesianEconometricsGuidedTour/sec42.html](https://bookdown.org/aramir21/IntroductionBayesianEconometricsGuidedTour/sec42.html)
- [https://stats.stackexchange.com/questions/548075/what-is-the-posterior-distribution-of-θ-is-the-gamma-a-conjugate-prior-for-an-e](https://stats.stackexchange.com/questions/548075/what-is-the-posterior-distribution-of-%CE%B8-is-the-gamma-a-conjugate-prior-for-an-e)

### Inverse Gamma

- [https://www.jarad.me/courses/stat587Eng/slides/Probability/Distributions/Inverse_gamma/Inverse_gamma.pdf](https://www.jarad.me/courses/stat587Eng/slides/Probability/Distributions/Inverse_gamma/Inverse_gamma.pdf)