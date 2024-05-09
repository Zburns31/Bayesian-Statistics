# What is it?

- **Bayesian inference** is therefore just the process of deducing properties about a population or probability distribution from data *using Bayes’ theorem.* That’s it
- Bayesian’s turn prior information and observed data into a posterior distribution. We do this using Bayes theorem

# Estimation

- We’ve seen some examples now of how to get the posterior distributions of our models. Now we’re asking: ***what is the meaning of the posterior and what can we do with it?***
    - We need to be able to summarize it in useful ways and make decisions based on these summaries
    - Point estimates are the simplest summary of the posterior
- For a Bayesian, the posterior is the ultimate summary of an experiment, prior info and observed data
    - The only logical approach to incorporate prior information is using Bayes Theorem
- When making point estimates of unknown parameters, we should make the choices that minimize the loss
    - ***Nevertheless, the best estimate depends on the kind of loss function we are using***

![Untitled](./Bayesian%20Decision%20Theory/Untitled.png)

- Bayes' estimators are functions of $X_1,...,X_n$
    - When $X_1,...,X_n$ are observed, Bayes’ estimators are called are called an action $a$
        - A **posterior mean** minimizes $\mathbb{E}^{\theta|X}[(\theta - a)^2]$ with respect to $a$
            - Quadratic (or Squared) error
        - A **posterior median** minimizes $\mathbb{E}^{\theta|X}[|\theta - a|]$ with respect to $a$
            - Linear error
- Define $L_C(\theta, a)$ as follows:

$$
L_C(\theta, a) = \begin{cases}0, & |\theta-a| \leq c\\1, & \text{else}\end{cases}
$$

- The **posterior mode** is an action that minimizes $\lim_{c \rightarrow 0}\mathbb{E}^{\theta|X}[L_C(\theta, a)]$ with respect to $a$
    - When the posterior mode is used, we call this the ***maximum posterior estimator***

## Examples

- If you are advising a patient on his/her life expectancy, it is easy to imagine that large errors are far more problematic than small ones
    - And perhaps the loss increases as the **square** of how far off your single number estimate is from the truth
    - For example, if she is told that her average life expectancy is two years, and it is actually ten, then her estate planning will be catastrophically bad, and she will die in poverty
        - In the case when the loss is proportional to the **quadratic** error, one can show that the optimal one-number estimate is the **mean** of the posterior distribution
- Finally, in some cases, the penalty is 0 if you are exactly correct, but constant if you’re at all wrong
    - This is the case with the old saying that close only counts with horseshoes and hand grenades; i.e., coming close but not succeeding is not good enough
        - And it would apply if you want a prize for correctly guessing the number of jelly beans in a jar
        - Here, of course, instead of minimizing expected losses, we want to **maximize the expected gain**
        - If a Bayesian is in such a situation, then his/her best one-number estimate is the **mode** of his/her posterior distribution, which is the most likely value

# MLE Vs. Posterior Mean

- The posterior mean is a linear combination of its frequentist estimate (likelihood) and the prior mean
- [Good Reference](https://stats.stackexchange.com/questions/305465/maximum-likelihood-estimator-and-posterior-mean)

# Bayes Risk

- The most common Bayes estimator is the **posterior mean**. There is a frequentist rule that minimizes **Bayes risk:**

    $$
    \mathbb{E}^\theta\mathbb{E}^{X|\theta}[(\theta - \delta(X))^2]
    $$

- This represents the double expectation of the squared error loss
- which is the posterior mean $\delta_B(X)$
    - If X is observed, that is, if $\delta_B(X)$ is conditioned on $X$, the result is ***Bayes action***
- Some errors may be inevitable: ***the minimum risk (shaded area) is called the Bayes risk***

    ![Untitled](./Bayesian%20Decision%20Theory/Untitled%201.png)

- Bayes risk is defined as:

    $$
    r(\theta, \delta) = \mathbb{E}^\theta\mathbb{E}^{X|\theta}[(\theta - \delta(X))^2]=\mathbb{E}^X\mathbb{E}^{\theta|X}[(\theta - \delta(X))^2]
    $$

- Posterior mean minimizes Bayes risk

# Bayes Estimator

![Untitled](./Bayesian%20Decision%20Theory/Untitled%202.png)

# Resources

- [Bayesian Decision Theory.pdf](./Bayesian%20Decision%20Theory/Bayesian_Decision_Theory.pdf)
- [https://statswithr.github.io/book/losses-and-decision-making.html](https://statswithr.github.io/book/losses-and-decision-making.html)
- [https://www.cs.ubc.ca/~lowe/425/slides/12-Classifiers-6up.pdf](https://www.cs.ubc.ca/~lowe/425/slides/12-Classifiers-6up.pdf)
- [https://bookdown.org/johnnydoorn/bayesbookdown/model-estimation-section.html#relation-to-hypothesis-testing](https://bookdown.org/johnnydoorn/bayesbookdown/model-estimation-section.html#relation-to-hypothesis-testing)
- [https://www.byclb.com/TR/Tutorials/neural_networks/ch4_1.htm](https://www.byclb.com/TR/Tutorials/neural_networks/ch4_1.htm)
- [https://towardsdatascience.com/bayesian-decision-theory-81103a68978e](https://towardsdatascience.com/bayesian-decision-theory-81103a68978e)
- [https://www2.stat.duke.edu/~rcs46/lecturesModernBayes/601-module2-decision-theory/lecture3-decision-theory.pdf](https://www2.stat.duke.edu/~rcs46/lecturesModernBayes/601-module2-decision-theory/lecture3-decision-theory.pdf)
- [https://www2.stat.duke.edu/~rcs46/books/babybayes-master.pdf](https://www2.stat.duke.edu/~rcs46/books/babybayes-master.pdf)
- [https://www2.stat.duke.edu/~rcs46/books/bayes_manuscripts.pdf](https://www2.stat.duke.edu/~rcs46/books/bayes_manuscripts.pdf)

## Bayes Risk

- [https://stats.stackexchange.com/questions/540140/what-is-the-difference-between-the-risk-function-used-in-bayesian-inference-and](https://stats.stackexchange.com/questions/540140/what-is-the-difference-between-the-risk-function-used-in-bayesian-inference-and)

### MLE

- [https://www2.stat.duke.edu/courses/Fall16/sta611.01/Lecture/Lecture10.pdf](https://www2.stat.duke.edu/courses/Fall16/sta611.01/Lecture/Lecture10.pdf)
- [https://people.eecs.berkeley.edu/~russell/classes/cs294/f05/papers/vidakovic-handout3.pdf](https://people.eecs.berkeley.edu/~russell/classes/cs294/f05/papers/vidakovic-handout3.pdf)