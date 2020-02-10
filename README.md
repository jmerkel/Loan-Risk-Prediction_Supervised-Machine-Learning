# jmerkel_Module_17
LendingClub - Supervised Learning

### Summary
In this challenge, we used different Supervised Machine Learning Algorithms to predict of a loan is considered risky. In total, 4 methods were used: Random Oversampling, SMOTE oversampling, Cluster Centroids undersampling, and SMOTEEN combination sampling.

### Analysis
In this analysis, we are looking at a few different metrics to judge each prediction method:
- Accuracy: Difference between predicted values and actual values, commonly classified into a confusion matrix (True Positive / False Positive / False Negative / True Negative)
- Precision: The reliableness of a positive classification
- Sensitivity: (aka Recall) the measure of of correct identification

In this analysis, precision is not very useful as the difference in classification sizes causes the results to be skewed. The main metric being used is the accuracy and sensitivity of each loan type. In the tables below, the results of each method can be seen, where correct identifications can be seen the the top left and bottom right locations of the array, as well as the precision and sensitivity for the prediction of each loan type.


#### Random
This method should not be used. In addition to roughly half of the risky loans being picked up, about 2/3 of the low-risk loans were identified.
array([[   48,    34],
       [ 6233, 10890]])
                pre       rec
high_risk       0.01      0.59
low_risk        1.00      0.64


#### SMOTE
Of the 3 Oversample/Undersample methods, this algorithm works best. However, it should still not be used. Slightly over half of the Risky loans were picked up and about 2/3 of the low-risk loans were flagged correctly.
array([[   47,    35],
       [ 5560, 11563]])
                pre       rec
high_risk       0.01      0.57
low_risk        1.00      0.68


#### Cluster Centroids
This method should not be used. In addition to roughly half of the risky loans being picked up, less than half of the low-risk loans were accurately predicted. This makes the classification of each loan no-better than a coin flip (and functionally useless).

array([[  45,   37],
       [9217, 7906]])
               pre       rec
high_risk      0.00      0.55                 
low_risk       1.00      0.46


#### Combination
This method may be valuable because it identified 3/4 of the high-risk loans correctly. Unfortunately, by labeling many loans as high-risk, it mistakenly labelled many low-risk loans as risky.
array([[  61,   21],
       [7372, 9751]])
               pre       rec
high_risk      0.01      0.74
low_risk       1.00      0.57


### Recommendation
The recommendation on which algorithm to use depends on the factors each financial institution places importance on.

If the bank views the ability to flag as many high risk loans accurately without regard to the low-risk loans, then the Combination method should be used. The updside is that this method had a high Sensitivity and flagged 3/4 of the high-risk loans. Unfortunately, this sensitivity flagged many low-risk loans as risky, which in-turn would lead to lost work hours investigating false positives.

If the institution views the time value of its employees as important, and believe the time lost investigating false positives is more significant than letting high-risk loans go unidentified, then none of the methods should be used. If one of these methods should be used, then the SMOTE method would be best overall. None of these methods should be used because they are not precise enough. Either half of the risky loans are unflagged, or
