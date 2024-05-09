# Overview

- Markov Chain Monte Carlo (MCMC) methods are a class of statistical techniques used for approximating complex probability distributions and making Bayesian inference
- They work by generating a Markov chain of samples from the target distribution, allowing practitioners to compute various statistical quantities of interest
- Combining these two methods, Markov Chain and Monte Carlo, allows random sampling of high-dimensional probability distributions that honors the probabilistic dependence between samples by constructing a Markov Chain that comprise the Monte Carlo sample
- Monte Carlo methods provide a numerical approach for solving complicated functions. Instead of solving them analytically, we sample from distributions in approximating the solutions

# What is MCMC?

- MCMC is a family of algorithms that provides a way to draw samples from a probability distribution when direct sampling is difficult or impossible
    - It is widely used in Bayesian statistics, machine learning, and various scientific fields for tasks such as parameter estimation, uncertainty quantification, and model selection

# How do they work?

MCMC works through a random walk in a high-dimensional space. The key idea is to construct a Markov chain whose stationary distribution (long-term behaviour) matches the target probability distribution you want to sample from. Here's how it works step by step:

1. **Initialization**: Start with an initial guess or state in the parameter space
2. **Proposal Step**: Propose a new state or parameter value by making a small random perturbation to the current state. This step introduces randomness and ensures exploration of the parameter space
3. **Acceptance or Rejection**: Evaluate whether the proposed state is better or worse than the current state using the target distribution. If it's better (i.e., it increases the likelihood of the data given the parameters), accept the proposed state with a certain probability
    1. If it's worse, accept it with a lower probability. This probabilistic acceptance step ensures that the Markov chain samples from the correct distribution over time
4. **Repeat**: Repeat steps 2 and 3 for many iterations. The chain gradually explores the parameter space, and after a sufficient number of iterations, it reaches a state where the distribution of sampled values closely matches the target distribution
5. **Convergence**: Check for convergence to ensure that the Markov chain has reached a stationary distribution. Common convergence diagnostics include monitoring trace plots, autocorrelation, and other statistical tests
6. **Collect Samples**: Once the chain has converged, collect the sampled values as representative samples from the target distribution. These samples can be used to estimate posterior probabilities, compute expectations, and make inferences about the parameters of interest

# Algorithms to Perform MCMC

There is a large family of algorithms that perform MCMC. Most of these algorithms can be expressed at a high level as follows:

1. Start at current position
2. Propose moving to a new position (investigate a pebble near you)
3. Accept/Reject the new position based on the position's adherence to the data and prior distributions (ask if the pebble likely came from the mountain)
    1. If you accept: Move to the new position. Return to Step 1
    2. Else: Do not move to new position. Return to Step 1
4. After a large number of iterations, return all accepted positions

- This way we move in the general direction towards the regions where the posterior distributions exist, and collect samples sparingly on the journey
    - Once we reach the posterior distribution, we can easily collect samples as they likely all belong to the posterior distribution
- If the current position of the MCMC algorithm is in an area of extremely low probability, which is often the case when the algorithm begins (typically at a random location in the space), the algorithm will move in positions *that are likely not from the posterior* but better than everything else nearby
    - Thus the first moves of the algorithm are not reflective of the posterior

# Approaches

- The main difference between MCMC algorithms occurs in ***how you jump*** as well as ***how you decide whether to jump***

## **Metropolis-Hastings Algorithm**

- One of the most foundational MCMC methods that uses an acceptance-rejection mechanism to propose and accept new states
- [Metropolis Hastings Algorithm](./Markov%20Chain%20Monte%20Carlo%20Methods/Metropolis%20Hastings%20Algorithm.md)

## **Gibbs Sampling**

- A specific MCMC algorithm for sampling from multivariate distributions by iteratively updating one variable at a time, conditional on the others
- [Gibbs Sampling](./Markov%20Chain%20Monte%20Carlo%20Methods/Gibbs%20Sampling.md)

# Markov Chains

- **Markov chains can be thought of as walking on the chain, given the state at a particular step, we can decide on the next state by seeing the ‘probability distribution of states’ over the next step**
- A sequence ${X_0, X_1, X_2, \dots, X_{n-1}, X_n, X_{n+1}, \dots}$ forms a Markov Chain if:
    1. The conditional probability $P\left(X_{n+1} \in A | X_0, X_1, \dots, X_n\right) = P\left(X_{n+1} \in A | X_n\right)$. This property states that given the present, the future is independent of the past
    2. Given $X_n$, the future (events defined on $X_{n+1}, X_{n+2}, \dots$) is independent of the past (events defined on $\dots, X_{n-2}, X_{n-1}$)
    3. The conditional probability $P\left(X_{n+1} \in A | X_n\right)$ is equivalent to a transition kernel $Q_{A | X_n}$
    4. The transition kernel $Q_{A | X_n} = x$ can be computed as $\int_A q(x, y) dy$ which represents the probability of transitioning into set $A$ from state $x$
    5. $\Pi$ is an invariant distribution if $\Pi(A) = \int Q_{A | x} \Pi dx$. This means that integrating the transition kernel distribution with respect to the distribution $\Pi$ yields the same distribution $\Pi$, making it invariant

