# What are Bayesian Methods?

- Bayesian inference is simply updating your beliefs after considering new evidence
    - A Bayesian can rarely be certain about a result, but he or she can be very confident
    - This contrasts to Frequentists who assume that the probability is the long-run frequency of events
- Bayesian's interpret a probability as the measure of belief, or confidence, in an event occurring
- The basic philosophical difference between the frequentist and Bayesian paradigms is that Bayesian’s treat an unknown parameter $θ$ as random and use probability to quantify their uncertainty about it
    - In contrast, frequentists treat $θ$ as unknown but fixed, and they therefore believe that probability statements about $θ$ are useless
    - This fundamental disagreement leads to entirely different ways to handle statistical problems, even problems that might at first seem very basic

# Bayesian Vs. Classical Statistics
## **Main Differences**

- **Philosophical Foundation**
    - Classical Statistics: Classical statistics is based on the frequentist interpretation of probability. It treats probability as the long-term relative frequency of an event occurring in repeated trials
    - Bayesian Statistics: Bayesian statistics is rooted in the Bayesian interpretation of probability, which incorporates both prior knowledge and observed data to update beliefs about a parameter or hypothesis
- **Treatment of Uncertainty:**
    - Classical Statistics: In classical statistics, parameters are considered fixed, and uncertainty is addressed through confidence intervals and hypothesis testing
    - Bayesian Statistics: Bayesian statistics treats parameters as random variables and quantifies uncertainty using probability distributions, resulting in posterior distributions that express updated beliefs about the parameters after observing data
- **Prior Information:**
    - Classical Statistics: Classical statistics typically does not formally incorporate prior information or beliefs into the analysis
    - Bayesian Statistics: Bayesian statistics explicitly incorporates prior information by using a prior distribution to represent existing knowledge or beliefs about the parameter before observing new data
- **Inference Process:**
    - Classical Statistics: Classical inference involves hypothesis testing and the construction of confidence intervals based on the data at hand
    - Bayesian Statistics: Bayesian inference involves updating a prior distribution with new data to obtain a posterior distribution, which summarizes the updated beliefs about the parameter's true value
- **Interpretation of Results**
    - Classical Statistics: Results are often interpreted in terms of p-values, significance levels, and confidence intervals
    - Bayesian Statistics: Results are interpreted in terms of the posterior distribution, which provides a range of plausible values for the parameter along with their associated probabilities
- **Sample Size and Hypothesis Testing**
    - Classical Statistics: Classical methods often focus on fixed sample sizes and assess hypotheses in terms of the probability of observing results as extreme as those obtained, assuming the null hypothesis is true
    - Bayesian Statistics: Bayesian methods can adjust for varying sample sizes and directly compute the probability of hypotheses given the data
- **Computational Complexity:**
    - Classical Statistics: Classical methods are generally simpler computationally and may not require complex algorithms
    - Bayesian Statistics: Bayesian methods can be more computationally intensive, especially when dealing with complex models or high-dimensional data, as they involve iterative techniques like Markov Chain Monte Carlo (MCMC) sampling
- **Model Flexibility**
    - Classical Statistics: Classical methods often rely on assumptions such as normality and linearity, and violations of these assumptions can affect the validity of results
    - Bayesian Statistics: Bayesian methods offer greater flexibility to model complex relationships and incorporate prior information, which can be particularly useful when dealing with non-standard situations

![Untitled](./Bayesian%20Statistics/Untitled.png)

## 10 Coin Flips Example

- Notes:
    - $L(p)$ represents the likelihood

    ![Untitled](./Bayesian%20Statistics/Untitled%201.png)


# How it works

Designing a simple Bayesian model benefits from a design loop with three steps:

1. Data story: Motivate the model by narrating how the data might arise
2. Update: Educate your model by feeding it the data
3. Evaluate: All statistical models require supervision, leading to model revision

# Independence

- **Causal Independence:** refers to the absence of a direct causal relationship between two variables
    - In other words, two variables are causally independent if changes in one variable do not cause changes in the other
    - Causal independence is an important concept in understanding cause-and-effect relationships in various fields, such as epidemiology, economics, and social sciences. Establishing causal independence helps researchers identify whether changes in one variable can be attributed to changes in another variable, without a direct causal link
- **Logical Independence:** Logical independence, on the other hand, refers to the absence of a logical connection between two events or propositions
    - In statistics, logical independence is often used in the context of probability and probability distributions. Two events are said to be logically independent if the occurrence or non-occurrence of one event does not provide any information about the occurrence or non-occurrence of the other event
    - In terms of probability, if the probability of the joint occurrence of two logically independent events is equal to the product of their individual probabilities, then they are logically independent
- The suit of a card does not physically affect or cause any change in the probability of a queen. Neither does removing the two of diamonds, except for the fact that there are fewer cards to draw from
    - What we’re talking about here is logical independence, which is reflected in the state of our knowledge about the cards

# The Law of Total Probability

