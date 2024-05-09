# Generalized Linear Models

---

# Deviances

- Standard measures of model performance are ***deviances:***
    
    $$
    D = -2\log \dfrac{\text{likelihood of the fitted model}}{\text{likelihood of the saturated model}}
    $$
    
    - The saturated model is the best model possible
        - If you were to model the $y_i$’s themselves which is the best thing you can do
- For Logistic Regression:
    
    $$
    D =-2\sum_{i=1}^k y_i \log \dfrac{\hat y_i}{y_i} + (n_i-y_i) \log \dfrac{n_i - \hat y_i}{n_i - y_i}
    $$
    
    - Where:
        - $\hat y_i = n_ip_i$ is the model fit for $y_i$
        - For saturated model: $\hat p_i = \dfrac{y_i}{n_i}, \hat y_i = y_i$
        - $n$ is the number of cases for which covariates coincide, and $k$ is the number of such groups
- For Poisson Regression:
    
    $$
    D =-2\sum_{i=1}^n \left ( y_i \log \dfrac{y_i}{\hat y_i} - (y_i - \hat y_i) \right )
    $$
    
    - Where:
        - $\hat y_i = \exp \lbrace b_0 + b_1x_{i1} + .... + b_kx_{ik} \rbrace$

# Multinomial Regression

# Resources

- [https://jrnold.github.io/bayesian_notes/generalized-linear-models.html](https://jrnold.github.io/bayesian_notes/generalized-linear-models.html)
- [https://towardsdatascience.com/bayesian-generalized-linear-models-with-pyro-b80bc08d7b75](https://towardsdatascience.com/bayesian-generalized-linear-models-with-pyro-b80bc08d7b75)
- [https://spia.uga.edu/faculty_pages/rbakker/bayes/Day2.applied.bayes.pdf](https://spia.uga.edu/faculty_pages/rbakker/bayes/Day2.applied.bayes.pdf)