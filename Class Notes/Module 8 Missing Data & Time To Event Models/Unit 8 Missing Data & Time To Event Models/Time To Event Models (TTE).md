# What are they?

- Time-to-event (TTE) data is unique because the outcome of interest is not only whether or not an event occurred, but also when that event occurred
- Traditional methods of logistic and linear regression are not suited to be able to include both the event and time aspects as the outcome in the model
    - Traditional regression methods also are not equipped to handle censoring, a special type of missing data that occurs in time-to-event analyses when subjects do not experience the event of interest during the follow-up time
    - In the presence of censoring, the true time to event is underestimated

# Questions of Interest

- The choice of analytical tool should be guided by the research question of interest. With TTE data, the research question can take several forms, which influences which survival function is the most relevant to the research question
- Three different types of research questions that may be of interest for TTE data include:
    1. What proportion of individuals will remain free of the event after a certain time?
    2. What proportion of individuals will have the event after a certain time?
    3. What is the risk of the event at a particular point in time, among those who have survived until that point?

# Components & Characteristics

- Each of the above questions corresponds with a different type of function used in survival analysis:
    1. **Survival Function**, $S(t)$: the probability that an individual will survive beyond time $t [Pr(T>t)]$
    2. **Probability Density Function**, $F(t)$, or the **Cumulative Incidence Function**, $R(t)$: the probability that that an individual will have a survival time less than or equal to $t [Pr(T≤t)]$
    3. **Hazard Function**, $h(t)$: the instantaneous potential of experiencing an event at time t, conditional on having survived to that time
    4. **Cumulative Hazard Function**, $H(t)$: the integral of the hazard function from time 0 to time $t$, which equals the area under the curve $h(t)$ between time 0 and time $t$

- If one of these functions is known, the other functions can be calculated using the following formulas:
    - $S(t) = 1 – F(t)$
        - The survival function and the probability density function sum to 1
    - $h(t)=f(t)/S(t)$
        - The instantaneous hazard equals the unconditional probability of experiencing the event at time $t$, scaled by the fraction alive at time $t$
    - $H(t) = -log[S(t)]$
        - The cumulative hazard function equals the negative log of the survival function
    - $S(t) = e –H(t)$
        - The survival function equals the exponentiated negative cumulative hazard function
- Notes:
    - Generally, an increase in $h(t)$, the instantaneous hazard, will lead to an increase in $H(t)$, the cumulative hazard, which translates into a decrease in $S(t)$, the survival function

## Survival Function

## Probability Density Function (PDF)

## Hazard Function

## Cumulative Hazard Function

# Assumptions

- **Censoring:** The main assumption in analyzing TTE data is that of non-informative censoring: individuals that are censored have the same probability of experiencing a subsequent event as individuals that remain in the study
    - Informative censoring is analogous to non-ignorable missing data, which will bias the analysis
        - There is no definitive way to test whether censoring is non-informative, though exploring patterns of censoring may indicate whether an assumption of non-informative censoring is reasonable. If informative censoring is suspected, sensitivity analyses, such as best-case and worst-case scenarios, can be used to try to quantify the effect that informative censoring has on the analysis
- Another assumption when analyzing TTE data is that there is sufficient follow-up time and number of events for adequate statistical power
- Additional Simplifying Assumptions:
    - No cohort effect on survival: for a cohort with a long recruitment period, assume that individuals that join early have the same survival probabilities as those than join late
    - Right censoring only in the data
    - Events are independent of each other

# Approaches

There are three main approaches to analyzing TTE data: **non-parametric**, **semi-parametric** and **parametric** approaches

## Non-Parametric Approaches

- Non-parametric approaches do not rely on assumptions about the shape or form of parameters in the underlying population
    - In survival analysis, non-parametric approaches are used to describe the data by estimating the survival function, $S(t)$, along with the median and quartiles of survival time
    - These descriptive statistics cannot be calculated directly from the data due to censoring, which underestimates the true survival time in censored subjects, leading to skewed estimates of the mean, median and other descriptives
        - Non-parametric approaches are often used as the first step in an analysis to generate unbiased descriptive statistics, and are often used in conjunction with semi-parametric or parametric approaches

### Models

- [Kaplan-Meier Estimator](<./Time%20To%20Event%20Models%20(TTE)/Kaplan-Meier Estimator.md>)
- [Life Table Estimator](<./Time%20To%20Event%20Models%20(TTE)/Life Table Estimator.md>)

