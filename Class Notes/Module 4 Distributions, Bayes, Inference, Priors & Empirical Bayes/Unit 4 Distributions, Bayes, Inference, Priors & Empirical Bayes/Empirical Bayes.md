# What is it?

- One of the practical challenges with Bayesian inference methods is that it requires a statistician to hold some prior belief of the parameter that they are trying to estimate
    - So, how might one go about specifying their prior belief if you don’t have an informed guess? One way might be to assign a “flat prior” — a prior where you specify that every value of your parameter is equally likely
    - Another way is to use **Empirical Bayes**, where your data is used to estimate the prior by looking at what potential distributions may be
- There are two main steps in Empirical Bayes:
    1. Estimate the overall distribution of your data
    2. Use that distribution as your prior for estimating each average
    - [Reference](http://varianceexplained.org/r/empirical_bayes_baseball/)

# How do Empirical Bayes Methods Work?

- There are different Bayes estimation techniques for each type of probability distribution, but all share the same basic format:
    1. Create [hyperparameters](https://deepai.org/machine-learning-glossary-and-terms/hyperparameter) (probability distributions) instead of fixed values for each parameter in a prior assumption
    2. Test the prior probability on a sample of data, which turns the hyperparameters into an approximate value for each parameter
    3. Use this updated prior assumption, which is technically a [posterior probability](https://deepai.org/machine-learning-glossary-and-terms/posterior-probability), as a prior probability when running the model on the full data set

# Parametric Approach

- $X_i|\theta_i \sim f_i(x_i|\theta)$ where $i = 1,2,...n$ and these samples are independent, not IID (independent and identically distributed)
    - Not IID because the likelihood functions could be different
- $\theta_i \sim \pi(\theta_i|\xi)$ where $\theta$ is assumed to be IID
    - $\xi$ is a common hyperparameter

- If $f_i \equiv f$, then $X_i$ are i.i.d (marginally). The posterior is:

$$
\pi(\theta_i|X_i, \xi) = \dfrac{f(x_i|\theta_i). \pi(\theta_i|\xi)}{m(x_i|\xi)}
$$

- If $\xi$ is unknown, it can be estimated from $X_1, X_2, ..., X_n$ via:
    - MLE (called MLE II Approach)
    - Moment Matching (MM)

# Non-Parametric

- We assume only that parameters of $\theta_i$ are $i.i.d$, no family of distribution is specified
- Use data to estimate marginal or the prior directly
- Has limited practical value

# Problem Types

- Find the Empirical Bayes Estimator of some parameter given a prior and likelihood function
    - Steps:
        1. Find the marginal via the integral of the prior and likelihood
        2. Form the marginal by taking the product of n and the marginal
        3. Take the log to remove the product operator and replace with sum
        4. Find the MLE by taking the partial derivative w.r.t to the parameter in question

# Resources

- [https://online.stat.psu.edu/stat555/node/40/](https://online.stat.psu.edu/stat555/node/40/)
- [https://en.wikipedia.org/wiki/Empirical_Bayes_method#Parametric_empirical_Bayes](https://en.wikipedia.org/wiki/Empirical_Bayes_method#Parametric_empirical_Bayes)
- [https://kiwidamien.github.io/shrinkage-and-empirical-bayes-to-improve-inference.html](https://kiwidamien.github.io/shrinkage-and-empirical-bayes-to-improve-inference.html)
- [https://online.stat.psu.edu/stat555/node/40/](https://online.stat.psu.edu/stat555/node/40/)