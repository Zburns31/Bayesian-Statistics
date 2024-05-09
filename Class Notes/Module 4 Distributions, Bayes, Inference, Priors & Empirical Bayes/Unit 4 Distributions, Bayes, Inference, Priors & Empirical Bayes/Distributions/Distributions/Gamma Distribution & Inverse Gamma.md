# Gamma Distribution

- The gamma distribution is another widely used distribution. Its importance is largely due to its relation to exponential and normal distributions
- The **gamma distribution** is a generalization of the [exponential distribution](https://brilliant.org/wiki/exponential-distribution/) that models the amount of time between events in an otherwise [Poisson process](https://brilliant.org/wiki/poisson-distribution/) in which the event rate is not necessarily constant
    - It is also used to model the amount of time before the $k^{th}$ event in a Poisson process, equivalent to the note that the sum of exponential distributions is a gamma distribution
- The gamma distribution is often used to model waiting times, particularly in the case of lifespan testing in which the "waiting time" until death is modelled by a gamma distribution
    - It is also commonly used in applied fields such as finance, civil engineering, climatology (e.g. in estimating rainfall), and econometrics
- The gamma distribution is a continuous probability distribution that models right-skewed data

## How it works

- Gamma distributions have two free parameters, named as alpha ($α$) and beta ($β$), where:
    - $\alpha$ = Shape Parameter
    - $\beta$ = Rate Parameter
        - The reciprocal of the scale parameter
        - The scale parameter $\beta$ is used only to scale the distribution
            - This can be understood by remarking that wherever the random variable $x$ appears in the probability density, then it is divided by $\beta$
            - Since the scale parameter provides the dimensional data, it is seldom useful to work with the “standard” gamma distribution, i.e., with $\beta$ = 1
- The scale $\beta$ parameter represents the variability present in the gamma distribution
    - Higher values cause the distribution to expand further right and decrease the height. Conversely, lower values contract the distribution to the left and increase its peak
    - Alternatively, if you use the rate form of the parameter, higher rates shrink the distribution while lower rates spread it out

## Parameters

- **Shape Parameter - $\alpha$:**
    - The shape parameter for the gamma distribution specifies the number of events you are modelling
        - For example, if you want to evaluate probabilities for the elapsed time of three accidents, the shape parameter equals 3. Shape must be positive, but it does not have to be an integer
- **Scale Parameter** - $\beta$:
    - The scale parameter for the gamma distribution represents the mean time between events
        - For example, if you measure the time between accidents in days and the scale parameter equals 4, there are four days between accidents on average
- **Rate Parameter** - $\lambda$
    - Alternatively, analysts can use the rate form of the scale parameter, lambda ($λ$), for the gamma distribution
        - Lambda is also the mean rate of occurrence during one unit of time in the Poisson distribution
    - Use the following equations to convert between the scale ($β$) and rate ($λ$) forms:
        - $\beta = \dfrac{1}{\lambda}$
        - $\lambda = \dfrac{1}{\beta}$
        - They are reciprocals. To understand why let’s return to our example of one accident occurring every four days on average (β = 4). An equivalent way to state it is that an average of one-quarter accident occurs during one day (λ = 1 / 4 = 0.25)
- Location Parameter - $\mu$

## Properties

- The parameters of the gamma distribution define the shape of the graph. Shape parameter $\alpha$ and rate parameter $\beta$ are both greater than 1:
    - When $\alpha$ = 1, this becomes the exponential distribution
    - When $\beta$ = 1 this becomes the standard gamma distribution

        ![Untitled](./Gamma%20Distribution%20&%20Inverse%20Gamma/Untitled.png)


# Parameterizations

## Scale Parameterization

- There are multiple parameterizations of the gamma distribution. The first is the $**k−θ**$ parametrization and perhaps is the more natural one, with p.d.f:

    $$
    F(x) = \dfrac{1}{\Gamma(\alpha)\beta^\alpha}\cdot x^{\alpha-1} \cdot e^{\frac{-x}{\beta}}
    $$

    - Here $\alpha$ is the **shape parameter,** $\beta$ is the **scale parameter and $\Gamma$** is the gamma function

## Rate Parameterization

- The alternative parametrization, the $**α−β**$ parametrization, is commonly used in [Bayesian statistics](https://brilliant.org/wiki/bayesian-theory-in-science-and-math/) as a [conjugate prior](https://brilliant.org/wiki/conjugate-prior/?wiki_title=conjugate%20prior) for rate parameters in distributions such as the [exponential distribution](https://brilliant.org/wiki/exponential-distribution/) and the gamma distribution itself. It has p.d.f:

    $$
    F(x) = \dfrac{\beta^\alpha}{\Gamma(\alpha)} \cdot x^{\alpha -1} \cdot e^{-\beta x}
    $$

    - which simply makes the substitution $β=θ$ and $α=k$ and is thus not so independently interesting
        - Here $α$ is the **shape parameter** and $β$ is the **inverse scale parameter** (also **rate parameter**)

## Numerical Characteristics

- **PDF:** $f(x|\alpha,\beta) = \frac{\beta^\alpha}{\Gamma(\alpha)}x^{\alpha-1}e^{-\beta x}$
- **CDF:** $F(x|\alpha,\beta) = \frac{\gamma(\alpha, \beta x)}{\Gamma(\alpha)}$
- **Mean:** $\frac{\alpha}{\beta}$
- **Mode:**  $\frac{\alpha - 1}{\beta}$
- **Variance:** $\frac{\alpha}{\beta^2}$
- **Support:** $(0, \infty)$
- **Parameters:** $\alpha$ (shape), $\beta$ (rate)
- **Notation:** $X \sim Ga(\alpha, \beta)$

# Inverse Gamma Distribution

# Precision

- [Precision](https://stats.stackexchange.com/questions/183522/antonym-of-variance/183523#183523) is often used in Bayesian software by convention. It gained popularity because gamma distribution can be used as a [conjugate prior for precision](https://stats.stackexchange.com/questions/161328/why-use-precision-instead-of-variance-in-a-prior/161329#161329)
    - Some say that precision is more "intuitive" than variance because it says *how concentrated* are the values around the mean rather than *how spread* they are
    - It is said that we are more interested in how precise is some measurement rather than how imprecise it is (but honestly I do not see how it would be more intuitive).
- The more spread are the values around the mean (high variance), the less precise they are (small precision). The smaller the variance, the greater the precision. Precision is just an inverted variance $*\tau =1/\sigma2*$
- [Reference](https://stats.stackexchange.com/questions/211419/whats-in-a-name-precision-inverse-of-variance)

# Resources

### Gamma Distribution

- [https://byjus.com/maths/gamma-distribution/](https://byjus.com/maths/gamma-distribution/)
- [https://www.itl.nist.gov/div898/handbook/eda/section3/eda366b.htm](https://www.itl.nist.gov/div898/handbook/eda/section3/eda366b.htm)
- [https://statisticsbyjim.com/probability/gamma-distribution/](https://statisticsbyjim.com/probability/gamma-distribution/)
- [https://en.wikipedia.org/wiki/Gamma_distribution](https://en.wikipedia.org/wiki/Gamma_distribution)
- [Gamma Function](https://math.libretexts.org/Bookshelves/Analysis/Complex_Variables_with_Applications_(Orloff)/14%3A_Analytic_Continuation_and_the_Gamma_Function/14.02%3A_Definition_and_properties_of_the_Gamma_function)

### Inverse Gamma Distribution

- [https://www.jarad.me/courses/stat587Eng/slides/Probability/Distributions/Inverse_gamma/Inverse_gamma.pdf](https://www.jarad.me/courses/stat587Eng/slides/Probability/Distributions/Inverse_gamma/Inverse_gamma.pdf)
- [https://www.statisticshowto.com/inverse-gamma-distribution/](https://www.statisticshowto.com/inverse-gamma-distribution/)
- [https://www.johndcook.com/inverse_gamma.pdf](https://www.johndcook.com/inverse_gamma.pdf)
- [https://handwiki.org/wiki/Inverse-gamma_distribution](https://handwiki.org/wiki/Inverse-gamma_distribution)

### Conjugacy

- [https://www.johndcook.com/inverse_gamma.pdf](https://www.johndcook.com/inverse_gamma.pdf)
- [https://seor.vse.gmu.edu/~klaskey/SYST664/Bayes_Unit3.pdf](https://seor.vse.gmu.edu/~klaskey/SYST664/Bayes_Unit3.pdf)
- [https://math.stackexchange.com/questions/4709192/numerical-values-of-parameters-of-posterior-distribution](https://math.stackexchange.com/questions/4709192/numerical-values-of-parameters-of-posterior-distribution)

## Notebooks & Tutorials

### Finding the Posterior

- [https://juanitorduz.github.io/intro_pymc3/](https://juanitorduz.github.io/intro_pymc3/)