# Notation

- $T$ - lifetime, time-to-event
    - Naturally: $T \ge 0$

- $F(t) = P(T \le t)$
    - CDF

- $S(t) = 1 - F(t) - P(T < t)$
    - Survival Function

- $f(t)$ - density of $T, f(t) = \dfrac{d F(t)}{dt} = -\dfrac{d S(t)}{dt}$

- $P(a \le T \le b) = F(b) - F(a) = S(a) - S(b)$

- $h(t) df = P(t \le T \le t + dt | T \ge t) = \dfrac{S(t)-S(t +dt)}{S(t)}$

- $h(t) = \lim_{dt \rightarrow 0} \left (\dfrac{S(t)-S(t+1)}{dt} \cdot \dfrac{1}{S(t)} \right) = -\dfrac{S(t)'}{S(t)} = -(\log S(t))'$
    - $h(t)$ is called the ***Hazard Function***

- $h(t) = -\dfrac{S(t)'}{S(t)} = \dfrac{f(t)}{S(t)}$

- $f(t) dt = P(t\le T \le t + dt)$

- $h(t) dt = P(t \le T \le t + dt|T \ge t)$

- **Cumulative Hazard Function**
    - $H(t) = \int_0^t h(u) du = - \int_0^t (\log S(u))' du = - \log S(t) + 0$
    - $S(t) = e^{-H(t)}$
    - $S(t)$ and $h(t)$ are the most popular summaries in TTE models

# Likelihood with Censored Observations

- $Y_i \sim f(y_i |\theta), \space i=1,...n$
    - $n$ observations and $k$ of them are observed
- $\delta_i = 0, \space i =1,...k, \space \delta_i = 1, i = k+1,...n$
- **Likelihood**

    $$
    L(\theta|y_1,...y_n) = \prod_{i=1}^n f(y_i|\theta)^{1-\delta_i} S(y_i|\theta)^{\delta_i}
    $$

    - This is the product of likelihood functions
    - $S(y_i|\theta) = P^\theta(Y_i > y_i)$
        - We did not observe, but we know that $Y_i > y_i$

# Key Terms & Concepts

### **Censoring**

- One of the challenges specific to survival analysis is that only some individuals will have experienced the event by the end of the study, and therefore survival times will be unknown for a subset of the study group
    - This phenomenon is called censoring and may arise in the following ways: the study participant has not yet experienced the relevant outcome, such as relapse or death, by the close of the study; the study participant is lost to follow-up during the study period; or, the study participant experiences a different event that makes further follow-up impossible
    - Such censored interval times underestimate the true but unknown time to event. For most analytic approaches, censoring is assumed to be random or non-informative
- There are ***three main types of censoring, right, left, and interval***
    - If the events occur beyond the end of the study, then the data is right-censored
    - Left-censored data occurs when the event is observed, but exact event time is unknown
    - Interval-censored data occurs when the event is observed, but participants come in and out of observation, so the exact event time is unknown
        - Most survival analytic methods are designed for right-censored observations, but methods for interval and left-censored data are available
- **Censoring Types**
    1. Censoring time fixed, number of observations are random
    2. Censoring time is random, number of observations are fixed
- In this case, the records of customers A and C are **censored**

    ![Untitled](./Time%20To%20Event%20Models%20(TTE)/Untitled.png)

- How do we work with censored data?
    - Censoring Indicator for observed and censored data

# Resources

- [https://www.publichealth.columbia.edu/research/population-health-methods/time-event-data-analysis](https://www.publichealth.columbia.edu/research/population-health-methods/time-event-data-analysis)
- [https://handbook-5-1.cochrane.org/chapter_9/9_2_6_effect_measures_for_time_to_event_survival_outcomes.htm](https://handbook-5-1.cochrane.org/chapter_9/9_2_6_effect_measures_for_time_to_event_survival_outcomes.htm)
- [https://www.page-meeting.org/pdf_assets/2573-time-to-event-tutorial.pdf](https://www.page-meeting.org/pdf_assets/2573-time-to-event-tutorial.pdf)
- [https://www.bookdown.org/rwnahhas/RMPH/survival.html](https://www.bookdown.org/rwnahhas/RMPH/survival.html)
- [https://archive.ph/qZ0py](https://archive.ph/qZ0py)