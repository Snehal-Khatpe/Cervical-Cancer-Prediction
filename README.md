# Problem Statement:
Cervical cancer is the fourth most frequent cancer among women globally. Early detection through regular screening is crucial for successful treatment. Traditional Pap smear tests, while effective, can be subjective and have limitations in accuracy. Machine learning offers promising avenues to potentially improve the accuracy and efficiency of cervical cancer screening. This project aimed to develop an XGBoost model that could predict cervical cancer diagnosis based on patient data, potentially aiding in earlier detection and better healthcare outcomes.

# Data Acquisition and Exploration:

The cervical cancer dataset was obtained from kaggle. The dataset included various features potentially relevant for predicting cervical cancer, such as patient age, smoking history, number of sexual partners etc.

A key challenge during data exploration was handling missing values, particularly in some non-critical features. We employed mean imputation for numerical features and dropped features with excessively high missingness rates to ensure data quality and prevent model bias.

# Model Building with XGBoost:

XGBoost was chosen for its strengths in handling complex relationships between features, which might be present in cervical cancer prediction. It also excels at dealing with potentially imbalanced class distributions (cervical cancer being less frequent than healthy cases) often encountered in medical datasets. We tuned essential hyperparameters like learning rate, max depth, and the number of estimators to optimize the model's performance. 

# Training and Testing Accuracy:

result_train = 0.947 and result_test = 0.944: These accuracy scores indicate that the model performs well on both the training data (almost 95%) and the testing data (slightly lower at around 94%). This suggests that the model has learned the patterns in the training data and generalizes reasonably well to unseen data in the testing set.

# Classification Report:

Precision: For positive predictions (cancer), how often was the prediction correct? (0.95 for cancer class)
Recall: For actual cancer cases, how often did the model correctly predict cancer? (1.0 for cancer class, ideal but potentially inflated due to class imbalance)
F1-Score: Harmonic mean of precision and recall, balancing both metrics. (1.0 for cancer class, again potentially high due to imbalance)
Support: Number of data points in each class (399 negative, 23 positive)

# Key Observations:

The model excels at identifying negative cases (no cancer) with a precision of 0.95 and a recall of 1.0. 
This means that for most negative predictions, the model was correct.
However, the model struggles with identifying positive cases (cancer) with a precision of 0.86 and a recall of 0.21.
This indicates that while the model captures many negative cases accurately, it misses a significant portion of actual cancer cases (low recall). 
This could be due to the imbalanced nature of the dataset (potentially fewer cancer cases).

# Confusion Matrix
True Negative (TN): 399 - These are the cases where the model correctly predicted no cancer, and there was indeed no cancer present.
False Negative (FN): 23 - These are the concerning cases where the model incorrectly predicted no cancer, but cancer was actually present (missed diagnoses).
True Positive (TP): 6 - These are the ideal cases where the model correctly predicted cancer, and cancer was indeed present.
False Positive (FP): 23 - These are the incorrect predictions where the model predicted cancer, but there was actually no cancer present (false alarms).