- The Law of Total Probability is a fundamental concept in probability theory that provides a way to express the probability of an event in terms of its partitions or subsets
    - It is a useful tool for decomposing a complex probability problem into simpler, more manageable parts. The Law of Total Probability states that for any event A and a partition of the sample space into mutually exclusive and exhaustive events B₁, B₂, ..., Bₙ, the probability of event A can be expressed as the sum of the probabilities of A given each partition element, weighted by the probabilities of those partition elements:

$$
    \begin{align}
        P(A)=P(A∩B_1)+P(A∩B_2)+…+P(A∩B_n)
    \end{align}
$$

- Which is equivalent to:

$$
    \begin{align}
        P(A) = \sum_{i=1}^{n} P(A \mid H_i) P(H_i)
    \end{align}
$$

- We use this often in homework problems for finding the marginal probability of some event - $P(A)$. You will want to partition your sample space into mutually exclusive, exhaustive hypotheses ($H_i$)
    - Try it out on some of the [supplementary exercises](https://www2.isye.gatech.edu/isye6420/supporting.html)

# Bayes Theorem

- [Bayes Theorem & Ingredients For Inference](./Bayesian%20Statistics/Bayes%20Theorem%20&%20Ingredients%20For%20Inference.md)
- In order to compute the posterior distribution, we multiply the prior and the likelihood. So, we need the Bayes Rule:

$$
\begin{align}
P(A|X) = \dfrac {P(X|A)P(A)} {P(X)}
\end{align}
$$

# Bayesian Inference

- Bayesian Inference involves setting up an *N*-dimensional space for prior distributions and an additional dimension that reflects the prior probability of a particular point
    - This allows us to make decisions based on observed data and our prior knowledge of the data

# Markov Chain Monte Carlo (MCMC)

- Markov Chain Monte Carlo (MCMC) methods are very powerful Monte Carlo methods that are often used in Bayesian inference
    - While "classical" Monte Carlo methods rely on computer-generated samples made up of independent observations, MCMC methods are used to generate sequences of dependent observations
    - These sequences are Markov chains, which explains the name of the methods
    - **Examples**
        - [Metropolis-Hastings Algorithm](./Metropolis-Hastings/Metropolis%20Hastings%20Algorithm.md)
        - [Gibbs Sampling](./Gibbs%20Sampling.md)

        - Laplace Approximation
- **Goal:** Recall that MCMC returns *samples* from the posterior distribution, not the distribution itself with the hopes that we can reconstruct the original distribution
    - By repeatedly sampling from the prior distribution and only accepting new samples which are more likely, we move in the general direction toward the regions where the posterior exists

    ## How Do MCMC Algorithms Work?

    1. Start at the current position
    2. Propose moving to a new position (investigate drawn sample from current state)
    3. Accept/Reject the new position based on adherence to the data and prior distributions
        1. If you accept:
            1. Move to the new position
            2. Return to step 1
        2. Else
            1. Do not move to the new position
            2. Return to step 1
    4. After a large number of iterations, return all accepted positions

    ### Algorithm Understanding

    - If the current position of the MCMC algorithm is in an area of extremely low probability, which is often the case when the algorithm begins (typically at a random location in the space), the algorithm will move in positions that are *likely not from the posterior* but *better than everything else nearby*
        - Thus the first moves of the algorithm are not very reflective of the posterior


# Terms & Key Concepts

- **Likelihood:** The relative number of ways that a value p can produce the data is usually called a likelihood
    - It is derived by enumerating all the possible data sequences that could have happened and then eliminating those sequences inconsistent with the data
- **Probability Distribution:** Let *Z* be some random variable. Then associated with *Z* is a *probability distribution function* that assigns probabilities to the different outcomes *Z* can take
- **Random Variables:** Z can be divided into three classifications: 1) Discrete, 2) Continuous and 3) Mixed
    - If Z is discrete, then its distribution is called a probability mass function which measures the probability that Z takes on the value k, denoted $P(Z=k)$
        - Note that the probability mass function completely describes the random variable Z
    - If Z is continuous, then Z has a probability density function
        - ***It’s important to know that the value of the probability density function at a point does not equal the probability of that point***
- **Marginalization (Summing Out):** Marginalization is a method that requires summing over the possible values of one variable to determine the marginal contribution of another

# Resources

- [https://www.statlect.com/fundamentals-of-statistics/Markov-Chain-Monte-Carlo](https://www.statlect.com/fundamentals-of-statistics/Markov-Chain-Monte-Carlo)

## Books

- Statistical Rethinking & [Github](https://github.com/pymc-devs/pymc-resources/tree/main/Rethinking_2)
- [Bayesian Data Analysis](https://learning.oreilly.com/library/view/bayesian-data-analysis/9781439898222/OEBPS/pI.htm)
- [ThinkBayes](https://allendowney.github.io/ThinkBayes2/)
- [Model-Based ML](https://www.mbmlbook.com/)