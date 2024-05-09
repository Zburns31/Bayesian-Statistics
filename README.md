# Bayesian-Statistics

This repository contains my course notes and course summary from Bayesian Statistics (ISYE 6420)

## Course Resources
- [OMSCS Course Page](https://omscs.gatech.edu/isye-6420-bayesian-statistics)
- [Course Notes & Python Translations](https://areding.github.io/6420-pymc/intro.html)
- [Textbooks & Resources](https://areding.github.io/6420-pymc/unit1/Unit1-about-this-course.html)
- [Course Website - Practice Problems & Code](https://www2.isye.gatech.edu/isye6420/)

## What is Bayesian Statistics?
Bayesian statistics offers an alternative approach to frequentist statistics, utilizing Bayes' theorem to update our beliefs about model parameters as new data is observed. This method treats parameters as random variables, incorporating prior knowledge and uncertainty, and results in a posterior distribution that provides valuable insights. The background knowledge is expressed as a prior distribution and combined with observational data in the form of a likelihood function to determine the posterior distribution. The posterior can also be used for making predictions about future events.

Unlike frequentist statistics, which relies on fixed parameters and long-run frequency outcomes, Bayesian statistics allows for probability statements about parameters, offering a more intuitive and probabilistic interpretation of the data, and facilitating more informed decision-making, especially with small sample sizes.

Bayesian statistics is a departure from classical inferential (frequentist) statistics that prohibits probability statements about parameters and is based on asymptotically sampling infinite samples from a theoretical population and finding parameter values that maximize the likelihood function. Mostly notorious is null-hypothesis significance testing (NHST) based on p-values.


## Course Summary
This course gives a wholistic overview of Bayesian Statistics and how we can apply this approach to practical problems. The course moves from reviewing the fundamentals of Bayes Theorem and Bayesian Networks to Bayesian Inference via sampling algorithms such as Metropolis-Hastings or Gibbs Sampling. The first half of the course is focused on finding numerical solutions to problems using calculus and integration while the second half of the course is focused on Markov Chain Monte Carlo methods for approximate Bayesian Computation. Further, a big focus of the course is on conjugacy and how we can find the posterior distribution taking advantage of conjugate families. Throughout the course, we used PyMC (Probabilistic Programming Language) to solve a variety of problems such as Time to Event Models, Bayesian Regression & Classification and hierarchial models. The class consisted of 6 homework assignments, a midterm and final exam as well as a final project.

Bayesian Statistics gives an excellent introduction to a wide array of topics and problem types while also exploring the differences against frequentist statistics. The course covers the following topics:

- [Module 2: Bayesian Vs. Frequentist Statistics](./Class%20Notes/Module%202%20Bayesian%20Vs.%20Frequentist%20Statistics/Bayesian%20Statistics.md)
- [Module 3: Probability Overview](./Class%20Notes/Module%203%20Probability%20Overview/Unit%203%20Probability%20Overview.md)
- [Module 4: Distributions, Bayes, Inference, Priors & Empirical Bayes](./Class%20Notes/Module%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes/Unit%204%20Distributions,%20Bayes,%20Inference,%20Priors%20&%20Empirical%20Bayes.md)
- [Module 5: Bayesian Computation](./Class%20Notes/Module%205%20Bayesian%20Computation/Unit%205%20Bayesian%20Computation.md)
- [Module 6: Graphical Models & PPL's](./Class%20Notes/Module%206%20Graphical%20Models%20&%20PPL's/Unit%206%20Graphical%20Models%20&%20PPL’s.md)
- [Module 7: Hierarchial, Generalized Linear & Multilevel Models](./Class%20Notes/Module%207%20Hierarchial,%20GLM%20&%20Multilevel%20Models/Unit%207%20Hierarchial,%20GLM%20&%20Multilevel%20Models.md)
- [Module 8: Missing Data & Time to Event Models](./Class%20Notes/Module%208%20Missing%20Data%20&%20Time%20To%20Event%20Models/Unit%208%20Missing%20Data%20&%20Time%20To%20Event%20Models.md)
- [Module 9: Model Fit & Selection](./Class%20Notes/Module%209%20Model%20Fit%20&%20Selection/Unit%209%20Model%20Fit%20&%20Selection.md)


## Project Summaries

### HW1
The first homework assignment was focused on solidfying the fundamentals before going into anything too complex. We used Pgmpy to create Bayesian networks and calculate marginal probabilities given a conditional probability table. We were also tasked with using Bayes Theorem to calculate different conditional and marginal probabilities through hand calculations.


### HW2
HW2 was focused on using calculus to solve for cumulative distribution functions and find probabilties associated with some event. This meant using integration by parts to calculate the area between some interval. Additionally, we looked at solving problems such as [K-out-of-N](https://catalogimages.wiley.com/images/db/pdf/047139761X.07.pdf) using the binomial distribution to help calculate probabilities of multiple events occuring. Lastly, we looked at finding the Maximum Likelihood Estimates (MLE) of variious distributions, such as the Exponential Distribution. This involved using a prior distribution, and our observed likelihood to calculate the Bayes Estimator (Mean and Variance) by hand.

### HW3
HW3 focused on using priors and conjugacy to find the Bayes Estimator of a posterior distribution. We were given a Jeffrey's uninformative prior, and a MLE and were asked to compute the 95% Equitailed and Highest Density Interval (HDI) credible sets. Going one step further, we also computed the Maxium a Posteriori (MAP) estimator of the posterior. For the Empirical Bayes focus, we were given priors and likelihood functions and asked to calculate by hand the posterior distributions so that we could calculate our Bayes Estimator.

### HW4
The primary focus of HW4 was on Markov Chain Monte Carlo sampling algorithms. Firstly, we looked at Metropolis-Hastings and the Independent Metropolis Algorithms. This involved using a prior and and a bivariate normal PDF to calculate our likehood function by hand. Using this, we could then calculate our proposal function using a uniform distribution. After this, we could then implement the derived functions into Python to create our own Metropolis sampling algorithm. A similar process was followed for the Gibbs Sampling algorithm as well.

### HW5
HW5 was more focused on approximate Bayesian computation using PyMC. We looked at a variety of problems such as difference of means, Bayesian Logistic Regression and Poisson Regression.

### HW6
HW6 was focused on Time-to-Event Models, imputing missing data, Hierarchial Models and Model Selection methods. There was a heavy focus on utilizing PyMC to calculate credible sets, predictions and make inferences about the data. The model fit and selection portion was focused on identifying important predictors in the GLM and assessing outliers and their associated impact on the model. This involved using the Empirical Cumulative Distribution function and posterior predictive distributions to analyze whether an observation is an outlier or not.

### Project
For our final project, we were allowed to choose any dataset where we could tackle a problem using Bayesian Methods. For my project, I chose to use Bayesian Hierarchial Models to forecast bike rentals using a Bike Sharing dataset. For this analysis, I looked at univariate and multivariate regression, as well as a Guassian Random-Walk Process. A large part of the work went into experimenting with different priors on predictions and how to formulate these Bayesian Models to get good results. My report can be found [here](./Midterm%20Report/Project-Burns.pdf).

### Midterm & Exam
Both the midterm and final exams were a cumulative representation and collection of questions we had covered across the course. There was a mix of numerical and approximate methods, requiring us to compute posterior distributions by hand and with PyMC.

# Questions?

If you are a potential employer looking at this, I would be happy to go into more depth about the solutions to the work on the above assignments.
