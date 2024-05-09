# What is it?

- Unlike the classical approach, Bayesian testing doesn’t prioritize the null hypothesis. Instead, we calculate the posterior probabilities for both hypotheses, ***then choose the one with the larger posterior probability***
- Bayesian/Frequentist approaches we used earlier in the book Recall that the **likelihood** function underpinned a lot of the frequentist approach: that is, $f(X|θ)$, or the likelihood of the data we observed given specific parameters
    - The Bayesian approach flipped this on it’s head: we found $f(θ|X)$, or the distribution of the parameter given the data, by employing Bayes rule
- Unlike frequentist statistics Bayesian statistics does allow to talk about the probability that the null hypothesis is true
    - Better yet, it allows us to calculate the ***posterior probability of the null hypothesis***, using Bayes’ rule:

    $$
    P(h_0|data) = \dfrac{P(d|h_0)P(h_0)}{P(d)}
    $$

    - This formula tells us exactly how much belief we should have in the null hypothesis after having observed the data d. Similarly, we can work out how much belief to place in the alternative hypothesis using essentially the same equation. All we do is change the subscript

        $$
        P(h_1|data) = \dfrac{P(d|h_1)P(h_1)}{P(d)}
        $$

        ![Untitled](./Bayesian%20Hypothesis%20Testing/Untitled.png)


# Components

### **Bayes Factor**:

