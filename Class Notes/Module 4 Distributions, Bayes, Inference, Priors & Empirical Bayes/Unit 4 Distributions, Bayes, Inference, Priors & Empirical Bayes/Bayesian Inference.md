# Predictive Distributions

- The word ‘predictive’ in predictive distribution refers to the prediction for observations
    - The difference between prior(posterior) distribution and prior(posterior) predictive distribution is that the former one is a distribution for parameters(or weights) theta whereas the latter one is a distribution for observations(y, also called target value)
-

# Prior Predictive Distribution

- They represent the distribution of data that would be expected if one were to generate data from the prior distribution alone, before observing any actual data
    - In other words, prior predictive distributions allow you to simulate or predict what your data might look like based on your prior beliefs or knowledge about the model's parameters
    - This is essentially saying what our combined prior and likelihood will do before looking at our sample data
- Recall the marginal distribution, which is sometimes called the ***prior predictive distribution***

    $$
    p(x) = p(x_1,x_2,...x_n) = ∫ f (x | θ)π(θ)dθ
    $$

    - This is often useful as a way to see if the sampling distribution or prior we have chosen is appropriate, after integrating out all unknown parameters
    - Sample directly from the prior predictive and assess whether the samples are consistent with our prior knowledge
- The product under the integral reduces to the joint posterior density $p(x,θ∣y)$, so that the integral is simply marginalizing out the parameters $θ$, leaving the predictive density $p(\hat x∣x)$ of future observations given past observations
- The *prior predictive* distribution is the distribution of *𝑋* $$ "averaged" over all possible values of $*\theta*$
    - The prior predictive distribution can be interpreted as the distribution of **averaged(or weighted)** $y$ over all possible values of theta

# Posterior Predictive Distribution

- A posterior predictive distribution is a fundamental concept in Bayesian statistics that helps you make predictions about future or unobserved data based on the information contained in your observed data and the posterior distribution of your model parameters. It provides a probabilistic way to quantify uncertainty about future outcomes and assess the adequacy of your statistical model
- The below is called the ***posterior predictive distribution***

$$
f(x_{n+1}|x_1,...,x_n) = \int \underbrace{f(x_{n+1} | \theta)}_{\text{likelihood density}} \underbrace{\pi(\theta | x_1,...,x_n)}_{\text{posterior}}d\theta
$$

# Predictive Mean

- The below is called the ***predictive mean***

$$
\hat{X}_{n+1} = \int x_{n+1} \cdot f(x_{n+1}|x_1,...,x_n) dx_{n+1} = E^fX_{n+1}
$$

# Predictive Variance

- The below is called the predictive variance

$$
\int(x_{n+1} -\hat X_{n+1})^2 \cdot f(x_{n+1}|x_1,...,x_n) dx_{n+1}
$$

# Resources

- [U4L13.pdf](./Bayesian%20Inference/U4L13.pdf)
- [https://stats.stackexchange.com/questions/438218/intuition-behind-posterior-predictive-distribution](https://stats.stackexchange.com/questions/438218/intuition-behind-posterior-predictive-distribution)
- [https://www2.stat.duke.edu/courses/Fall21/sta601.001/slides/03-normal-predictive-distributions.html#1](https://www2.stat.duke.edu/courses/Fall21/sta601.001/slides/03-normal-predictive-distributions.html#1)
- [https://medium.com/jun94-devpblog/bayesian-dl-1-properties-of-gaussian-distribution-and-prior-posterior-predictive-distribution-b02529b894a8](https://medium.com/jun94-devpblog/bayesian-dl-1-properties-of-gaussian-distribution-and-prior-posterior-predictive-distribution-b02529b894a8)
- [https://www.medicine.mcgill.ca/epidemiology/Joseph/courses/EPIB-668/predictive.pdf](https://www.medicine.mcgill.ca/epidemiology/Joseph/courses/EPIB-668/predictive.pdf)
- [https://revbayes.github.io/tutorials/intro_posterior_prediction/](https://revbayes.github.io/tutorials/intro_posterior_prediction/)
- [https://www.linkedin.com/pulse/posterior-distribution-predictive-leonard-mensah-boante](https://www.linkedin.com/pulse/posterior-distribution-predictive-leonard-mensah-boante)
- [https://medium.com/jun94-devpblog/bayesian-dl-1-properties-of-gaussian-distribution-and-prior-posterior-predictive-distribution-b02529b894a8](https://medium.com/jun94-devpblog/bayesian-dl-1-properties-of-gaussian-distribution-and-prior-posterior-predictive-distribution-b02529b894a8)
- [https://bookdown.org/kevin_davisross/bayesian-reasoning-and-methods/prediction.html](https://bookdown.org/kevin_davisross/bayesian-reasoning-and-methods/prediction.html)
- [https://jrnold.github.io/bayesian_notes/bayesian-inference.html](https://jrnold.github.io/bayesian_notes/bayesian-inference.html)
- [https://stats.stackexchange.com/questions/394648/differences-between-prior-distribution-and-prior-predictive-distribution](https://stats.stackexchange.com/questions/394648/differences-between-prior-distribution-and-prior-predictive-distribution)
- [https://en.wikipedia.org/wiki/Posterior_predictive_distribution#Posterior_predictive_distribution_in_exponential_families](https://en.wikipedia.org/wiki/Posterior_predictive_distribution#Posterior_predictive_distribution_in_exponential_families)