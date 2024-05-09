# Metropolis Hastings Algorithm

---

# What is it?

- The Metropolis Hastings algorithm is a beautifully simple algorithm for producing samples from distributions that may otherwise be difficult to sample from
    - Suppose we want to sample from a distribution $*π*$, which we will call the “target” distribution. For simplicity we assume that $*π$* is a one-dimensional distribution on the real line, although it is easy to extend to more than one dimension (see below)
    - The MH algorithm works by simulating a Markov Chain, whose stationary distribution is $*π*$. This means that, in the long run, the samples from the Markov chain look like the samples from $*π*$
    - As we will see, the algorithm is incredibly simple and flexible
        - Its main limitation is that, for difficult problems, “in the long run” may mean after a *very* long time. However, for simple problems the algorithm can work well
- The MH algorithm works by iteratively proposing and accepting or rejecting new states in a way that eventually generates samples from the desired target distribution
- The Metropolis algorithm uses a normal distribution to propose a jump. This normal distribution has a mean value $\mu$ which is equal to the current position and takes a "proposal width" for its standard deviation $\sigma$
- The basic idea behind MCMC is very simple. The idea is to define a [Markov chain](https://en.wikipedia.org/wiki/Markov_chain) over possible $x$ values, in such a way that the stationary distribution of the Markov chain is in fact $p(x)$
    - That is, what we’re going to do is use a Markov chain to generate a sequence of $x$ values, denoted $(x_1, …, x_n)$, in such a way that as $n \rightarrow \infty$, we can guarantee that $x_n \sim p(x)$. There are many different ways of setting up a Markov chain that has this property. The Metropolis-Hastings algorithm is one of these

# How does it work?

- **Objective**: The MH algorithm aims to generate a sequence of samples from a target probability distribution, often a posterior distribution in Bayesian statistics
- **Initialization**: Start with an initial state or parameter value, denoted as $θ₀$
- **Iteration**:
    1. **Proposal**: At each iteration, propose a new state, $θ*$, by making a small random perturbation from the current state $θ$. This perturbation is typically generated from a proposal distribution, $q(\theta * | \theta)$, which can be any distribution that allows movement in the parameter space
    2. **Acceptance or Rejection**: Calculate an acceptance ratio, $α$, which is the ratio of the posterior probability of the proposed state to the posterior probability of the current state:
        
        $$
        α = min \bigg (1, \dfrac{P(θ*)} {P(θ)} \bigg)
        $$
        
        - Where $P(θ)$ is the target distribution (often the posterior), and $P(θ*)$ is the proposed distribution. The "min(1, ...)" part ensures that the acceptance ratio is bounded by 1
    3. **Accept or Reject**: Sample a random value, u, from a uniform distribution between 0 and 1
        1. If $u ≤ α$, accept the proposed state ($θ*$); otherwise, reject it, and the chain remains at the current state ($θ$)
    4. **Repeat**: Continue this process for a predefined number of iterations or until convergence criteria are met
- **Convergence**: After running the MH algorithm for a sufficient number of iterations, the chain will converge to a stationary distribution, which is the desired target distribution
    - This means that the samples collected in the latter iterations closely approximate samples from the target distribution

# Metropolis Hastings Algorithm Overview

---

- This is also known as random-walk Metropolis
    - The proposal distribution is a perturbation of the current location of the chain. It must be symmetrical in this version of the algorithm, which can be considered a specific case of the more general Metropolis-Hastings algorithm. You can control the “step size” of the algorithm by reducing the variance of your proposal
- The most important step is the acceptance probability. If the acceptance ratio comes out greater than 1, great! We definitely want that new proposed value because it is more likely than the previous value
    - That’s why we take the minimum of 1 and $\dfrac{\pi(x_*)}{\pi(x_j)}$
    - If the ratio is less than 1, then we might accept it. We want to accept it based on that probability, so if it’s .8 then we will take it 80% of the time, if it’s .1 then we’ll accept it 10% of the time. This allows the sampler to get unlikely values as well, but keeps it within a representative area of the target distribution

## Proposal Step

- Here’s how it works. Suppose that the current state of the Markov chain is $x_{n}$, and we want to generate $x_{n+1}$. In the Metropolis-Hastings algorithm, the generation of $x_{n+1}$ is a two-stage process:
    1. The first stage is to generate a *candidate*, which we’ll denote $x_{*}$
        1. The value of $x_{*}$ is generated from the proposal distribution that we already know how to sample from. We denote this proposal distribution $q(x_{*}|x_n)$
            1. Notice that the distribution we sample from depends on the current state of the Markov chain, $x_{n}$
            2. There are some technical constraints on what you can use as a proposal distribution, but for the most part it can be anything you like
            3. A very typical way to do this is to use a normal distribution centered on the current state $x_{n}$. More formally, we write this as:
                
                $$
                x_*|x_n \sim Normal(x_n, \sigma^2)
                $$
                
                - for some standard deviation $\sigma$ that we select in advance
- Why use a proposal distribution?
    - Helps us bounce around within the limits of the posterior (target) distribution
    - In each iteration, the algorithm proposes a new sample based on the current state and the proposal distribution. This proposed sample is then accepted or rejected based on a probability ratio, which depends on the target distribution. The proposal distribution affects the algorithm's efficiency and convergence rate

## Acceptance Step

- The second stage is the accept-reject step. Firstly, what you need to do is calculate the *acceptance probability*, denoted $A(x_n \rightarrow x_*)$, which is given by:
    
    $$
    A(x_n \rightarrow x_*) = \min \Bigg(1, \dfrac{p(x_*)}{p(x_n)}\cdot \dfrac{q(x_n|x_*)}{q(x_*|x_n)}\Bigg)
    $$
    
- There are two things to pay attention to here. Firstly, notice that the ratio $\dfrac{p(x_*)}{p(x_n)}$ doesn’t depend on the normalizing constant for the distribution
- The second thing to pay attention to is the behaviour of the other term, $\dfrac{q(x_n|x_*)}{q(x_*|x_n)}$. What this term does is correct for any biases that the proposal distribution might induce
    - In this expression, the **denominator $q(x_*|x_n)$ describes the probability with which you’d choose $x_*$ as the candidate if the current state of the Markov chain is** $x_n$
    - The numerator, however, describes the probability of a transition that goes the other way: that is, if the current state had actually been $x_*$, what is the probability that you would have generated $x_n$ as the candidate value?
        - ***If the proposal distribution is symmetric, then these two probabilities will turn out to be equal***
    - For example, if the proposal distribution is normal, then:
    
    $$
    q(x_*|x_n) = \dfrac{1}{\sqrt{2\pi \sigma}} \exp \Big \lbrace{-\dfrac{1}{2\sigma^2}(x_n-x_*)^2 \Big \rbrace}
    \\~\\
    
    q(x_n|x_*) = \dfrac{1}{\sqrt{2\pi \sigma}} \exp \Big \lbrace{-\dfrac{1}{2\sigma^2}(x_*-x_n)^2 \Big \rbrace}
    $$
    
    - ***Clearly, $q(x_*|x_n) = q(x_n|x_*)$ for all choices of $x_n$ and $x_*$, and as a consequence the ratio $\dfrac{q(x_n|x_*)}{q(x_*|x_n)}$ is always 1 in this case***
        - This special case of the Metropolis-Hastings algorithm, in which the proposal distribution is symmetric, is referred to as the *Metropolis algorithm*
- Having proposed the candidate $x_*$ and calculated the acceptance probability $A(x_n \rightarrow x_*)$, , we now either decide to “accept” the candidate and set $x_{n+1} = x_*$ or we “reject” the candidate and set $x_{n+1} = x_n$
    - To make this decision, we generate a uniformly distributed random number between 0 and 1, denoted $u$. Then:
    
    $$
    x_{n+1} = \begin{cases}
       x_* &\text{if } u \le A(x_n \rightarrow x_*)\\
       x_n &\text{otherwise}
    \end{cases}
    $$
    

## Random Walk Metropolis

![Untitled](Metropolis%20Hastings%20Algorithm%201af2eb22115e43aea6ff585c9f0f3a5f/Untitled.png)

- **Inputs** Let $\pi(x)$ be proportional to the target PDF. $x_j$ is the current value and $q(x|x_j)$ is a symmetric proposal distribution - $q(x|x_j) = q(x_j|x)$
- **Output** An array of samples representing the target PDF
- **Steps:**
    1. The first step is to initialize the sample value for each random variable (this value is often sampled from the variable’s prior distribution)
        1. Choose an initial value $x_0$ from your sample space
    2. Sample $x_* ∼ q(x|x_j)$
    3. Calculate the acceptance probability: 
    
    $$
    \rho(x_j, x_*) = min\left\{1, \dfrac{\pi(x_*)}{\pi(x_j)}\right\}
    $$
    
    4. Update $x_{j+1} = x_*$ *with probability $\rho(x_j, x_*)$*, otherwise $x_{j+1}$ remains equal to $x_j$
    
- **Definitions:**
    - $\pi(x)$ is the target distribution
    - $q(x_*|x)$ is the proposal distribution which is a distribution that we can easily sample from
        - The proposal distribution should share the same support as the target distribution, i.e. the two distributions should have the same range of x-values

## Independent Metropolis

- **Inputs** Let $\pi(x)$ be proportional to the target PDF. $x_j$ is the current value and $q(x|x_j)$ is a symmetric proposal distribution - $q(x|x_j) = q(x_j|x)$
- **Output** An array of samples representing the target PDF
- **Steps:**
    1. Choose an initial value $x_0$ from your sample space
    2. Sample $x_* ∼ q(x|x_j)$
    3. Calculate the acceptance probability: 
    
    $$
    \rho(x_j, x_*) = min\left\{1, \frac{\pi(x_*)}{\pi(x_j)}\frac{q(x_j|x_*)}{q(x_*|x_j)}\right\}
    $$
    
    4. Update $x_{j+1} = x_*$ *with probability $\rho(x_j, x_*)$*, otherwise $x_{j+1}$ remains equal to $x_j$
    

# Implementation Considerations

- If we are going to implement the above steps, there is another consideration we need to mention. With many data samples, the likelihood term $*p(X|θ)*$ is the product of all the $*p(X_i|θ)*$ likelihoods (of each sample). Multiplying many probabilities for simulation will lead to very small numbers. Instead, for numerical stability during computational simulation, we need to use the log transform instead. This means we are calculating the log of unnormalized posterior:
    
    $$
    \log p(\theta|x) = \log p(x|\theta)\cdot p(\theta)
    $$
    
- **Proposal Distributions:** There are mainly two kinds of proposal distributions, symmetric and asymmetric. A proposal distribution is a symmetric distribution if $q(x^i|x^{i−1}) = q(x^{i−1}|x^{i})$
    - Straightforward choices of symmetric proposals include Gaussian distributions or Uniform distributions centered at the current state of the chain
        - For example, if we have a Gaussian proposal, then we have $x^{cand} = x^{i−1}+ Normal(0, σ)$
            - Because the pdf for $Normal(x^{cand} − x^{i−1}; 0, σ) = Normal(x^{i−1} − x^{cand}; 0, σ)$, this is a symmetric proposal

# Issues with Metropolis Hastings

- Dependence on starting values
    - We can reduce the influence on the starting value by using a ***burn-in period***
        - This is the time it takes for the chain to stabilize so its not drifting up or down over time
    - Look at plots for the first and last halves of the sampling procedure to identify differences
- Autocorrelation due to Markov Chain
    - The values of the parameter we are sampling are correlated due to the Markov Process
    - ***Thinning*** can help
        - The process of increasing the MCMC sample size and drawing at regular intervals
            - I.e. Keep every third value
- In practice when you’re implementing a Metropolis algorithm, the choice of proposal distribution matters a lot
    - If it’s too narrow, your sampler will have an extremely high acceptance rate on average, but it will move around extremely slowly
        - To use the technical term, it has a very low *mixing* rate. This distorts your estimate of the target distribution.
    - However, if it’s too wide, the acceptance rate becomes too low and the chain gets stuck on specific values for long periods of time
        - This also distorts your estimate of the target distribution
    - Yes, technically, if you run your accursed sampler long enough despite it’s poor choice of proposal distribution it will eventually produce the right answer… but wouldn’t you prefer a sampler that gives you the right answer quickly rather than slowly?

# **Key Concepts**

- The choice of the ***proposal*** distribution $q(θ_* | θ)$ affects the efficiency and convergence of the MH algorithm. It should be designed to allow adequate exploration of the parameter space
- The acceptance ratio $α$ ensures that the Markov chain eventually samples from the correct distribution by accepting or rejecting proposed states based on their relative probabilities
- MH is versatile and can be applied to a wide range of problems, including Bayesian inference, statistical physics, and optimization
- Like other MCMC methods, the initial iterations of the chain may not be representative of the target distribution, so a burn-in period is often used to allow the chain to reach convergence

# Resources

[Video Overview](https://www.youtube.com/watch?v=OTO1DygELpY&t=362s)

[https://www.youtube.com/watch?v=yCv2N7wGDCw&list=PLvcbYUQ5t0UEkf2NUEo7XSsyVTyeEk3Gq&index=4](https://www.youtube.com/watch?v=yCv2N7wGDCw&list=PLvcbYUQ5t0UEkf2NUEo7XSsyVTyeEk3Gq&index=4)

[MetropolisHastingsSampling.pdf](Metropolis%20Hastings%20Algorithm%201af2eb22115e43aea6ff585c9f0f3a5f/MetropolisHastingsSampling.pdf)

- [https://areding.github.io/6420-pymc/unit5/Unit5-Metropolis.html](https://areding.github.io/6420-pymc/unit5/Unit5-Metropolis.html)
- [https://blog.djnavarro.net/posts/2023-04-12_metropolis-hastings/](https://blog.djnavarro.net/posts/2023-04-12_metropolis-hastings/)
- [https://stephens999.github.io/fiveMinuteStats/MH_intro.html](https://stephens999.github.io/fiveMinuteStats/MH_intro.html)
- [https://bayesball.github.io/BOOK/simulation-by-markov-chain-monte-carlo.html#the-metropolis-algorithm](https://bayesball.github.io/BOOK/simulation-by-markov-chain-monte-carlo.html#the-metropolis-algorithm)
- [https://boyangzhao.github.io/posts/mcmc-bayesian-inference](https://boyangzhao.github.io/posts/mcmc-bayesian-inference)
- [https://twiecki.io/blog/2015/11/10/mcmc-sampling/](https://twiecki.io/blog/2015/11/10/mcmc-sampling/)
- [https://people.duke.edu/~ccc14/sta-663/MCMC.html](https://people.duke.edu/~ccc14/sta-663/MCMC.html)
- [https://similarweb.engineering/mcmc/](https://similarweb.engineering/mcmc/)
- [https://gregorygundersen.com/blog/2019/11/02/metropolis-hastings/](https://gregorygundersen.com/blog/2019/11/02/metropolis-hastings/)
- [https://www.jarad.me/courses/stat544/slides/Ch11/Ch11a.pdf](https://www.jarad.me/courses/stat544/slides/Ch11/Ch11a.pdf)
- [https://bookdown.org/kevin_davisross/bayesian-reasoning-and-methods/mcmc.html](https://bookdown.org/kevin_davisross/bayesian-reasoning-and-methods/mcmc.html)
- [https://www.baeldung.com/cs/markov-chain-monte-carlo](https://www.baeldung.com/cs/markov-chain-monte-carlo)
- [https://twiecki.io/blog/2015/11/10/mcmc-sampling/](https://twiecki.io/blog/2015/11/10/mcmc-sampling/)
- [https://similarweb.engineering/mcmc/](https://similarweb.engineering/mcmc/)
- [https://people.duke.edu/~ccc14/sta-663-2016/16A_MCMC.html](https://people.duke.edu/~ccc14/sta-663-2016/16A_MCMC.html)

### Acceptance Ratio

- [https://stats.stackexchange.com/questions/271953/acceptance-rate-for-metropolis-hastings-0-5](https://stats.stackexchange.com/questions/271953/acceptance-rate-for-metropolis-hastings-0-5)
- [https://stats.stackexchange.com/questions/88308/can-we-change-the-acceptance-rate-in-random-walk-metropolis-algorithm-by-changin](https://stats.stackexchange.com/questions/88308/can-we-change-the-acceptance-rate-in-random-walk-metropolis-algorithm-by-changin)