- We will see accuracy
- We will see different types of errors
- Precision and Recall
- ROC curves
- ROC-AUC curves
- Cross-validation

### Accuracy and Dummy model
- Accuracy is number of correct predictions divided by total data points
- `from sklearn.metrics import accuracy_score`
- If we predict all customers as non-churning, we will be right 73% of the time. This is the problem with accuracy, it doesn't tell you how good the model is.
- Accuracy as a score in cases with class imbalance can be misleading

### Confusion Table
- True Positive - actual is positive class and prediction is positive class
- True Negative - actual is negative and prediction is negative
- False positive - actual is negative and prediction is positive
- False negative - actual is positive and prediction is negative
- Confusion matrix is a table of these 4 values and True positive + True negative add up to accuracy

### Precision and Recall
- Precision tells us how many positive predictions turned out to be correct
- Precision = $\frac{TP}{TP + FP}$
- Recall tells us fraction of correctly identified positive examples
- Recall = $\frac{TP}{TP + FN}$

### ROC curves
- ROC stands for Receiver Operating Characterstics and this is used to describe the performance of a binary classification model.
- This was used originally in 2nd world war when radar wanted to detect the plane.
- It is based on two underlying metrics: FPR and TPR
- False Positive Rate (FPR) is the fraction of false positives amongst all negative examples.
- FPR = $\frac{FP}{TN + FP}$
- True positive Rate is the fraction of true positives amongst all positive examples
- TPR = $\frac{TP}{FN + TP}$
- We want to minimize the False Positive Rate and Maximize the True Positive Rate
- True positive rate is the same as recall
- For x-axis, we plot FPR, and y-axis we plot TPR
- If the model line goes below random baseline you have a mistake somewhere
- `from sklearn.metrics import roc_curve`

### ROC-AUC
- Area Under the ROC curve
- For Random model, AUC = 0.5
- For Ideal model, AUC = 1.0
- `from sklearn.metrics import auc`
- `from sklearn.metrics import roc_auc_score`
- AUC tells us the probability of having score of randomly selected positive example is greater than the score of randomly selected negative example

### Cross-Validation
- Cross-validation is the process of splitting datasets into K-folds and training the model on K-1 fold and evaluating it on the remaining fold.
- Hence, we train K models, and in the end we can calulate the mean and standard-deviation on the metric of each fold
- We create a function for train and predict
- `from sklearn.model_selection import KFold`
- Most of the time a single holdout dataset is fine but if the dataset is too small, cross-validation is useful.