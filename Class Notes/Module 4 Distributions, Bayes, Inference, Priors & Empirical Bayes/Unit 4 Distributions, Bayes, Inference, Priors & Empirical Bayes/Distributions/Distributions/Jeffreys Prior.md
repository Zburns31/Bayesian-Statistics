# What is it?

- The Jeffreys prior is a non-informative prior distribution that is invariant under transformation (reparameterization)
- It is an [uninformative prior](https://www.statisticshowto.com/prior-probability-uniformative-conjugate/), which means that it gives you vague information about probabilities. It’s usually used when you don’t have a suitable [prior distribution](https://www.statisticshowto.com/prior-distribution/) available
    - The uninformative prior isn’t really “uninformative,” because any probability distribution will have *some* information. However, it will have little impact on the [posterior distribution](https://www.statisticshowto.com/posterior-distribution-probability/) because it makes minimal assumptions about the model

# What is the intuition behind Jeffreys Prior?

- The initial proposal for noninformative priors is to use uniform priors: $p(θ)∝1$
    - However, such a prior depends on the parameterization. This goes against our intuition because if we don't know anything about $θ$, then we don't know anything about $g(θ)$ as well
    - Jeffreys prior tries to overcome this issue. Under Jeffreys prior $p(θ)∝I(θ)$. If $ψ=g(θ)$, then $p(ψ)∝I(ψ)$
- Thus, Jeffreys prior is invariant under transformations. This is a desirable property for priors. However, this still doesn't clarify if Jeffreys prior is indeed a good representation of noninformativeness
    - At a later time, Bernado proposed reference priors that maximizes some statistical distance (e.g. Kullback-Liebler divergence) between prior and posterior
    - Thus reference priors carries the least amount of information about the parameter
    - It turns out that for one-parameter models, Bernado's reference priors reduces to Jeffreys prior. This seems like a good justification for using Jeffreys prior for one-parameter models. The multivariate version of Jeffreys prior that uses determinant of $I(θ)$ seems to have some issues, but the one-parameter priors give very sensible results

# How it works

- Jeffreys prior is defined in terms of [Fisher information,](https://www.statisticshowto.com/fisher-information/) which tells us how much information about an unknown [parameter](https://www.statisticshowto.com/what-is-a-parameter-statisticshowto/) we can get from a [sample](https://www.statisticshowto.com/sample/)
    - In other words, Fisher Information tells us how well we can measure a parameter, given a certain amount of data. The formula for Jeffreys prior is:

    $$
    \begin{align}

    p(\vec{\theta}) \propto\sqrt{\det I (\vec \theta)} \\

    \\

    I(\theta) = -E_\theta \left[\dfrac{\partial^2}{\partial \theta^2} \log  f(x|\theta)\right]
    \end{align}
    $$

    - Where:
        - $\vec \theta$ is a parameter vector
        - $\det I$ is the determinant of the fisher information matrix
        - $f(x|\theta)$ is the likelihood function
        - $\dfrac{\partial^2}{\partial \theta^2}$ is the second derivative with respect to the $\theta$
- It has the key feature that it is invariant under a change of coordinates for the parameter vector
    - This implies that it leads to the same posteriors regardless of how the model is represented
    - That is, the relative probability assigned to a volume of a probability space using a Jeffreys prior will be the same regardless of the parameterization used to define the Jeffreys prior. This makes it of special interest for use with *[scale parameters](https://handwiki.org/wiki/Scale_parameter)*

# Fisher Information

- Fisher Information is a way of measuring the amount of [information](https://en.wikipedia.org/wiki/Information) that an observable [random variable](https://en.wikipedia.org/wiki/Random_variable) *X* carries about an unknown parameter *θ* of a distribution that models *X*. Formally, it is the [variance](https://en.wikipedia.org/wiki/Variance) of the [score](https://en.wikipedia.org/wiki/Score_(statistics)), or the [expected value](https://en.wikipedia.org/wiki/Expected_value) of the [observed information](https://en.wikipedia.org/wiki/Observed_information)
- Fisher Information is calculated as the **Variance** of the **partial derivative w.r.t. $*θ*$** of the **Log-likelihood function** $*ℓ(θ | y)*$
    - [Reference](https://towardsdatascience.com/an-intuitive-look-at-fisher-information-2720c40867d8)

# Conjugate Families

- Although Jeffreys’s priors are rarely conjugate priors, they often give rise to analytically tractable posterior distributions
    - Moreover, the posterior distributions arising from Jeffrey’s priors are often members of the conjugate family for the likelihood function

# Resources

- [Video](https://www.youtube.com/watch?v=S42N_6pQ5TA)
- [https://handwiki.org/wiki/Jeffreys_prior](https://handwiki.org/wiki/Jeffreys_prior)
- [https://www.statisticshowto.com/jeffreys-prior/](https://www.statisticshowto.com/jeffreys-prior/)
- [https://math.stackexchange.com/questions/210607/in-what-sense-is-the-jeffreys-prior-invariant](https://math.stackexchange.com/questions/210607/in-what-sense-is-the-jeffreys-prior-invariant)
- [https://stats.stackexchange.com/questions/38962/why-is-the-jeffreys-prior-useful](https://stats.stackexchange.com/questions/38962/why-is-the-jeffreys-prior-useful)
- [https://people.eecs.berkeley.edu/~jordan/courses/260-spring10/lectures/lecture6.pdf](https://people.eecs.berkeley.edu/~jordan/courses/260-spring10/lectures/lecture6.pdf)
- [https://eventuallyalmosteverywhere.wordpress.com/2013/05/10/bayesian-inference-and-the-jeffreys-prior/](https://eventuallyalmosteverywhere.wordpress.com/2013/05/10/bayesian-inference-and-the-jeffreys-prior/)
- [https://www2.isye.gatech.edu/isyebayes/bank/handout5.pdf](https://www2.isye.gatech.edu/isyebayes/bank/handout5.pdf)

## Fisher Information

- [https://towardsdatascience.com/an-intuitive-look-at-fisher-information-2720c40867d8](https://towardsdatascience.com/an-intuitive-look-at-fisher-information-2720c40867d8)