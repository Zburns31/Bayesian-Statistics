# Model Fitting & Comparison Metrics

## Deviance

- Intuitively, it measures the **deviance of the fitted model with respect to a perfect model for $P[Y=1|X_1=x_1,…,X_k=x_k]$**
    - This perfect model is known as the ***saturated model***
- For a model with likelihood $f(y|\theta)$, the deviance is given by: $D(\theta) = -2 \log f(y|\theta)$
    - More precisely, the deviance is defined as the difference of likelihoods between the fitted model and the saturated model
        - However, the deviance of the saturated model is always equal to 1
        - As a consequence, **the deviance is always larger or equal than zero, being zero only if the fit is perfect**
- Alternatively, we can use the ***saturated deviance*** which is given by: $D(\theta) = -2 (\log f(y|\theta) - \log f(y|\theta_s)$
- **TL;DR: Smaller deviance is better**

### How it works

1. Observed Data: You start with a set of observed data, which could be anything from the number of people who buy a product to the outcome of a medical experiment. This data is what you're trying to model or understand
2. Model's Predictions: You have a statistical model that makes predictions based on certain parameters. These parameters are like the settings or assumptions of your model. For example, in a linear regression model, the parameters are the coefficients that determine how variables are related
3. Deviance Calculation: Deviance is a way to measure how well your model's predictions match the actual observed data. It's calculated by comparing the likelihood of the observed data given your model's predictions to the likelihood of the observed data under an ideal model. This ideal model is usually a model with perfect predictions
4. Good Fit vs. Bad Fit: Lower deviance values indicate a better fit between your model and the observed data
    1. When deviance is small, it means that your model's predictions are very close to the actual data. A larger deviance means that your model's predictions are not as good at explaining the data
5. Model Comparison: You can use deviance to compare different models
    1. For example, if you have two models, you can calculate the deviance for each and see which one provides a better fit to the data

## Deviance Information Criterion (DIC)

- The DIC is a more Bayesian alternative that uses the posterior mean point estimate $\theta_{bayes}$ instead of the MLE estimate. Here $\theta_{bayes}$ is the expected value of $\theta$:

$$
DIC = -2 \sum_{i=1}^n \log (y_i|\theta_{bayes}) + 2_{var_{posterior}} \log(y_i|\theta)
$$

- It is closely related to the Akaike information criteria (AIC) which is defined as $2k−2 \ln \hat \ell$, where $*k*$ is the number of parameters in a model and $\hat \ell$ is the maximized log-likelihood
    - The DIC makes some changes to this formula
        - Firstly by replacing a maximized log-likelihood with the log-likelihood evaluated at the Bayes estimate $\hat \theta$ and by replacing $k$ with an alternative correction

### How it works

1. **Model Likelihood**: In Bayesian statistics, we start with a statistical model that describes how we think the data was generated. This model has parameters (numbers that describe the model), which we often want to estimate from the data
    1. The likelihood is a measure of how well the model explains the observed data
2. **Complexity Penalty**: DIC takes into account not only how well the model fits the data but also the complexity of the model
    1. More complex models, with lots of parameters, are more likely to overfit the data, which means they may not generalize well to new data. DIC includes a penalty for model complexity to avoid favoring overly complex models
3. **Calculation**: To calculate DIC, we first compute the average of the deviance across a large sample of model parameters
    1. The deviance is a measure of how well the model fits the data
    2. The DIC is then computed as the difference between this average deviance and the deviance at the maximum likelihood point
        1. The larger the difference, the better the model fit
4. **Interpretation**: A lower DIC means a better model fit
    1. It suggests that the model does a good job of explaining the data while taking into account its complexity
    2. When comparing different models, you would choose the one with the lowest DIC because it strikes a good balance between model fit and simplicity

## Ibrahim-Laud Criteria

- **TL;DR:** The L metric is a measure of distance between the original y values and the PPC. The lower L is, the better
- The criterion is constructed from the posterior predictive distribution of the data, and can be written as a sum of two components, one involving the means of the posterior predictive distribution and the other involving the variances
    - It can be viewed as a Bayesian goodness-of-fit statistic which measures the performance of a model by a combination of how close its predictions are to the observed data and the variability of the predictions
- It is a general Bayesian criterion for model assessment called the **weighted L measure**
    - The measure is constructed from the posterior predictive distribution of the data and is based on weighting the observations according to the sampling variance of their future response vector
    - The weight component in the weighted L measure plays the role of a penalty term in the criterion, in which a greater weight assigned to covariate values implies a greater penalty term on the dimension of the model

## Conditional Predictive Ordinate (CPO)

- The conditional predictive ordinate (CPO) is a Bayesian diagnostic which detects surprising observations
- Conditional predictive ordinates (CPO, Pettit [1990](https://becarioprecario.bitbucket.io/inla-gitbook/ch-INLA.html#ref-pettit:1990)) are a cross-validatory criterion for model assessment that is computed for each observation as:

$$
CPO_i=\pi(y_i∣y_{−i})
$$

- [In the cross-validation sense, this is a “leave-out one” approach](https://open.library.ubc.ca/collections/24/items/1.0354974)
    - This means that each data point is left out one at a time, and the model is used to predict that left-out data point based on the remaining data. The accuracy of these predictions is then used to assess the model’s performance
- Hence, for each observation its CPO is the posterior probability of observing that observation when the model is fit using all data but $y_i$
    - Large values indicate a better fit of the model to the data, while small values indicate a bad fitting of the model to that observation and, perhaps, that it is an outlier
- A measure that summarizes the CPO is:

    $$
    −\sum_i^n \log(CPO_i)
    $$

    - with smaller values pointing to a better model fit
- [Good reference](https://mybiostats.files.wordpress.com/2015/03/dicmagicformmhalgoy9.pdf)

## Stochastic Search Variable Selection (SSVS)

- Stochastic search variable selection (SSVS) identifies promising subsets of multiple regression covariates via Gibbs sampling
    - For SSVS, you express the relationship between the response variable and the candidate predictors in the framework of a hierarchical normal mixture model, where latent variables are used to identify subset choices
    - In this framework, the promising subsets of predictors are identified as those that have a higher posterior probability
        - SSVS uses Markov chain Monte Carlo (MCMC) sampling to indirectly sample from this posterior distribution on the set of possible subset choices. Subsets that have a higher posterior probability are identified by their more frequent appearance in the MCMC sample
- The basic idea of SSVS is to assign commonly used prior variances to parameters, which should be included in a model, and prior variances close to zero to irrelevant parameters
    - By that, relevant parameters are estimated in the usual way and posterior draws of irrelevant variables are close to zero so that they have no significant effect on forecasts and impulse responses
    - This is achieved by adding a hierarchial prior to the model, where the relevance of a variable is assessed in each step of the sampling algorithm
- [The goal of SSVS is to estimate the posterior regime probabilities, which determine whether corresponding coefficients should be included in the  model](https://www.mathworks.com/help/econ/implement-bayesian-variable-selection.html)
    - [In the Bayesian formulation, the prior distribution of each regression coefficient is assumed to be a mixture of a point mass at 0 and a normal distribution with zero mean2](https://link.springer.com/article/10.1007/s11222-009-9165-4)[3](https://link.springer.com/content/pdf/10.1007/s11222-009-9165-4.pdf). [This implies that the prior of each coefficient is a Gaussian mixture model](https://www.mathworks.com/help/econ/implement-bayesian-variable-selection.html)
- The SSVS method introduces latent, binary random variables, such that:
    - [If the variable equals 1, it indicates that the coefficient is included in the model](https://www.mathworks.com/help/econ/implement-bayesian-variable-selection.html)
    - [If the variable equals 0, it indicates that the coefficient is excluded from the model1](https://www.mathworks.com/help/econ/implement-bayesian-variable-selection.html)
- [The SSVS method circumvents the complexity induced by degenerate variates by assigning a Gaussian distribution with a mean of 0 and a small variance to the prior for a coefficient being excluded](https://www.mathworks.com/help/econ/implement-bayesian-variable-selection.html)
    - [The prior for the coefficient being included can be a normal distribution where the variance is sufficiently away from zero](https://www.mathworks.com/help/econ/implement-bayesian-variable-selection.html)


# Outliers Analysis

- [Outliers Analysis](./Unit%209%20Model%20Fit%20&%20Selection/Outliers%20Analysis.md)


# Resources

### Deviance & Deviance Information Criterion (DIC)

- [https://bookdown.org/egarpor/SSS2-UC3M/logreg-deviance.html](https://bookdown.org/egarpor/SSS2-UC3M/logreg-deviance.html)
- [https://sjster.github.io/introduction_to_computational_statistics/docs/Production/BayesianInference.html#log-likelihood-and-deviance](https://sjster.github.io/introduction_to_computational_statistics/docs/Production/BayesianInference.html#log-likelihood-and-deviance)
- [https://dm13450.github.io/2018/01/18/DIC.html](https://dm13450.github.io/2018/01/18/DIC.html)
- [https://archive.ph/hw0fl](https://archive.ph/hw0fl)

### Conditional Predictive Ordinate

- [https://jrnold.github.io/bayesian_notes/model-checking.html](https://jrnold.github.io/bayesian_notes/model-checking.html)
- [https://mybiostats.files.wordpress.com/2015/03/dicmagicformmhalgoy9.pdf](https://mybiostats.files.wordpress.com/2015/03/dicmagicformmhalgoy9.pdf)
- [https://becarioprecario.bitbucket.io/inla-gitbook/ch-INLA.html](https://becarioprecario.bitbucket.io/inla-gitbook/ch-INLA.html)

### SSVS

- [https://hackmd.io/@manukris/SSVS](https://hackmd.io/@manukris/SSVS)