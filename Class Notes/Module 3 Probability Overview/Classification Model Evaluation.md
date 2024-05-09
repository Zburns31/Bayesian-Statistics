# Confusion Matrix

- The confusion matrix provides more insight into not only the performance of a predictive model but also which classes are being predicted correctly, which incorrectly, and what type of errors are being made
- If binary classification, the confusion matrix will be 2x2 (Predicted Vs. Actual for each class), else, it will be 4 x 4
- Positive Prediction
    - (Minority Class): Call/Default/Tested Positive/etc. (Label Index: 1)
- Negative Prediction
    - (Majority Class): No Call/No Default/Tested Negative/etc. (Label Index: 0)


|  | Disease (D) | No Disease (C) | Total |
| --- | --- | --- | --- |
| Test Positive | TP | FP | nP = TP + FP |
| Test Negative | FN | TN | nN = FN + TN |
| Total | nD = TP + FN | nC = FP + TN | n = nD + nC = nP + nN |

Where:

- TP: True Positives (Test Positive, Disease present)
- FP: True Positives (Test Positive, Disease absent)
- FN: True Positives (Test Negative, Disease present)
- TN: True Positives (Test Negative, Disease absent)
- nP: Total number of positives
- nN: Total number of negatives
- nD: Total number with disease present
- nC: Total Number without disease present
- n: Total sample size (TP + FP + FN + TN)

## Statistic Summary Table

| Sensitivity | Se = TP / (TP + FN) = TP /nD |
| --- | --- |
| Specificity | Sp = TN / (FP + TN) = TN / nC |
| Prevalence | Pre = (TP + FN) / (TP + FP + FN + TN) = nD / n |
| Positive Predictive Value (PPV) |  PPV = TP / (TP + FP) = TP / nP |
| Negative Predictive Value (NPV) | NPV = TN / (TN + FN) = TN / nN |
| Likelihood Ratio Positive (LRP) | LRP = Se / (1-Sp) |
| Likelihood Ratio Negative (LRN) | LRN = (1-Se) / Sp |
| Apparent Prevalence (APre) | APre = nP/n |
| Accuracy (Ac) | Ac = (TP + TN) / n |

### Other Formulas:

- $TNR \space (Specificity) \space = \dfrac {TN} {TN + FP}$

- $PPV \space = \dfrac {Se * Pre} {Se * Pre + (1-Sp) * (1 - Pre)}$

- $NPV \space = \dfrac {Sp * (1-Pre)} {Sp * (1-Pre) + (1-Se) * Pre}$

# Metrics:

**Accuracy: Correct Predictions / Total Predictions**

- It works well only if there are equal number of samples belonging to each class

**Precision or Weighted Precision (for Multi-Class Classification): True Positive / (True Positive + False Positive)**

- Precision is the ratio of the **correctly** labeled positive instances by our model compared to all instances labeled the as positive. For example, how many predictions that were identified to be a “Call” were actually a call? So basically, the less false positives a classifier gives, the higher is its precision
- **Focus on this if the cost of FP's is high**
- Also known as Positive Predictive Value

**Recall (Sensitivity or TPR) or Weighted Recall (for Multi-Class Classification): True Positive / (True Positive + False Negative)**

- Recall summarizes how well the positive class was predicted. For example, of all the instances of a “Call”, how well did you predict those? Recall focuses on all relevant instances
- **Focus on this if the cost of FN's is high**

**Specificity / True Negative Rate: True Negative / (TN + FP)**

- Specificity is of all the instances in the negative class, how many negative labels were assigned?

**False Positive Rate:** The False Positive Rate answers the question, "When the actual classification is negative (meaning not admitted), how often does the classifier incorrectly predict positive?

**F-Score & F-Beta Score:** So the higher precision and recall are, the better the classifier performs because it detects most of the positive samples (high recall) and does not detect many samples that should not be detected (high precision). In order to quantify that, we can use another metric called F1 score

- **F-Score**

    $F-Score = 2 * \dfrac {precision * recall} {precision + recall}$

- A weighted balance between precision and recall can be combined into a single score that seeks to balance both concerns, called the F-score or the F-measure
    - There is also a beta coefficient if you want to favour precision or recall. Generally:
    - To give more weight to the Precision, we pick a Beta value in the interval 0 < Beta < 1
    - To give more weight to the Recall, we pick a Beta Value in the interval 1 < Beta < + ∞
