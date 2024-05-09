# What is Gibbs Sampling?

- Like other MCMC methods, the Gibbs sampler constructs a Markov Chain whose values converge towards a target distribution. Gibbs Sampling is in fact a specific case of the [Metropolis-Hastings](https://towardsdatascience.com/monte-carlo-markov-chain-89cb7e844c75) algorithm wherein proposals are always accepted
- Say that there is an $m$-component joint distribution of interest that is difficult to sample from. Even though I do not know how to sample from the joint distribution, assume that I do know how to sample from the full conditional distributions. That is, I can easily sample from each of the $m$ components conditional on the other $m-1$
    - **Under these conditions, Gibbs sampling iteratively updates each of the components based on the full conditionals to obtain samples from the joint distribution**
- Also called Markov Chain Monte Carlo (MCMC)
    - These are called ***dependent sampling algorithms***

# When to use Gibbs Sampling?

- Gibbs Sampling is applicable when the joint distribution is not known explicitly or is difficult to sample from directly, but the conditional distribution of each variable is known and is easier to sample from
- **The main point of Gibbs sampling is that given a multivariate distribution, it’s simpler to sample from a conditional distribution than from a joint distribution**
    - For instance, instead of sampling directly from a joint distribution $P(x,y)$, Gibbs sampling propose sampling from two conditional distribution $P(x|y)$ and $P(y|x)$

# How does it work?

- The basic idea in Gibbs sampling is that, rather than probabilistically picking the next state all at once, you make a separate probabilistic choice for each of the k dimensions, where each choice depends on the other $k − 1$ dimensions
- The Gibbs sampling algorithm for Bayesian networks starts with an arbitrary state (with the evidence variables fixed at their observed values) and generates a next state by ***randomly sampling a value for one of the non-evidence variables $X_i$***
    - Xi is independent of all other variables given it’s **Markov Blanket** (its parents, its children and children’s other parents)
        - **Therefore, Gibbs Sampling for $X_i$, means sampling conditioned on the current values of the variables in the Markov Blanket**
- We start off by selecting an initial value for the random variables $X \& Y$
    - Then, we sample from the conditional probability distribution of $X$ given $Y = Y⁰$ denoted $p(X|Y⁰)$
    - Next, we sample a new value of $Y$ conditional on $X¹$, which we just computed. We repeat the procedure for an additional $n - 1$ iterations, alternating between drawing a new sample from the conditional probability distribution of $X$ and the conditional probability distribution of Y, given the current value of the other random variable

# Algorithm Overview

- Let's say that we have a multivariate probability distribution: $p(X,Y)$
    - This probability distribution tends to generalize one-dimensional normal distributions to higher dimensions
    - The distribution given above has two conditional probabilities, given as follows:
        1. $p(X∣Y)$
        2. $p(Y∣X)$
- The steps of the algorithm are as follows:
    1. Choose a random value for both variables, $X$ and $Y$
    2. Sample from the distribution of $X$
    3. Sample a new value for $Y$ on the $X$ we just computed
    4. Repeat 1 and 2 for n iterations
- We can also do alternative sampling between $X$ and Y

# Pseudocode

```python
function GIBBS-ASK(X, e, bn, N) returns an estimate of P(X | e)
 local variables: N, a vector of counts for each value of X, initially zero
        Z, the nonevidence variables in bn
        x, the current state of the network, initially copied from e

 initialize x with random values for the variables in Z
 for j = 1 to N do
   choose any variable Zi from Z acoording to any distribution ρ(i)
     set the value of Zi in x by sampling from P(Zi | mb(Zi))
     N[x] ← N[x] + 1 where x is the value of X in x
 return NORMALIZE(N)
```

# Pros & Cons

### Pros

1. It is easy to evaluate the conditional distributions
2. There is an exact sampling from conjugate conditionals
3. There are lower dimensional conditions and it's easy to apply both rejection and importance samplings

### Cons

1. There is always a need to derive conditional probability distributions
2. There is also a need to derive random samples from these distributions
3. Gibbs sampling may get slow because of no diagonal steps and correlated parameters

# References

- Gibbs Sampling Walkthrough: [https://www.youtube.com/watch?v=ER3DDBFzH2g](https://www.youtube.com/watch?v=ER3DDBFzH2g)
- [https://www.youtube.com/watch?v=7LB1VHp4tLE&list=PLvcbYUQ5t0UEkf2NUEo7XSsyVTyeEk3Gq&index=7&pp=iAQB](https://www.youtube.com/watch?v=7LB1VHp4tLE&list=PLvcbYUQ5t0UEkf2NUEo7XSsyVTyeEk3Gq&index=7&pp=iAQB)
- [https://jwmi.github.io/BMS/chapter6-gibbs-sampling.pdf](https://jwmi.github.io/BMS/chapter6-gibbs-sampling.pdf)
- [https://stephens999.github.io/fiveMinuteStats/gibbs1.html](https://stephens999.github.io/fiveMinuteStats/gibbs1.html)
- [https://towardsdatascience.com/gibbs-sampling-8e4844560ae5](https://towardsdatascience.com/gibbs-sampling-8e4844560ae5)
- [https://cs.adelaide.edu.au/~dsuter/Harbin_course/BayesNetsSampling.pdf](https://cs.adelaide.edu.au/~dsuter/Harbin_course/BayesNetsSampling.pdf)
- [https://people.duke.edu/~ccc14/sta-663/MCMC.html#gibbs-sampler](https://people.duke.edu/~ccc14/sta-663/MCMC.html#gibbs-sampler)
- [https://bookdown.org/rdpeng/advstatcomp/gibbs-sampler.html](https://bookdown.org/rdpeng/advstatcomp/gibbs-sampler.html)
-

### Python Implementation

- [https://jaketae.github.io/study/gibbs-sampling/](https://jaketae.github.io/study/gibbs-sampling/)
- [https://github.com/hendrycks/ML-Coursework/blob/master/AM207-Monte Carlo Methods%2C MCMC%2C Gibbs/Gibbs Sampling.ipynb](https://github.com/hendrycks/ML-Coursework/blob/master/AM207-Monte%20Carlo%20Methods%2C%20MCMC%2C%20Gibbs/Gibbs%20Sampling.ipynb)
- [https://people.duke.edu/~ccc14/sta-663-2016/16A_MCMC.html](https://people.duke.edu/~ccc14/sta-663-2016/16A_MCMC.html)