# What is it?

- The Weibull distribution is one of the most important distributions in survival theory and engineering reliability
- The Weibull distribution is a continuous probability distribution that can fit an extensive range of distribution shapes
    - Like the normal distribution, the Weibull distribution is [unimodal](https://statisticsbyjim.com/basics/unimodal-distribution/) and describes probabilities associated with [continuous data](https://statisticsbyjim.com/glossary/continuous-variables/)
    - However, unlike the normal distribution, it can also model skewed data. In fact, its extreme flexibility allows it to model both left and right-skewed data

# How it works

- The failure rate is determined by the value of the shape parameter $\lambda$
    - If $\lambda$ < 1, then the **failure rate decreases with time**
    - If $\lambda$ = 1, then the **failure rate is constant**
    - If $\lambda$ > 1, the **failure rate increases with time**
- **Parameters**
    - $r$ = Shape parameter
        - Also called as the Weibull slope or the threshold parameter
    - $\lambda$ = Rate parameter
        - Also called the waiting time parameter or sometimes the shift parameter
    - $\alpha$ = Scale Parameter
        - Also known as characteristic life parameter
    - Both of these parameters are strictly positive

## Probability Density Function

- The PDF of the three-parameter Weibull distribution is given as:

$$
f(x) = \dfrac{\lambda}{\alpha}(\dfrac{x-\mu}{\alpha})^{(\gamma - 1)} e^{-(\frac{x}{\alpha})^\lambda}
$$

- The PDF of the two-parameter Weibull distribution is given as:

$$
f_X(x) = \lambda rx^{r-1}e^{-\lambda x^r}, \space x>0
$$

- Note that the two-parameter distribution is the same as the three-parameter distribution but without the location

## Cumulative Density Function (CDF)

- The CDF is given as:

$$
F_X(x) = 1-e^{-\lambda x^r}
$$

# Numerical Characteristics

### BUGS

- **PDF:** $f(x|r, \lambda) = \lambda r x^{r-1} e^{-\lambda x^r}, \space \text{for x} > 0$
- **CDF:** $F(x|r, \lambda) = 1 - e^{-\lambda x^r}$
- **Mean:** $\lambda^{-\frac{1}{r}} \Gamma\left(1 + \frac{1}{r}\right)$
- **Variance:** $\frac{\Gamma(1+2/r) - [\Gamma(1+1/r)]^2}{\lambda^{2/r}}$
- **Parameters:** $r$ (shape parameter), $\lambda$ (rate parameter)
- **Support:** $(0, \infty)$
- **Notation:** $X \sim Weibull(r, \lambda)$

### PyMC

- **PDF:** $f(x|\alpha, \beta) = \frac{\alpha x^{\alpha - 1} e^{-(x/\beta)^{\alpha}}}{\beta^\alpha}, \space \text{for x} > 0$
- **CDF:** $F(x|\alpha, \beta) = 1 - e^{-(x/\beta)^\alpha} \space \text{ for x} > 0$
- **Mean:** $\beta \Gamma(1 + \frac{1}{\alpha})$
- **Variance:** $\beta^2 \Gamma(1+2/\alpha - \mu^2/\beta^2)$
- **Parameters:** $\alpha$ (shape parameter, $\alpha > 0$), $\beta$ (scale parameter, $\beta > 0$)
    - $\alpha = r$
    - $\beta = \lambda^{-1/\alpha}$
- **Notation:** $X \sim Weibull(\alpha, \beta)$

# Example Problem Types

- [Reliability for K out of N Systems](https://egyankosh.ac.in/bitstream/123456789/35169/1/Unit-15.pdf)

# Resources

- [https://mathworld.wolfram.com/WeibullDistribution.html](https://mathworld.wolfram.com/WeibullDistribution.html)
- [https://stats.libretexts.org/Bookshelves/Probability_Theory/Probability_Mathematical_Statistics_and_Stochastic_Processes_(Siegrist)/05%3A_Special_Distributions/5.38%3A_The_Weibull_Distribution](https://stats.libretexts.org/Bookshelves/Probability_Theory/Probability_Mathematical_Statistics_and_Stochastic_Processes_(Siegrist)/05%3A_Special_Distributions/5.38%3A_The_Weibull_Distribution)