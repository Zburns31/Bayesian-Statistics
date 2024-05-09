# Time To Event Models

- [Time To Event Models (TTE)](./Unit%208%20Missing%20Data%20&%20Time%20To%20Event%20Models/Time%20To%20Event%20Models%20(TTE).md)


# Missing Data

## Types of Missing Data:

- **Missing Completely At Random (MCAR)**
    - These are the missing data points that follow no discernable pattern. Often the choice for which value to impute is down to a flip of a coin. These values are most clearly identified when you cannot predict the missing value from the remaining know variables
        - The fact that it is missing is independent of the remaining variables
        - Missingness does not depend on observed or unobserved data
    - Also known as ***Ignorable Missingness***


- **Missing At Random (MAR)**
    - MAR does not assume that the other variables cannot predict the missing value
        - This type is perhaps more often the case when there are errors with recording the data correctly
        - For example, imagine a sensor that misses a particular minute’s measurement but captures that data the minute before and the minute following
            - The missing value can roughly be interpolated from the remaining values to a reasonable degree of accuracy
    - To determine if your data contains missing at random data, observe the conditional probabilities of different features
        - For example, if conditioning on another feature increases the likelihood of a particular value compared to a proportional distribution, this value is likely MAR
    - Missingness depends only on the observed data
    - Also known as ***Ignorable Missingness***

- **Missing Not At Random (MNAR):**
    - Missing not at random or nonignorable data is data where the mechanism for why the data is missing is known. Still, the values can not effectively be inferred or predicted
    - An example of this form of data is a demographic for a survey avoiding questions
        - For example, perhaps people in a certain age/income bracket refuse to answer how many vehicles or houses they own. The mechanism here may be apparent, but inferring the actual value of the missing data is difficult to predict accurately
        - This type of missing data is similar to the following missing data type, structurally missing data, however, with one large distinction
        - In structurally missing data, the mechanism is easy to analyze. In contrast, when data is truly missing, not at random, this data is hard to handle because the mechanism may not be obvious
    - Neither MCAR, nor MAR hold; missingness may depend on the data that is missing, say data magnitude
    - Also known as ***Non-Ignorable Missingness***


### Multiple Imputations

- Multiple Imputation (MI) is currently the most acclaimed approach for handling missing data. These approaches provide estimates that are unbiased (and are therefore generalizable) and recovers the population variance, which is critical to statistical inference
    - The main difference with the single imputation method is that instead of imputing a single value for a missing observation, several values (say 3 to 10) are imputed. **The average of that is treated as the final imputed value**
    - MI is not just one method but a term for numerous approaches that deal with multiple imputations of values
        - These multiple values are derived from an iterative process that uses both the:  1) observed data and 2) sample values generated during the iterations
        - Each set of imputed values is then used to replace missing values to create a complete dataset
            - So if we chose to impute 3 values, these values result in three complete datasets
            - Those multiple estimates are combined to obtain a single best estimate of the parameter of interest
                - For example, if our approach is that of a multiple regression model, three regression models are constructed, one for each complete dataset. The resulting models have their corresponding parameters and coefficient estimates and the mean of these estimates will be our final one
- The general procedure for Multiple Imputation is straightforward
    1. Impute the missing values with values randomly drawn from some distributions to generate ***m*** complete cases data sets
    2. Perform the same analysis on each of the *m* data sets
    3. Pool the results in some fashion
- Types of Imputation
    - **Mean, Median, Mode**
        - A simple guess of a missing value is the mean, median, or mode (most frequently appeared value) of that variable
    - **Regression Imputation**
        - Mean, median or mode imputation only look at the distribution of the values of the variable with missing entries. If we know there is a correlation between the missing value and other variables, we can often get better guesses by regressing the missing variable on other variables
    - **KNN Imputation**
        - Besides model-based imputation like regression imputation, neighbour-based imputation can also be used
            - **K-nearest neighbour (KNN) imputation** is an example of neighbour-based imputation. For a discrete variable, **KNN imputer** uses the most frequent value among the k nearest neighbours and, for a continuous variable, use the mean or mode
    - **Last Observation Carried Forward**

# Censored Data

- [https://www.pymc.io/projects/docs/en/v3.11.4/pymc-examples/examples/survival_analysis/censored_data.html](https://www.pymc.io/projects/docs/en/v3.11.4/pymc-examples/examples/survival_analysis/censored_data.html)
- [https://www.pymc.io/projects/examples/en/latest/generalized_linear_models/GLM-truncated-censored-regression.html](https://www.pymc.io/projects/examples/en/latest/generalized_linear_models/GLM-truncated-censored-regression.html)

# Key Terms & Concepts

- **Hyperpriors**
    - Setting priors on priors to allow for more degrees of freedom in our Bayesian models
    - A hyperprior is an assumption made about a parameter in a [prior probability](https://deepai.org/machine-learning-glossary-and-terms/prior-probability) assumption. This is commonly used when the goal is to create [conjugate priors](https://deepai.org/machine-learning-glossary-and-terms/conjugate-prior), but no specific group of parameters can be inferred from past experiments or subjective analysis

# Resources

### Missing Data

- [https://archive.ph/8PcFi#selection-847.0-847.329](https://archive.ph/8PcFi#selection-847.0-847.329)
- [https://bookdown.org/mike/data_analysis/imputation-missing-data.html](https://bookdown.org/mike/data_analysis/imputation-missing-data.html)
- [https://dept.stat.lsa.umich.edu/~jerrick/courses/stat701/notes/mi.html](https://dept.stat.lsa.umich.edu/~jerrick/courses/stat701/notes/mi.html)
- [https://stefvanbuuren.name/fimd/sec-whyandwhen.html](https://stefvanbuuren.name/fimd/sec-whyandwhen.html)
- [https://medium.com/@Cambridge_Spark/tutorial-introduction-to-missing-data-imputation-4912b51c34eb](https://medium.com/@Cambridge_Spark/tutorial-introduction-to-missing-data-imputation-4912b51c34eb)
- [https://archive.ph/HIlup#selection-1151.0-1175.379](https://archive.ph/HIlup#selection-1151.0-1175.379)