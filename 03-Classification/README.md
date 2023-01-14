### Churn Prediction Project
- In this project we will predict the customer who will churn out of a given telecom company 
- This is a __binary classification problem__. For $i^{th}$ sample it is defined as $g(x_i) \approx y_i$ where , $y_i \in \{0,1\}$  
- Another type of classification problem can be multi-class
- 0 means not churn, 1 means churn
- Steps we will follow:
	- Data Preparation
	- Set up the validation framework
	- EDA
	- Feature Importance
	- Mutual Information
	- Correlation
	- Logistic Regression
	- Model Interpretation

### Data Preparation
- Import the data
- Change all column names to lower case and replace spaces with strings
- change all object type values to lower case and change spaces to null
- total charges should be numeric so convert it to numeric using `pd.to_numeric`. set `errors='coerce'`
- Fill NaN totalcharges with 0 (not always the best option, but good for now)
- create a variable churn and store Churn as 1, and non-churn as 0

### Setting up the validation framework
- Split datasets using `sklearn.model_selection.train_test_split`
- Reset index
- Create y arrays and remove churn column from dataframes

### EDA
- Check for missing values
- Check distribution of target variables
- create a list of numerical and categorical variables
- Check unique values in all categorical variables

### Feature Importance - Churn rate and risk ratio
- Look at churn rate within different groups
- Risk ratio = group_churn_rate / global_churn_rate
- Risk ratio > 1, likely to churn
- Risk ratio < 1, not likely to churn

### Feature Importance - Mutual Information
- Mutual Information between two random variables is the measure of mutual dependence between the two variables
- For example: how much do we know about churn by knowing about the contract
- The higher mutual information is, the more we learn about the churn by knowing the variable (in our example: contract)
- `from sklearn.metrics import mutual_info_score`

### Correlation
- It is used to calculate dependency between two numerical variables
- _Pearson Correlation_ values range between -1 to 1
- Negative correlation denotes that growth in one variable leads to reduction in the other
- Positive correlation means increase in one variable leads to the increase in another
- Following is the interpretation of correlation results:
	- $|0| to |0.2| = low$ 
	- $|0.2| to |0.5| = moderate$
	- $|0.5| to |1.0| = high$
- __Correlation Coefficient__ tells us the strength of correlation

### One-hot encoding
- We use `sklearn.feature_extraction import DictVectorizer` 
- `DictVectorizer` returns sparse matrix by default, we can turn it off by passing `sparse=False`
- It lets continuous fields as it is

### Logistic Regression
- Linear models is fast to use, fast to train
- Logistic regression applies sigmoid function which limits the output to range (0, 1)
- Sigmoid function is defined as $\frac{1}{1 + \exp{-z}}$ 

### Training Logistic Regression with scikit-learn
- `from sklearn.linear_model` import LogisticRegression
- fit the model
- predict for hard predictions
- predict_proba for soft predictions

### Model Interpretation
- Look at bias and coefficients of individual features and effect on the output

### Using the model
- Convert user info to dict
- use the same vectorizer and model to predict