# What is the hierarchy?

- In a **Bayesian hierarchical model**, the model for the data depends on certain parameters, and those parameters in turn depend on other parameters
    - Hierarchical modelling provides a framework for building complex and high-dimensional models from simple and low-dimensional building blocks
- The Bayesian Hierarchical Model (BHM) links the sub-models together, correctly propagating uncertainties in each sub-model from one level to the next
    - At each step ideally we will know the conditional distributions
    - The aim is to build a complete model of the data
    - Principled way to include systematic errors, selection effects

# How do they work?

- Hierarchical Bayesian Models work by incorporating multiple levels of uncertainty into the model structure. In a hierarchical model, parameters are not treated as fixed but rather as random variables with their own probability distributions
    - These distributions, in turn, can have their own hyperparameters, which can also be assigned prior distributions, creating a multilevel hierarchy of parameters and hyperparameters
- The main advantage of hierarchical models is that they allow for the sharing of information across different levels of the hierarchy, leading to more accurate and robust inferences, especially when dealing with small sample sizes or sparse data

# Factorial Designs

- Expanding One-Way ANOVA to more than a single factor

# Generalized Linear Models

- [Generalized Linear Models](./Unit%207%20Hierarchial,%20GLM%20&%20Multilevel%20Models/Generalized%20Linear%20Models.md)

- What is generalized?
    - $y_i$ remains independent, but distribution is generalized from normal to exponential family
    - The mean of $y_i$ is a function of $\beta_0 + \beta_1 x_{i1} + ....+\beta_k x_{ik} = l_i$
        - $\mu_i = Ey_i = g(l_i) \rightarrow g$ is a ***link function***
        - Variance of $y_i$ is not constant, depends on $\mu_i$

# Multilevel Models

- Random Effects Models
- Mixed Effects Models

# Resources

- [https://s3.amazonaws.com/OM-SHARE/Hierarchical+Bayes+SSRN-id655541.pdf](https://s3.amazonaws.com/OM-SHARE/Hierarchical+Bayes+SSRN-id655541.pdf)
- file:///Users/zacburns/Downloads/manuscript-1.pdf

### Bayesian Regression

- [https://statswithr.github.io/book/introduction-to-bayesian-regression.html](https://statswithr.github.io/book/introduction-to-bayesian-regression.html)