# Car Price Prediction Project
- __Problem Statement__: To help user select the best selling price for a car.
- Use CooperUnion car dataset from Kaggle https://www.kaggle.com/datasets/CooperUnion/cardataset
- The target column is MSRP (Manufacturer Suggested Retail Price)
- Project plan
	- EDA
	- Use Linear Regression
	- Understand Internals of Linear Regression
	- Evaluate Model with RMSE
	- Feature Engineering
	- Regularization
	- Using the model

### Data Preparation
- Import the data
- Look at few data points
- Remove inconsistencies
	- Change all column names to lower case and replace spaces with underscores
	- Do the same for column values of type strings

### Exploratory Data Analysis
- Look at few rows of each column value in the dataframe
- Look at top unique values and number of unique values in each column
- Look at the distribution of the taret column MSRP using a histogram
	- It results in a long tail
	- We deal with the long tail by applying log distribution because the long tail is not good for ML algos.
	- Models do well when target variable resembles normal distribution.
	*A long tail distribution is common in regression problems like prices where the distribution is skewed around cheaper prices and few values exist for higher prices*
- Look at missing data

### Setting up the validation data
- We split the data into three sets: Training, Validation, and Test in 60%, 20%, 20% ratio respectively
- We may have to shuffle the dataset if there is some order which prevents useful features being available in all three sets
- Reset the index after shuffle

### Linear Regression
- Linear Regression is used to predict a number (continuous output)
- The model takes the form: $g(X) \approx y$, where $g$ is the Linear regression model, $X$ is the feature matrix and $y$ is our target
- Simplified form is: $g(x_i^{(1)}, x_i^{(2)}, ..., x_i^{(j)}) \approx y_i$ 
- Linear Regression can be implemented as $w_0 + \sum_{j=1}^n w_j.x_i^{(j)} \approx y_i$

### Linear Regression Vector form
$w^T.X \approx y$

### Training a Linear Regression Model
- Linear regression takes the form: $Xw = y$
- Multiplying both sided by $X^{-1}$ we get: $$X^{-1}Xw = X^{-1}y 
\implies Iw = X^{-1}y \implies w = X^{-1} y$$
given $X^{-1}$ exists
- Since X is usually not a square matrix, inverse of $X$,  $X^{-1}$, doesn't usually exist
- We can calculate an approximate solution by multiplying by $X^T$ which gives _Gram Matrix_ $X^TX$ which is always square: $$ Xw = y \implies X^TXw = X^Ty \implies (X^TX)^{-1}X^TXw = (X^TX)^{-1}X^Ty \implies  Iw = (X^TX)^{-1}X^Ty \implies w = (X^TX)^{-1}X^Ty$$
- Refer to [[Elements of Statistical Learning]] for proof

### Baseline model
- Take all the numerical features
- Fill the na values with 0, indicating the model should ignore the features
- Train the linear regression on this data
- See the histograms or predictions vs actuals

### RMSE
- RMSE is used to calculate how far the predictions are from the actual values
- It is defined as: $$RMSE = \frac{1}{m}\sum_i^m\sqrt{(y_i - g(x_i))^2}$$
### Validating the model
- Calculare rmse on the validation set

### Simple feature engineering
- The feature year can be used to calculate age of the car.
- Validate the model using the new feature 'age'

### Categorical Variables
- One-hot encode categorical variables
- Adding all variables worsens the performance

### Regularisation 
- If $X$ has duplicate columns, $X^TX$ is a singular matrix and inverse $(X^TX)^{-1}$ doesn't exist
- If X has slight numerical difference is columns, $(X^TX)^{-1}$ results in large values
- This is solved by regularisation
- We add small numbers to diagonal of $X^TX$ which results in smaller inverse

### Tuning the model
- We will find the best value for r

### Using the model
- User input is usually in the form of a dict
- convert it into dataframe and use the same pipeline