# PyMC Overview

---

# Core Concepts

- PyMC has three core functions that map to the traditional Bayesian workflow:
    - `sample_prior_predictive` ([docs](https://www.pymc.io/projects/docs/en/stable/api/generated/pymc.sample_prior_predictive.html))
    - `sample` ([docs](https://www.pymc.io/projects/docs/en/stable/api/generated/pymc.sample.html))
    - `sample_posterior_predictive` ([docs](https://www.pymc.io/projects/docs/en/stable/api/generated/pymc.sample_posterior_predictive.html))

- **Prior predictive sampling** helps understanding the relationship between the parameter priors and the outcome variable, before any data is observed
- **Sampling** is used to infer the posterior distribution of parameters in a model, conditioned on observed data
- Finally, **posterior predictive sampling** can be used to predict new outcomes, conditioned on the posterior parameters

# XArrays

- [Great Post](https://cluhmann.github.io/inferencedata/)

# Coodinates & Dims

- [Great Post](https://oriolabrilpla.cat/en/blog/posts/2020/pymc3-arviz.html)

# Resources

- [https://www.pymc-labs.com/blog-posts/out-of-model-predictions-with-pymc/](https://www.pymc-labs.com/blog-posts/out-of-model-predictions-with-pymc/)

### Multilevel Models

- [https://www.pymc.io/projects/examples/en/2022.01.0/case_studies/multilevel_modeling.html](https://www.pymc.io/projects/examples/en/2022.01.0/case_studies/multilevel_modeling.html)

### Bayesian Methods for Hackers

- [https://github.com/CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/tree/master](https://github.com/CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/tree/master)