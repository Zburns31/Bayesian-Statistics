# What are they?

- The difference between confidence intervals and credible sets is a great entry point into the philosophical differences between frequentist and Bayesian reasoning
    - This [Stack Exchange](https://stats.stackexchange.com/questions/2272/whats-the-difference-between-a-confidence-interval-and-a-credible-interval) post is a great read on the subject
- A confidence interval has the form of an upper and lower bound.

    $$
    L,U=pe±se×cv
    $$

    - where $L, U$ are the lower bound and upper bound of the confidence interval respectively, $pe$ represents “point estimates”, $se$ is the standard error, and $cv$ is the critical value
- Most importantly, the interpretation of a 95% confidence interval on the mean is that **“95% of similarly constructed intervals will contain the true mean”**, not “the probability that true mean lies between $L$ and $U$ is 0.95”
    - The reason for this frequentist wording is that a frequentist may not express his uncertainty as a probability. The true mean is either within the interval or not, so the probability is zero or one. The problem is that the frequentist does not know which is the case
- On the other hand, Bayesians have no such qualms. It is fine for us to say that **“the probability that the true mean is contained within a given interval is 0.95”**
    - To distinguish our intervals from confidence intervals, we call them **credible intervals**

# How do they work?

- A Bayesian credible interval of size $1 − α$ is an interval $(a, b)$ such that:

$$
P(a \le \theta \le b |x) = 1 - \alpha
\\
\newline

\int_a^bp(\theta|x) d \theta = 1 - \alpha
$$

# Types of Credible Sets

- Highest Posterior Density (HPD) Credible Sets
- Equitailed Credible Sets

# Highest Posterior Density (HPD) Credible Sets

- A **highest posterior density** (**HPD**) region of confidence level $α$ is a $(1−α)$ confidence region $I_α$ for which holds that the posterior density for every point in this set is higher than the posterior density for any point outside of this set
- Choosing the narrowest interval, which for a [unimodal distribution](https://en.wikipedia.org/wiki/Unimodal_distribution) will involve choosing those values of highest probability density including the [mode](https://en.wikipedia.org/wiki/Mode_(statistics)) (the *[maximum a posteriori](https://en.wikipedia.org/wiki/Maximum_a_posteriori)*)
    - This is the narrowest credible interval that is comprised of 95% of this distribution’s density mass
- [Good Reference](https://sam-brady.medium.com/the-best-reason-to-practice-bayesian-statistics-that-you-havent-heard-of-yes-you-4bb37dbeceae)

    ![Untitled](./Credible%20Sets/Untitled.png)


# Equitailed Credible Sets (ETI)

- Contrary to the **HDI**, for which all points within the interval have a higher probability density than points outside the interval, the **ETI** is **equal-tailed**
    - This means that a 90% interval has 5% of the distribution on either side of its limits
    - It indicates the 5th percentile and the 95th percentile. In symmetric distributions, the two methods of computing credible intervals, the ETI and the HDI, return similar results
    - ***This is not the case for skewed distributions***
        - Indeed, it is possible that parameter values in the ETI have lower credibility (are less probable) than parameter values outside the ETI. This property seems undesirable as a summary of the credible values in a distribution
- An **equal-tailed interval** (also called a **central interval**) of confidence level $α$ is an interval $I_α=[q_α/2,q_{1-α/2}]$, where $q_z$ is a $z$ quantile (remember that we assumed the parameter to be have a continuous distribution; this means that the quantiles are always defined) of the posterior distribution
    - For instance, 95% equal-tailed interval is an interval $I_{0.05}=[q_{0.025},q_{0.975}]$, where $q_{0.025}$ and $q_{0.975}$ are the quantiles of the posterior distribution
    - This is an interval on whose both right and left side lies 2.5% of the probability mass of the posterior distribution
- Usually, when a credible interval is mentioned without specifying which type of the credible interval it is, an equal-tailed interval is meant

    ![Untitled](./Credible%20Sets/Untitled%201.png)


# Tips & Tricks

- Check [here](https://areding.github.io/6420-pymc/unit4/Unit4-crediblesets.html) and [here](https://areding.github.io/6420-pymc/unit4/Unit4-GammaGamma.html) for notes on credible sets. If you have a known posterior you can use the inverse CDF to find the equitailed credible set

# Resources

- [https://easystats.github.io/bayestestR/articles/credible_interval.html](https://easystats.github.io/bayestestR/articles/credible_interval.html)
- [https://www2.stat.duke.edu/~rcs46/lecturesModernBayes/601-module3-morebayes/lecture5-more-bayes.pdf](https://www2.stat.duke.edu/~rcs46/lecturesModernBayes/601-module3-morebayes/lecture5-more-bayes.pdf)
- [https://people.stat.sc.edu/hitchcock/slides535day4spr2014.pdf](https://people.stat.sc.edu/hitchcock/slides535day4spr2014.pdf)
- [https://vioshyvo.github.io/Bayesian_inference/summarizing-the-posterior-distribution.html#credible-intervals](https://vioshyvo.github.io/Bayesian_inference/summarizing-the-posterior-distribution.html#credible-intervals)
- [https://courses.cs.washington.edu/courses/cse312/20su/files/student_drive/8.2.pdf](https://courses.cs.washington.edu/courses/cse312/20su/files/student_drive/8.2.pdf)

### HPD Credible Intervals

- [https://sam-brady.medium.com/the-best-reason-to-practice-bayesian-statistics-that-you-havent-heard-of-yes-you-4bb37dbeceae](https://sam-brady.medium.com/the-best-reason-to-practice-bayesian-statistics-that-you-havent-heard-of-yes-you-4bb37dbeceae)
- [https://stats.stackexchange.com/questions/148439/what-is-a-highest-density-region-hdr](https://stats.stackexchange.com/questions/148439/what-is-a-highest-density-region-hdr)