- **F-Beta Score**

$F-Score = (1 + \beta^2) * \dfrac {precision * recall} {\beta^2 + precision + recall}$

- **When to use F-Beta?**
    - When you want to adjust whether you weight Recall or Precision higher:
        - When > 1: we weight **recall higher**
        - When < 1: we weight **recall lower**
        - When > =1: we weight **recall and precision**
- **Note:** F-Beta == F2 score when Beta == 2

- Note:
    - Type I Error == False Positive
    - Type II Error = False Negative

### When to Favour Recall Vs. Precision?

- Favour Recall when a FN outcome is more disastrous than a FP
- Favour Precision when a FP outcome is more disastrous than a FN
- **What is more costly to the business?**
- Notes:
    - Typically, we use both as any single metric alone can be misleading

# Thresholding

Distribution of Predicted Probabilities for each class

![Classification%20Model%20Evaluation%20b9c7710e94044a50a54e943fa8d8b30e/Untitled.png](./Classification%20Model%20Evaluation/Untitled.png)

## How To Choose The Optimal Threshold?

There a few different approaches for choosing the optimal threshold point

1. **G-Mean:**
    1. The geometric mean or known as G-mean is the geometric mean of sensitivity (known as recall) and specificity. So, it will be one of the unbiased evaluation metrics for imbalanced classification
2. **Youden’s J Statistic**
    1. Faster way to get the G-Mean
        1. Formula: J = Sensitivity + Specificity – 1
            1. Or: J = TruePositiveRate – FalsePositiveRate
3. **Precision-Recall Curve**
4. **Threshold Tuning**

### References:

