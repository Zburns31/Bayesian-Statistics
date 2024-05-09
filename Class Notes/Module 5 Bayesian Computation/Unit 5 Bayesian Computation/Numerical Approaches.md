# Why exact methods don’t always work

- Numerical methods in Bayesian computation refer to a set of techniques and algorithms used to perform computations related to Bayesian inference when analytical solutions are not feasible or practical
- Bayesian inference is a statistical framework for updating beliefs or making predictions about uncertain quantities based on prior knowledge and observed data. Numerical methods become necessary in many Bayesian problems because the posterior distributions, which represent updated beliefs after incorporating data, are often complex and analytically intractable
- For Bayesian stats, the posterior is represented by the posterior $\propto$ likelihiood x prior but ***needs to be normalized by the marginal***
    - This integral is often unfeasible and/or intractable
    - We could avoid integrating in the case of conjugate priors
- In non-conjugate cases, we typically compute the posterior either by numerical integration for $m(x)$, or by sampling

# Moving Beyond Conjugate Cases

- When we move beyond conjugate cases, we might possess the posterior in an analytical form due to Bayes’ theorem
- However, this will not represent any recognizable distribution, irrespective of how we manipulate it
- Many normalizing constants lack a closed-form solution. As illustrated in lessons 2 and 4 of this unit, we can attempt to numerically approximate these constants, but this method can be imprecise or computationally intractable. The time complexity increases exponentially with the number of parameters, as shown in section 2.1 of [[Blei *et al.*, 2017](https://areding.github.io/6420-pymc/backmatter/bibliography.html#id22)], linked [here](https://arxiv.org/pdf/1601.00670.pdf)

# Bayesian Vs. Frequentist Key Tools

- The main tools for each framework are:
    - Classical Statistics $\rightarrow$ Optimization
    - Bayesian Statistics $\rightarrow$ Integration

# Normal-Cauchy Pair

- Assume $x|\theta \sim N(\theta,1) \text{ and } \theta \sim Cau(0,1)$
- Likelihood is $f(x|\theta) \propto e^{-\frac{1}{2}(x-\theta)^2}$
- Prior is $\pi(\theta) \propto \dfrac{1}{1+\theta^2}$

## Steps

To solve for the marginal, we take the integral of the prior and likelihood:

$$
\int_{-\infty}^{\infty} e^{1\frac{1}{2}(x-\theta)^2} \dfrac{d\theta}{1+\theta^2}
$$

Which is not solvable in terms of elementary functions. What do we do if we need to find the Bayes Estimator?

$$
\delta_B = \dfrac{\int_{\Theta}\theta f(x|\theta)\pi(\theta)d\theta}{\int_\Theta f(x|\theta)\pi(\theta)d\theta}
$$

We can also do this via sampling in 2 ways:

1. Sample from the likelihood
2. Sample from the prior

    ![Untitled](./Numerical%20Approaches/Untitled.png)


- [Python Breakdown](https://areding.github.io/6420-pymc/unit5/Unit5-norcau1.html)