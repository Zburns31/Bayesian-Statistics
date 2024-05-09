# Bayesian Vs. Classical Statistics

- [Bayesian Statistics](../Module%202%20Bayesian%20Vs.%20Frequentist%20Statistics/Bayesian%20Statistics.md)

# Conditioning - The queen of spades

- Remember, by definition, independence means $P(AB) = P(A)P(B)$
    - Here we have a standard deck of 52 cards. There are 13 of each suit and 4 queens. Define Event A as drawing a spade and Event B as drawing a queen
    - $P(AB)$ is then the probability of drawing the queen of spades. This card is unique, so it occurs $\dfrac{1}{52}$ times
- If we multiply it out:
    - $P(A)P(B) = \frac{13}{52} \times \frac{4}{52} = \frac{1}{52}$
    - So $P(AB) = P(A)P(B)$ and the two events are independent
- ***But are they still independent if we first remove the two of diamonds from the deck? Let's see***
    - $P(AB) = \frac{1}{51}$
    - $P(AB) = P(A)P(B) = \frac{13}{51} \times \frac{4}{51} = \frac{52}{2601}$
    - $\frac{1}{51} \neq \frac{52}{2601}$
- **They are no longer independent!** It's easy to follow the math, but the intuition can take time to click. Think about it in terms of the information you have. If there are an equal number of cards left in the deck from each suit, any given suit has the same probability of being a queen
    - In the second case, if you draw a spade, heart, or club, the probability your card is a queen will be different than the probability of a queen given that you drew a diamond. You have slightly more information about diamonds since there are only 12 remaining in the deck
    - So now depending on the suit, a queen might be more likely. In other words, the probability of a queen is no longer independent of the suit

## Independence

- $A,B$ independent $\Leftrightarrow A,B P(AB) = P(A)P(B)$
- $P(A|B) = \dfrac{P(AB)}{P(B)}$
- By Symmetry $P(AB) = P(B|A)P(A)$
- $A,B$ independent
    - $P(A|B) = P(A)$
    - $P(B|A) = P(B)$
- [Examples](./Unit%203%20Probability%20Overview/Examples.md)

# Bayesian Learning & Bayes Rule

- There are 4 components to the Bayes Rule:
    1. **Posterior probability** (updated probability after the evidence is considered)
    2. **Prior probability** (the probability before the evidence is considered)
    3. **Likelihood** (probability of the evidence, given the belief is true)
    4. **Marginal probability** (probability of the evidence, under any circumstance)

$$
\underbrace{P(H_i)}_{\text{prior prob}} \rightarrow  P(H_i|A) = \underbrace{\dfrac{P(A|H_i)}{P(A)}}_{\text{Posterior}} \cdot P(H_i)
$$

$$
\underbrace{P(A|B)}_{\text{posterior}} = \underbrace{P(A)}_{\text{Prior}} \space * \space \dfrac{\underbrace{P(B|A)}_{\text{likelihood}}}{\underbrace{P(B)}_{\text{marginal}}}
$$

- Other Notes
    - The posterior is sometimes known as the Bayes Factor
    - $P(A|H_i)$ is known as the likelihood
        - This is another conditional probability. It is the probability of the evidence being present, given the hypothesis is true
    - $P(A)$ is known as the evidence
- More generally, we can write Bayes Rule as:

$$
P(Hypothesis|Evidence) = P(Hypothesis) * \dfrac{P(Evidence|Hypothesis)}{P(Evidence)}
$$

## **Bayes Theorem Notes**

[Bayes Theorem & Ingredients For Inference](../Module%202%20Bayesian%20Vs.%20Frequentist%20Statistics/Bayesian%20Statistics/Bayes%20Theorem%20&%20Ingredients%20For%20Inference.md)

# Causal Vs. Logical Independence

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
    - **The total probability rule lets you take a joint probability distribution over a set of variables and produce a distribution over a single variable**
    - It is a useful tool for decomposing a complex probability problem into simpler, more manageable parts. The Law of Total Probability states that for any event A and a partition of the sample space into mutually exclusive and exhaustive events B₁, B₂, ..., Bₙ, the probability of event A can be expressed as the sum of the probabilities of A given each partition element, weighted by the probabilities of those partition elements

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

## Lecture errata (Unit 3)

- There's a mistake at 5:40: $0.94\times 0.3 + 0.95\times 0.5 + 0.97\times 0.2 \space \text{equals} \space 0.951 \space, \text{not} \space 0.957$
    - Video: **Manufacturing Bayes**

# Bayes Networks

- [Bayesian Networks](./Bayesian%20Networks.md)

# Sensitivity, Specificity, and Relatives

[Classification: Model Evaluation](./Classification%20Model%20Evaluation.md)