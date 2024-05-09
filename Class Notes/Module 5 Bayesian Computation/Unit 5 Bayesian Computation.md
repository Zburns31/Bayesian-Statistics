# Unit 5: Bayesian Computation

# Approximate Bayesian Computation (ABC)

- **An ABC algorithm** estimates the posterior of a parameter by simulating the model to produce artificial data sets $*X*$ using sample parameters taken from the prior distribution
    - A comparison of how similar the artificial data set produced by the sample parameter from the prior to the observed real data set $*Y*$ is undertaken by computing a distance $\rho(X,Y)$
    - Parameter samples that produce artificial data sets that are ‘**very close’** to the real data set *$Y$* are collected as samples from the posterior distribution
    - How close is ‘very close’ is determined by a pre-defined hyper-parameter called the **tolerance** ($\epsilon$), with parameter’s that produce artificial data closer than $\epsilon$ to the observed data being accepted as part of the posterior

# How it works

- The general ABC approach

    ![Untitled](./Unit%205%20Bayesian%20Computation/Untitled.png)


# Numerical Approaches

- [Numerical Approaches](./Unit%205%20Bayesian%20Computation/Numerical%20Approaches.md)

# Laplace’s Method

- [Laplace’s Method](./Unit%205%20Bayesian%20Computation/Laplace’s%20Method.md)

# Markov Chain Monte Carlo (MCMC)

- [Markov Chain Monte Carlo Methods](./Unit%205%20Bayesian%20Computation/Markov%20Chain%20Monte%20Carlo%20Methods.md)

# Resources

- [https://people.duke.edu/~ccc14/sta-663/MCMC.html#gibbs-sampler](https://people.duke.edu/~ccc14/sta-663/MCMC.html#gibbs-sampler)
- [https://bookdown.org/kevin_davisross/bayesian-reasoning-and-methods/mcmc.html](https://bookdown.org/kevin_davisross/bayesian-reasoning-and-methods/mcmc.html)

### **Approximate Bayesian Computation**

- [Approximate Bayesian Computation Overview](https://towardsdatascience.com/the-abcs-of-approximate-bayesian-computation-bfe11b8ca341)
- [https://betanalpha.github.io/assets/case_studies/probabilistic_computation.html](https://betanalpha.github.io/assets/case_studies/probabilistic_computation.html)
- [https://bayesiancomputationbook.com/markdown/chp_08.html](https://bayesiancomputationbook.com/markdown/chp_08.html)