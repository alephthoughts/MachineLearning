# 1. 1 Introduction to Machine Learning

- Machine learning is the process of extracting patterns from data.
- The data is in the form of features, and we train a model that learns patterns from the data just like an expert would.
- For example, in a car market place, a car expert can suggest a price of your car based on information you provide suce as brand, age and mileage.
- If an expert can do this, so can a model.
- We train a model by providing input `features` and corresponding `target` prices. The model learns patterns from the input.
- We can then use the trained model on new data (unknown prices) for which we know the `features` to predict the `target` prices

# 1.2 ML Vs Rule based Systems
- A rule based system has rules embedded as code.
- Over time a rule based system can become complex and difficult to maintain as the variation of scenarios increases.
- In such situations, ML based systems prove to be better.
- For ML based systems, examples are required which can be available by recording actions of users of a given system. If that doesn't exist, starting with a rule based system can generate such examples.
- This can be illustrated by an example of spam filter. You can start by coding rules such as list of senders, domains or words in subject or body of the email to classify it as spam or not spam. An existing email program can record user action of marking emails as spam to generate examples of spam and not spam emails. An ML based system can learn from these examples.

# 1.3 Supervised Machine Learning
- The essence of supervised learning is that the model is trained on examples of the task to be performed. The car price prediction and spam filter are examples of supervised learning.
- Mathematically, supervised learning can be experssed as: $$g(X) \approx y$$
where, $X$ is the feature matrix, $y$ is the target vector and $g$ is the learnt model.
- Supervised learning is of three types:
	1. __Regression:__ In regression tasks, the target value to be predicted is continuous numerical value between $- \infty$ to $\infty$. Example: House price prediction
	2. __Classification:__ In classification tasks, the target is assigning inputs to a categorical discrete value. Example: classifying pictures of cats and dogs. Classification may be of two types:
		1. _Multiclass_: More than two target categories
		2. Binary: Two target categories
	3. __Ranking:__ In ranking tasks, items in the dataset are assigned a number between 0 to 1 and top items are organized in order. Example: recommender systems and search results.

# 1.4 CRISP-DM ML Process
- CRoss Industry Standard Process for Data Mining was developed by IBM in the early 90s. The process steps are:

![CRISP-DM](images/"Pasted image 20220907205647.png")
	1. __Business Understanding:__ 
		- Understand the business problem and assess how to solve it.
		- Important question to ask here is - do we need ML?
		- Define a business goal
		- The business goal should be measurable
	2. __Data Understanding__:
		- Identify the data sources and assess if we need to collect more data
		- Is the data reliable?
		- How do we track it?
		- Is the data enough?
		- Do we need to collect more data?
		- We may need to update our business understanding and goals based on the data
	3. __Data Preparation__:
		- Transform the data in a form that is consumable by the model.
		- Create validation set to test generalization performance of the model
	4. __Modelling__:
		- Train ML models, and choose the best one
		- There are many models to try such as tree based, logistic regression, neural networks and others
		- We may find data issues and we need to fix them
	5. __Evaluation + Deployment__:
		- Evaluate the model online on subset of few users
		- If the business goals are met and the results are reliable, deploy the morel to production
	6. __Iterate:__ 
		- ML is an interative process
		- The whole pipeline is iterated upon many times for most applications

# 1.5 Model Selection
- Split the data into train and validation set such that train data consists larger part of the dataset. This is because we want to mimic the real scenario where model has to perform well on unseen data
- _Multiple Comparisons Problem_ can occur when you test multiple models on the same validation set and one of the model may perform well just out to sheer luck
- To counter Multiple comparisons problem, we update our strategy to split the dataset to train, validation and test sets.
- We train multiple models on the training dataset.
- We evaluate models on the validation dataset and select the best performing model
- We then choose the best model and evaluate it on the test dataset to ensure that the model is not lucky on validation set
- Optionally, once we are satisfied we can train the model on train and validation set combined and evaluate it on test set for slightly better performance.