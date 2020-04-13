# LendingClub - Supervised Learning


### Summary
In this challenge, we used different Supervised Machine Learning Algorithms to predict if a loan is considered risky. In total, 4 methods were used: Random Oversampling, SMOTE oversampling, Cluster Centroids undersampling, and SMOTEEN combination sampling.

### Analysis
In this analysis, we are looking at a few different metrics to judge each prediction method:
- Accuracy: Difference between predicted values and actual values, commonly classified into a confusion matrix (True Positive / False Positive / False Negative / True Negative)
- Precision: The reliableness of a positive classification
- Sensitivity: (aka Recall) the measure of of correct identification

In this analysis, precision is not very useful as the difference in classification sizes causes the results to be skewed. The main metrics used are the accuracy and sensitivity stats of each loan type. In the tables below, the results of each method can be seen with their respective metrics. In the array in each section, the results are illustrated as follows:
  High-Risk [Predicted High/Actually High , Predicted Low / Actually High]
  Low-Risk  [Predicted High/Actually Low , Predicted Low / Actually Low]


#### Random
This method should not be used. In addition to roughly half of the risky loans being picked up, about 2/3 of the low-risk loans were identified.

|| T | F |
| --- |--- | --- | 
| T | 48 | 34 |
| F | 6233 | 10890 | 

| Risk | Pre | Rec |
| --- | --- | --- |
| high_risk | 0.01 | 0.59 | 
| low_risk | 1.00 | 0.64 |


#### SMOTE
Of the 3 Oversample/Undersample methods, this algorithm works best. However, it should still not be used. Slightly over half of the Risky loans were picked up and about 2/3 of the low-risk loans were flagged correctly.

|| T | F |
| --- |--- | --- | 
| T | 47 | 35 |
| F | 5560 | 11563 |


| Risk | Pre | Rec |
| --- | --- | --- |
| high_risk | 0.01 | 0.57 | 
| low_risk | 1.00 | 0.68 |


#### Cluster Centroids
This method should not be used. In addition to roughly half of the risky loans being picked up, less than half of the low-risk loans were accurately predicted. This makes the classification of each loan no-better than a coin flip (and functionally useless).

|| T | F |
| --- |--- | --- | 
| T | 45 | 37 |
| F | 9217 | 7906 |

| Risk | Pre | Rec |
| --- | --- | --- |
| high_risk | 0.00 | 0.55 | 
| low_risk | 1.00 | 0.46 |



#### Combination
This method may be valuable because it identified 3/4 of the high-risk loans correctly. Unfortunately, by labeling many loans as high-risk, it mistakenly labelled many low-risk loans as risky.

|| T | F |
| --- |--- | --- | 
| T | 61 | 21 |
| F | 7372 | 9751 |

| Risk | Pre | Rec |
| --- | --- | --- |
| high_risk | 0.01 | 0.74 | 
| low_risk | 1.00 | 0.57 |


### Recommendation
The recommendation on which algorithm to use depends on the factors each financial institution places importance on.

If the bank views the ability to flag as many high risk loans accurately without regard to the low-risk loans, then the Combination method should be used. The updside is that this method had a high Sensitivity and flagged 3/4 of the high-risk loans. Unfortunately, this sensitivity flagged many low-risk loans as risky, which in-turn would lead to lost work hours investigating false positives.

If the institution views the time value of its employees as important, and believe the time lost investigating false positives is more significant than letting high-risk loans go unidentified, hen the SMOTE method would be best overall. This method had a slightly higher than half chance of detecting high-risk loans while correctly detecting 2/3 of the low risk loans.

However, non of these methods should really be used. They do not predict/detect enough of the high risk loans to be much better than a coin flip, while still creating many false positives by flagging many of the low-risk loans as high risk. Financial institutions need a more accurate method to predict high-risk loans so they don't waste many man-hours on chasing false positives while not releasing extra liability into their financial securities.
