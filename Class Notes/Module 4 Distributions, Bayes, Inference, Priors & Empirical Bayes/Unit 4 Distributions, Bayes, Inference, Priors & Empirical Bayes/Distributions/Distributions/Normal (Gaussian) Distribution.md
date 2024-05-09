# What is it?

- Normal distribution, also known as the Gaussian distribution, is a [probability distribution](https://www.investopedia.com/terms/p/probabilitydistribution.asp) that is symmetric about the mean, showing that data near the mean are more frequent in occurrence than data far from the mean

# Key Properties

Normal distributions have key characteristics that are easy to spot in graphs:

- The [mean](https://www.scribbr.com/statistics/mean/), [median](https://www.scribbr.com/statistics/median/) and [mode](https://www.scribbr.com/statistics/mode/) are exactly the same
- The distribution is symmetric about the mean—half the values fall below the mean and half above the mean
- The distribution can be described by two values: the mean and the [standard deviation](https://www.scribbr.com/statistics/standard-deviation/)
    - The mean ($\mu$) is the location parameter while the standard deviation ($\sigma$) is the scale parameter
- **Empirical Rule**
    - For all normal distributions, 68.2% of the observations will appear within plus or minus one standard deviation of the mean; 95.4% of the observations will fall within +/- two standard deviations; and 99.7% within +/- three standard deviations

        ![Untitled](./Normal%20(Gaussian)%20Distribution/Untitled.png)

- [Skewness](https://www.investopedia.com/terms/s/skewness.asp) measures the degree of symmetry of a distribution. The normal distribution is symmetric and has a skewness of zero
- [Kurtosis](https://www.investopedia.com/terms/k/kurtosis.asp) measures the thickness of the tail ends of a distribution in relation to the tails of a distribution. The normal distribution has a kurtosis equal to 3.0
    - Distributions with larger kurtosis greater than 3.0 exhibit tail data exceeding the tails of the normal distribution (e.g., five or more standard deviations from the mean). This [excess kurtosis](https://www.investopedia.com/terms/e/excesskurtosis.asp) is known in statistics as [leptokurtic](https://www.investopedia.com/terms/l/leptokurtic.asp), but is more colloquially known as "fat tails."

# Probability Density Function

### Univariate

Univariate Gaussian: $p(x) = \dfrac {1} {\sqrt{2\pi \sigma^2}} e^{\frac {-(x- \mu)^2} {2 \sigma^2}}, -\infin < x < +\infin, -\infin < \mu < +\infin, \sigma > 0$

### Bivariate PDF

### Precision ($\tau$) Parameterization

- Since $\sigma = \dfrac{1}{\sqrt{\tau}}$ (or equivalently $\tau = \dfrac{1}{\sigma^2}$), our new parameterization becomes:

    $$
    p(x) = \dfrac {1}{\dfrac{1}{\sqrt{\tau}} \sqrt{2\pi}} \cdot e^{-0.5\frac{(x-\mu)^2}{\frac{1}{\tau}}} = \dfrac {\sqrt{\tau}}{\sqrt{2\pi}} e^{-0.5 \tau(x-\mu)^2}
    $$


# Central Limit Theorem

- In its simplest form, it states that if a large number of independent random variables are drawn from any distribution, then the distribution of their sum (or alternatively their sample average) always converges to the Normal distribution
- Sample sizes equal to or greater than 30 are often considered sufficient for the CLT to hold
- A key aspect of CLT is that the average of the sample means and standard deviations will equal the population mean and standard deviation

# Numerical Characteristics

- **PDF (variance):** $f(x|\mu,\sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-(x-\mu)^2 / (2\sigma^2)}$
- **PDF (precision):** $f(x|\mu,\tau) = \sqrt{\frac{\tau}{2\pi}} e^{-(\tau/2) (x-\mu)^2}$
- **CDF:** $\Phi(x|\mu,\sigma) = \frac{1}{2}[1 + \text{erf}((x-\mu)/(\sigma\sqrt{2}))]$
- **Mean:** $\mu$
- **Variance:** $\sigma^2$
- **Support:** $(-\infty, \infty)$
- **Parameters:** $\mu (\text{mean}), \sigma^2 (\text{variance}), \tau (\text{precision, defined as} \space  \tau = 1/\sigma^2)$
- **Notation:** $X \sim N(\mu, \sigma^2)$

# Estimating Probabilities

![Untitled](./Normal%20(Gaussian)%20Distribution/Untitled1.png)

# References

- [https://www.mathsisfun.com/data/standard-normal-distribution.html](https://www.mathsisfun.com/data/standard-normal-distribution.html)

## Multivariate Gaussian Distributions

- [gaussians.pdf](./Normal%20(Gaussian)%20Distribution/gaussians.pdf)

- [https://peterroelants.github.io/posts/multivariate-normal-primer/](https://peterroelants.github.io/posts/multivariate-normal-primer/)
- [https://online.stat.psu.edu/stat505/book/export/html/636](https://online.stat.psu.edu/stat505/book/export/html/636)
- [https://distill.pub/2019/visual-exploration-gaussian-processes/](https://distill.pub/2019/visual-exploration-gaussian-processes/)
- [https://ardianumam.wordpress.com/2017/10/21/understanding-multivariate-gaussian-gaussian-prperties-and-gaussian-mixture-model/](https://ardianumam.wordpress.com/2017/10/21/understanding-multivariate-gaussian-gaussian-prperties-and-gaussian-mixture-model/)
- [https://www.mathsisfun.com/data/standard-normal-distribution.html](https://www.mathsisfun.com/data/standard-normal-distribution.html)
- [https://www.scribbr.com/statistics/normal-distribution/](https://www.scribbr.com/statistics/normal-distribution/)
- [https://www.khanacademy.org/math/statistics-probability/modeling-distributions-of-data/normal-distributions-library/a/normal-distributions-review](https://www.khanacademy.org/math/statistics-probability/modeling-distributions-of-data/normal-distributions-library/a/normal-distributions-review)