## Stationary Distribution

- As we progress through time, the **probability of being in certain states are more likely than others**. Over the long run, the distribution will reach an **equilibrium** with an associated probability of being in each state. This is known as the **Stationary Distribution**

# Other Notes

- $\pi$ is the density for $\Pi$. It is stationary if it satisfies the detailed balance equation: $q(x|y) \pi(y) = q(y|x) \pi(x)$
    - The detailed balance condition states that for any two states $x$ and $y$, the probability of transitioning from $x$ to $y$ times the stationary distribution at $x$ equals the probability of transitioning from $y$ to $x$ times the stationary distribution at $y$
- If $Q^n_{A|x} = P(X_n \in A | X_0 = x)$, then as $n \rightarrow \infty$, $Q^n_{A|x} \rightarrow \Pi_A$
    - In other words, the $n$-step transition probabilities converge to the stationary distribution as $n$ goes to infinity
- $\Pi$ is called the equilibrium distribution of the Markov chain. The idea is to construct the Markov Chain such that this equilibrium distribution corresponds to the desired posterior distribution
- The initial condition $X_0 = x$ is "forgotten" as $n$ becomes large, meaning that the influence of the initial state diminishes over time
    - When $n$ is large enough, each $X_n$ can be considered as a random variable sampled from the posterior distribution

# **Key Concepts:**

- **Markov Chain:** [Markov chain](https://en.wikipedia.org/wiki/Markov_chain) is a systematic method for generating a sequence of random variables where the current value is probabilistically dependent on the value of the prior variable. Specifically, selecting the next variable is only dependent upon the last variable in the chain
- **Monte Carlo:** [Monte Carlo](https://en.wikipedia.org/wiki/Monte_Carlo_method) is a technique for randomly sampling a probability distribution and approximating a desired quantity
- **Burn-In**: The initial iterations of an MCMC chain may not be representative of the target distribution. The burn-in period is the time it takes for the chain to reach a stationary distribution
- **Thinning**: Reducing the number of collected samples to reduce autocorrelation and improve the efficiency of estimation
- **Convergence Assessment**: Various diagnostic tools, such as the Gelman-Rubin statistic and visual inspection, help assess whether the Markov chain has converged
- **Stationary Distribution ($\prod$):** A stationary distribution of a Markov chain is **a probability distribution that remains unchanged in the Markov chain as time progresses**

# Resources

- [https://www.youtube.com/watch?v=yApmR-c_hKU&list=PLvcbYUQ5t0UEkf2NUEo7XSsyVTyeEk3Gq&index=5](https://www.youtube.com/watch?v=yApmR-c_hKU&list=PLvcbYUQ5t0UEkf2NUEo7XSsyVTyeEk3Gq&index=5)
- [Computational Stats - MCMC](https://people.duke.edu/~ccc14/sta-663/MCMC.html)
- [https://bookdown.org/kevin_davisross/bayesian-reasoning-and-methods/mcmc.html](https://bookdown.org/kevin_davisross/bayesian-reasoning-and-methods/mcmc.html)
- [https://www.baeldung.com/cs/markov-chain-monte-carlo](https://www.baeldung.com/cs/markov-chain-monte-carlo)
- [https://betanalpha.github.io/assets/case_studies/markov_chain_monte_carlo.html](https://betanalpha.github.io/assets/case_studies/markov_chain_monte_carlo.html)
- [https://similarweb.engineering/mcmc/](https://similarweb.engineering/mcmc/)
- [https://www.cs.cmu.edu/~epxing/Class/10708-14/scribe_notes/scribe_note_lecture27.pdf](https://www.cs.cmu.edu/~epxing/Class/10708-14/scribe_notes/scribe_note_lecture27.pdf)
- [https://jellis18.github.io/post/2018-01-02-mcmc-part1/](https://jellis18.github.io/post/2018-01-02-mcmc-part1/)

### Markov Chains

- [https://towardsdatascience.com/monte-carlo-markov-chain-mcmc-explained-94e3a6c8de11](https://towardsdatascience.com/monte-carlo-markov-chain-mcmc-explained-94e3a6c8de11)
- [https://setosa.io/ev/markov-chains/](https://setosa.io/ev/markov-chains/)