- [https://towardsdatascience.com/optimal-threshold-for-imbalanced-classification-5884e870c293](https://towardsdatascience.com/optimal-threshold-for-imbalanced-classification-5884e870c293)
- [https://machinelearningmastery.com/threshold-moving-for-imbalanced-classification/](https://machinelearningmastery.com/threshold-moving-for-imbalanced-classification/)

## Macro Vs. Weighted Average

### Macro Average:

- The macro-averaged scores are computed by taking the arithmetic mean (aka **unweighted** mean) of all the per-class scores

    ![Untitled](./Classification%20Model%20Evaluation/Untitled%201.png)


### Weighted Average

- The **weighted-averaged** score is calculated by taking the mean of all per-class scores **while considering each class’s support**

    ![Untitled](./Classification%20Model%20Evaluation/Untitled%202.png)


### Micro Average

- Micro averaging computes a **global average** score by counting the **sums** of the True Positives (**TP**), False Negatives (**FN**), and False Positives (**FP**)
    - Why is there no Micro score shown?
        - **Only used when there are 3+ labels**
        - The reason is that micro-averaging essentially computes the **proportion** of **correctly classified** observations out of all observations. If we think about this, this definition is in fact what we use to calculate overall **accuracy**
            - Micro average (averaging the total true positives, false negatives and false positives) is only shown for multi-label or multi-class with a subset of classes, because it corresponds to accuracy otherwise and would be the same for all metrics
                - In **micro-averaging**, we collect the decisions for all classes into a single confusion matrix, and then compute precision and recall from that table

    ![Untitled](./Classification%20Model%20Evaluation/Untitled%203.png)


## Pros & Cons:

- A micro-average is dominated by the more frequent class (in this case spam), since the counts are pooled. The macro-average better reflects the statistics of the smaller classes, and so is more appropriate when performance on all the classes is equally important

### References:

- [https://towardsdatascience.com/micro-macro-weighted-averages-of-f1-score-clearly-explained-b603420b292f](https://towardsdatascience.com/micro-macro-weighted-averages-of-f1-score-clearly-explained-b603420b292f)
- [https://stackoverflow.com/questions/55740220/macro-vs-micro-vs-weighted-vs-samples-f1-score](https://stackoverflow.com/questions/55740220/macro-vs-micro-vs-weighted-vs-samples-f1-score)
- [https://datascience.stackexchange.com/questions/15989/micro-average-vs-macro-average-performance-in-a-multiclass-classification-settin](https://datascience.stackexchange.com/questions/15989/micro-average-vs-macro-average-performance-in-a-multiclass-classification-settin)
- [https://hbunyamin.github.io/ml-2/Micro_and_Weighted_Macro_Averages/](https://hbunyamin.github.io/ml-2/Micro_and_Weighted_Macro_Averages/)
- [https://www.mariakhalusova.com/posts/2019-04-17-ml-model-evaluation-metrics-p2/](https://www.mariakhalusova.com/posts/2019-04-17-ml-model-evaluation-metrics-p2/)

# ROC - AUC

**Receiver Operating Characteristics (ROC):** The ROC Curve is a graph showing the performance of a classification model at all classification thresholds. This curve plots two parameters:

- **How it works:**
    - True Positive Rate (Y-axis)
    - False Positive Rate (X-axis) Lowering the classification threshold classifies more items as positive, thus increasing both False Positives and True Positives
- Can be misleading when datasets are imbalanced to its focus on specificity ( True Negative Rate), which we don’t care about when the data is imbalanced since the minority class is often the positive class

- **Classification threshold:** What level of probability do you assign an instance/observation to a particular class?
    - It allows you to choose which type of errors you would prefer to make or not make
        - **Increasing the threshold will make your classifier "stricter" making less False Positive errors, Less TP's, but more False Negative errors**
            - We will classify more instances as negative

- **Decreasing the threshold will make your classifier "less strict" making more False Positive Errors, More True Positives and less False Negative Errors**
    - **Slope of the ROC curve reflects how many true positives you gain for each false positive you accept**
    - We will classify more instances as positive
        - Increasing TP's but more FP's

- **Interpretation:**
    - ROC is a probability curve and AUC represents the degree or measure of separability
        - It tells how well the model is capable of distinguishing between classes
        - Higher the AUC, the better the model is at predicting 0 classes as 0 and 1 classes as 1
        - **When AUC is 0.7, it means there is a 70% chance that the model will be able to distinguish between positive class and negative class**


**Area Under the Curve (AUC)**: AUC provides an aggregate measure of performance across all possible classification thresholds

- **The AUC of a classifier is equal to the probability that the classifier will rank a randomly chosen positive example higher than a randomly chosen negative example**
- **It tells us how much the model is capable of distinguishing between classes**
    - Higher the AUC, better the model is at predicting the probability of class YES higher than the probability of class NO
    - AUC ROC indicates how well the probabilities from the positive classes are separated from the negative classes
- One way of interpreting AUC is as the probability that the model ranks a random positive example more highly than a random negative example
- AUC ranges in value from 0 to 1
    - A model whose predictions are 100% wrong has an AUC of 0.0
    - one whose predictions are 100% correct has an AUC of 1.0
- **AUC is desirable for two reasons:**
    - **AUC is scale invariant:** It measures how well predictions are ranked, rather than their absolute values
    - **AUC is classification-threshold-invariant**: It measures the quality of the model's predictions irrespective of what classification threshold is chosen

## Precision-Recall Curve

**A precision-recall curve is a plot of the precision (y-axis) and the recall (x-axis) for different thresholds, much like the ROC curve**

- **Works well when data is imbalanced and we are interested in the minority class**
    - Should be used when specificity is of no concern for the classifier
- Typically, Precision and Recall are inversely related, ie. as Precision increases, recall falls and vice-versa. A balance between these two needs to be achieved, and to achieve this and to compare performance, the precision-recall curves come in handy
- **How it works:**
    - X-axis: Recall
    - Y-axis: Precision
- **Interpretability:**
    - The curve shows the trade-off between Precision and Recall across different thresholds. You can also think of this curve as showing the trade-off between the false positives and false negatives
- **Resources:**
    - [https://levelup.gitconnected.com/precision-recall-curve-explained-fabfe58fb52e](https://levelup.gitconnected.com/precision-recall-curve-explained-fabfe58fb52e)

## Support

- The support is the number of occurrences of each class in y_true

## Other Notes:

- Although widely used, classification accuracy is almost universally inappropriate for imbalanced classification. The reason is, a high accuracy (or low error) is achievable by a no skill model that only predicts the majority class. If the dataset is balanced, accuracy can be useful
- Great article on Precision, Recall and F1 Score: [https://simonhessner.de/why-are-precision-recall-and-f1-score-equal-when-using-micro-averaging-in-a-multi-class-problem/](https://simonhessner.de/why-are-precision-recall-and-f1-score-equal-when-using-micro-averaging-in-a-multi-class-problem/)
- **Note: Be careful when using Precision and Recall when dealing with imbalance classes**

# Resources

- Engineering Stats Book, Chapter 4 (Bayesian Stats)