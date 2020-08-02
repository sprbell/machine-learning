# Regularisation for Linear Regression

Regularisation is a technique commonly used in Machine Learning to prevent overfitting. It consists on adding terms to the objective function such that the optimisation procedure avoids solutions that just learn the training data. Popular techniques for regularisation in Supervised Learning include Lasso Regression, Ridge Regression and the Elastic Net. 

In this Assignment, you will be looking at Ridge Regression and devising equations to optimise the objective function in Ridge Regression using two methods: a closed-form derivation and the update rules for stochastic gradient descent. You will then use those update rules for making predictions on a Air Quaility dataset.

## Using ridge regression to predict air quality
Our dataset comes from a popular machine learning repository that hosts open source datasets for educational and research purposes, the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/index.php). We are going to use ridge regression for predicting air quality. The description of the dataset can be found [here](https://archive.ics.uci.edu/ml/datasets/Air+Quality).

### Splitting the dataset
Split the dataset into a training set and a test set. The training set should have 70% of the total observations and the test set, the 30%. For making the random selection make sure that you use a random seed that corresponds to the last five digits of your student UCard. Make sure that you comment your code.

## Preprocessing the data
The dataset has missing values tagged with a -200 value. Before doing any work with the training data, we want to make sure that we deal properly with the missing values. 

### Missing values

Make some exploratory analysis on the number of missing values per column in the training data. 

* Remove the rows for which the target feature has missing values. We are doing supervised learning so we need all our data observations to have known target values.

* Remove features with more than 20% of missing values. For all the other features with missing values, use the mean value of the non-missing values for imputation.

### Normalising the training data

Now that you have removed the missing data, we need to normalise the input vectors. 

* Explain in a sentence why do you need to normalise the input features for this dataset.

* Normalise the training data by substracting the mean value for each feature and dividing the result by the standard deviation of each feature. Keep the mean values and standard deviations, you will need them at test time.

## Training and validation stages

We have now curated our training data by removing data observations and features with a large amount of missing values. We have also normalised the feature vectors. We are now in a good position to work on developing the prediction model and validating it. We will use both the closed form expression for **w** and gradient descent for iterative optimisation. 

We first organise the dataframe into the vector of targets **y** and the design matrix **X**.

### training with closed form expression for **w**
To find the optimal value of **w** using the closed form expression that you derived before, we need to know the value of the regularisation parameter **a** in advance. We will determine the value by using part of the training data for finding the parameters **w** and another part of the training data to choose the best **a** from a set of predefined values.

* Use `np.log(start, stop, num)` to create a set of values for **a** in log scale. Use the following parameters `start=-3`, `stop=2` and `num=20`. 

* Randomly split the training data into what is properly called the training set and the validation set. As before, make sure that you use a random seed that corresponds to the last five digits of your student UCard. Use 70% of the data for the training set and 30% of the data for the validation set.

* For each value that you have for **a** from the previous step, use the training set to compute **w** and then measure the mean-squared error (MSE) over the validation data. After this, you will have `num=20` MSE values. Choose the value of **a** that leads to the lower MSE and save it. You will use it at the test stage.

### validation with the closed form expression for **w**

We are going to deal now with the test data to perform the validation of the model. Remember that the test data might also contain missing values in the target variable and in the input features.

* Remove the rows of the test data for which the labels have missing values. 
* If you remove any feature at the training stage, you also need to remove the same features from the test stage.
* Replace the missing values on each feature variables with the mean value you computed in the training data.
* Normalise the test data using the means and standard deviations computed from the training data
* Compute again **w** for the value of **a** that best performed on the validation set using ALL the training data (not all the training set).
* Report the MSE on the preprocessed test data and an histogram with the absolute error.

### training with gradient descent and validation
Use gradient descent to iteratively compute the value of **w_new**. Instead of using all the training set to compute the gradient, use a subset of **B** datapoints in the training set. This is sometimes called minibatch gradient descent where **B** is the size of the minibacth. When using gradient descent with minibatches, you need to find the best values for three parameters: **n**, the learning rate, **B**, the number of datapoints in the minibatch and **a**, the regularisation parameter.

* As you did on Question 6, create a grid of values for the parameters **a** and **n** using `np.logspace` and a grid of values for **B** using np.linspace. Because you need to find 
 three parameters, start with `num=5` and see if you can increase it.

* Use the same training set and validation set

* For each value that you have of **a**, **n** and **B** from the previous step, use the training set to compute **w** using minibatch gradient descent and then measure the MSE over the validation data. For the minibatch gradient descent choose to stop the iterative procedure after **500** iterations.

* Choose the values of **a**, **n** and **B** that lead to the lower MSE and save them. You will use them at the test stage.

* Use the test set from Question 7 and provide the MSE obtained by having used minibatch training with the best values for **a**, **n** and **B** over the WHOLE training data (not only the training set).