- The Bayes factor is the Bayesian counterpart of the [likelihood ratio](http://en.wikipedia.org/wiki/Likelihood-ratio_test), which is ubiquitous in frequentist hypothesis testing
- In practice, most Bayesian data analysts tend not to talk in terms of the raw posterior probabilities $P(h_0|d)$ and $P(h_1|d)$
    - Instead, we tend to talk in terms of the ***posterior odds*** ratio. Think of it like betting. Suppose, for instance, the posterior probability of the null hypothesis is 25%, and the posterior probability of the alternative is 75%
    - The alternative hypothesis is three times as probable as the null, so we say that the *odds* are 3:1 in favour of the alternative
    - The Bayes factor is the Bayesian counterpart of the [likelihood ratio](http://en.wikipedia.org/wiki/Likelihood-ratio_test), which is ubiquitous in frequentist hypothesis testing. The idea behind Bayesian hypothesis testing is that we should choose whichever hypothesis better explains the observation, so we reject $*𝐻_0*$ when $Odds(𝐻_𝐴)>1$, and accept $*𝐻_0*$ otherwise
- Intuitively, what is Bayes’ Factor giving?
    - ***It’s just the ratio of how likely the data we observed is for each model***
        - What if $M_A$ was much better than $M_B$? Then we would expect for the probability of the observed data to be higher, which means the numerator would be a lot larger than the denominator, which means Bayes Factor would be large
    - In general, then, a large Bayes factor is evidence supporting the model in the numerator, and a small Bayes factor is evidence supporting the model in the denominator
    - Generally, if one of the probabilities is more than 10 times as large as the other, it’s very strong evidence for that model. Between 3 times and 10 times as large a probability is generally considered ‘substantial’ evidence
- The Bayesian framework for hypothesis testing relies on the calculation of the posterior odds of the hypotheses

    $$
    \begin{align}
        Odds(H_A|x) = \dfrac{P(H_A|x)}{H_0|x)} = BF(x) \cdot \dfrac{\pi_A}{\pi_B}
    \end{align}
    $$

    - where $*𝐵𝐹(𝑥)*$ is the Bayes factor. In our situation, the Bayes factor is

$$
BF(x) = \dfrac{\int_{\Theta_A}f(x|\mu)P_A(\mu) du}{f(x|0)}
$$

### Precise Null & Point Masses

- Precise Null $H_0:\theta = \theta_0$ requires prior with point mass at $\theta_0$
- The professor notes that your overall prior needs to contain the point mass representing your precise null hypothesis
    - What the professor means here is that you can only test a hypothesis where your prior allows for a probability greater than 0
        - So if your prior is just a continuous distribution, the probability at any given point is 0. At a high level, if your prior doesn’t contain your hypothesis, you are essentially ruling out the hypothesis before you even build the rest of your model. Without mixing in the point mass, you’ve already predetermined that your hypothesis is impossible
    - That’s why he mixes that point mass and the “spread” distribution; you need a discrete distribution to test a specific point
    - [Reference](https://areding.github.io/6420-pymc/unit4/Unit4-testing.html)
- Bayes Factor in the precise null scenario

$$
B_{01} = \dfrac{f(x|\theta_0)}{m_1(x)}

\\
B_{10} = \dfrac{m_1(x)}{f(x|\theta_0)}
$$

# How does it work?

- Assume that $\Theta_0$ and $\Theta_1$ are two non-overlapping sets of parameter $\theta$ (not necessarily a partition, just non-overlapping). We want to test:

$$
H_0: \theta \in \Theta_0 \text{ vs } H_1: \theta \in \Theta_1
$$

- Conceptually simple:

$$
p_0 = \int_{\Theta_0} \pi(\theta|x)d\theta = \mathbb{P}^{\theta|X}(H_0) \\ p_1 = \int_{\Theta_1} \pi(\theta|x)d\theta = \mathbb{P}^{\theta|X}(H_1) \\
$$

- ***We then choose the hypothesis with the larger posterior probability***
- We have prior probabilities of:

$$
\pi_0=\int_{\Theta_0} \pi(\theta)d\theta \\ \pi_1=\int_{\Theta_1} \pi(\theta)d\theta \\
$$

- $B_{01}$ - Bayes factor in favour of $H_0$
- $B_{01} = \frac{p_0/p_1}{\pi_0/\pi_1} \rightarrow (\text{posterior odds / prior odds)}$
- $B_{10} = \frac{1}{B_{01}}$

## Bayes Factor Calibration

- $B_{10}$ - BF in favor of $H_1$

| Value | Evidence Against $H_0$ |
| --- | --- |
| 0 $\le log_{10} B_{10}$ $\le$ 0.5 | Poor |
| 0 $< log_{10} B_{10}$ $\le$ 1 | Substantial |
| 1 $< log_{10} B_{10}$ $\le$ 1.5 | Strong |
| 1.5 $< log_{10} B_{10}$ $\le$ 2 | Very Strong |
| $log_{10} B_{10}$ > 2 | Decisive |

# Key Terms & Concepts

- **Maximum a Posteriori Hypothesis Test:** Choose the hypothesis with the highest posterior probability

# Resources

- [https://stats.libretexts.org/Bookshelves/Applied_Statistics/Learning_Statistics_with_R_-_A_tutorial_for_Psychology_Students_and_other_Beginners_(Navarro)/17%3A_Bayesian_Statistics/17.02%3A_Bayesian_Hypothesis_Tests](https://stats.libretexts.org/Bookshelves/Applied_Statistics/Learning_Statistics_with_R_-_A_tutorial_for_Psychology_Students_and_other_Beginners_(Navarro)/17%3A_Bayesian_Statistics/17.02%3A_Bayesian_Hypothesis_Tests)
- [https://bookdown.org/probability/_inference2/bayesian-testing.html](https://bookdown.org/probability/_inference2/bayesian-testing.html)
- [https://www.probabilitycourse.com/chapter9/9_1_8_bayesian_hypothesis_testing.php](https://www.probabilitycourse.com/chapter9/9_1_8_bayesian_hypothesis_testing.php)
- [https://michael-franke.github.io/intro-data-analysis/ch-03-07-hypothesis-testing-Bayes-hypotheses.html](https://michael-franke.github.io/intro-data-analysis/ch-03-07-hypothesis-testing-Bayes-hypotheses.html)

### Bayes Factor

- [Video](https://www.youtube.com/watch?v=lG4VkPoG3ko)
- [https://austinrochford.com/posts/2013-05-17-bayesian-hypothesis-testing-with-pymc.html](https://austinrochford.com/posts/2013-05-17-bayesian-hypothesis-testing-with-pymc.html)
- [http://eointravers.com/post/hypothesis/](http://eointravers.com/post/hypothesis/)
- [https://mspeekenbrink.github.io/sdam-book/ch-Bayes-factors.html](https://mspeekenbrink.github.io/sdam-book/ch-Bayes-factors.html)