# What is it?

- In [mathematics](https://en.wikipedia.org/wiki/Mathematics), **Laplace's method**, named after [Pierre-Simon Laplace](https://en.wikipedia.org/wiki/Pierre-Simon_Laplace), is a technique used to approximate [integrals](https://en.wikipedia.org/wiki/Integral) of the form:

    $$
    \int_a^b e^{Mf(x)} dx
    $$

    - Where $f(x)$ is a twice-[differentiable](https://en.wikipedia.org/wiki/Derivative) [function](https://en.wikipedia.org/wiki/Function_(mathematics)), $*M*$ is a large number, and the endpoints $*a*$ and $*b*$ could possibly be infinite
- In [Bayesian statistics](https://en.wikipedia.org/wiki/Bayesian_statistics), [Laplace's approximation](https://en.wikipedia.org/wiki/Laplace%27s_approximation) can refer to either approximating the [posterior normalizing constant](https://en.wikipedia.org/wiki/Normalizing_constant) with Laplace's method[[1]](https://en.wikipedia.org/wiki/Laplace%27s_method#cite_note-1) or approximating the posterior distribution with a [Gaussian](https://en.wikipedia.org/wiki/Normal_distribution) centered at the [maximum a posteriori estimate](https://en.wikipedia.org/wiki/Maximum_a_posteriori_estimation)
- **The general idea is to take a well-behaved unimodal function and approximate it with a Normal density function**, which is a very well-understood quantity using only the likelihood and prior ($g(\theta) = f(x|\theta)\pi(\theta)$) (we are missing the normalizing constant)

# Requirements

- $g(\theta)$ is unimodal, not too skewed
- $\hat \theta$ is the mode of $g(\theta)$
- $\theta$ possibly multivariate

# How does it work?

Here's a step-by-step explanation of Laplace's method:

1. **Setup**: Suppose you have a Bayesian model with a parameter of interest, $θ$, and a likelihood function, $L(θ)$, and a prior distribution, $π(θ)$
2. **Posterior Distribution**: The posterior distribution, $π(θ | data)$, represents your updated beliefs about $θ$ after observing the data. It is proportional to the product of the likelihood and prior: $π(θ | data) ∝ L(θ) * π(θ)$
3. **Find the Mode**: First, you find the mode of the posterior distribution, which is the value of $θ$ that maximizes the posterior density. Mathematically, you solve for $θ_{mode}$ in the equation $∇ log(π(θ | data)) = 0$, where $∇$ represents the gradient
4. **Second Derivatives**: Calculate the second derivatives of the log posterior density with respect to $θ$ at the mode. This involves finding the Hessian matrix, which contains the second partial derivatives of the log posterior density
    1. Denote the Hessian matrix as $H(θ_{mode})$
5. **Approximate with a Gaussian**: Laplace's method approximates the posterior distribution as a multivariate Gaussian with mean at $θ_{mode}$ and covariance matrix equal to the inverse of the negative Hessian at $θ_{mode}: N(θ_{mode}, [H(θ_{mode})]^{(-1)})$

# Laplace Formula

- For a univariate parameter $\theta$

$$
Q = \Bigg [-\dfrac{\partial^2}{\partial \theta^2} \log g(\theta) \Bigg ]_{\theta = \hat \theta}
$$

# Resources

- [https://en.wikipedia.org/wiki/Laplace's_method](https://en.wikipedia.org/wiki/Laplace%27s_method)
- [https://bookdown.org/rdpeng/advstatcomp/laplace-approximation.html](https://bookdown.org/rdpeng/advstatcomp/laplace-approximation.html)
- [https://francisbach.com/laplace-method/](https://francisbach.com/laplace-method/)
- [https://james-brennan.github.io/posts/laplace_approximation/](https://james-brennan.github.io/posts/laplace_approximation/)
- [https://forem.julialang.org/mroavi/the-laplace-approximation-part-1-2cob](https://forem.julialang.org/mroavi/the-laplace-approximation-part-1-2cob)