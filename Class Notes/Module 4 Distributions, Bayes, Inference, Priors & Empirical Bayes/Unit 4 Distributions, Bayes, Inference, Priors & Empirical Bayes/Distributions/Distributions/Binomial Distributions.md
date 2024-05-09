# What is it?

- The binomial distribution gives the [discrete probability distribution](https://mathworld.wolfram.com/DiscreteDistribution.html) $P(n|N)$ of obtaining exactly $n$ successes out of $N$ [Bernoulli trials](https://mathworld.wolfram.com/BernoulliTrial.html) (where the result of each [Bernoulli trial](https://mathworld.wolfram.com/BernoulliTrial.html) is true with probability and false with probability )



    ![Untitled](./Binomial%20Distributions/Untitled.png)


# Criteria

Binomial distributions must also meet the following three criteria:

1. **The number of observations or trials is fixed**
    1. In other words, you can only figure out the [probability](https://www.statisticshowto.com/probability-and-statistics/probability-main-index/) of something happening if you do it a certain number of times
    2. This is common sense—if you toss a coin once, your probability of getting a tails is 50%. If you toss a coin a 20 times, your probability of getting a tails is very, very close to 100%
2. **Each observation or trial is** [independent](https://www.statisticshowto.com/probability-and-statistics/dependent-events-independent/#or)
    1. In other words, none of your trials have an effect on the probability of the next trial
3. The **probability of success** (tails, heads, fail or pass) is **exactly the same** from one trial to another

# Binomial Distribution Function

$$
P(X=n) = P_p(n|N) = {N \choose n}p^nq^{N-n}
$$

Which is equivalent to:

$$
P_p(n|N) = \dfrac{N!}{n!(N-n)!}* p^n(1-p)^{N-n}
$$

Where:

- $n$ represents the number of successes to achieve
- $N$ represents the number of Bernoulli trials

# Likelihood Function

$$
L(p|n,x) = \prod_{i=1}^n {n_i \choose k_i} p_i^{k_i} \cdot (1-p_i)^{n_i-k_i}
$$

# Numerical Characteristics

- **PMF:** $P(X=k|n,p) = \binom{n}{k} p^k(1-p)^{n-k} \space \text{for k} \in \{0, 1, 2, ..., n\}$
- **CDF:** $F(k|n,p) = \sum_{i=0}^{k} \binom{n}{i} p^i(1-p)^{n-i}$
- **Mean:** $np$
- **Variance:** $np(1-p)$
- **Support:** $\{0, 1, 2, ..., n\}$
- **Parameters:** $n$ (number of trials), $p$ (probability of success)
- **Notation:** $X \sim Bin(n, p)$

# Resources

- [https://mathworld.wolfram.com/BinomialDistribution.html](https://mathworld.wolfram.com/BinomialDistribution.html)
- [https://www.statisticshowto.com/probability-and-statistics/binomial-theorem/binomial-distribution-formula/](https://www.statisticshowto.com/probability-and-statistics/binomial-theorem/binomial-distribution-formula/)
- [https://sites.warnercnr.colostate.edu/gwhite/wp-content/uploads/sites/73/2017/04/BinomialLikelihood.pdf](https://sites.warnercnr.colostate.edu/gwhite/wp-content/uploads/sites/73/2017/04/BinomialLikelihood.pdf)
- [https://sherrytowers.com/2014/07/12/binomial-likelihood/](https://sherrytowers.com/2014/07/12/binomial-likelihood/)