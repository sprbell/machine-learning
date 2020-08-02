# Supervised learning
## Searching for exotic particles in high-energy physics using classic supervised learning algorithms

In this question, you will explore the use of supervised classification algorithms to identify *[Higgs bosons](https://en.wikipedia.org/wiki/Higgs_boson)* from particle collisions, like the ones produced in the *[Large Hadron Collider](https://en.wikipedia.org/wiki/Large_Hadron_Collider)*. In particular, you will use the *[HIGGS dataset](http://archive.ics.uci.edu/ml/datasets/HIGGS)*.

About the data: “The data has been produced using Monte Carlo simulations. The first 21 features (columns 2-22) are kinematic properties measured by the particle detectors in the accelerator. The last seven features are functions of the first 21 features; these are high-level features derived by physicists to help discriminate between the two classes. There is an interest in using deep learning methods to obviate the need for physicists to manually develop such features. Benchmark results using Bayesian Decision Trees from a standard physics package and 5-layer neural networks are presented in the original paper. The last 500,000 examples are used as a test set.”
You will apply Random Forests and Gradient boosting over a subset of the dataset and over the full dataset. As performance measures use classification accuracy and *[area under the curve](https://en.wikipedia.org/wiki/Receiver_operating_characteristic%23Area_under_the_curve)*.

1. Use pipelines and cross-validation to find the best configuration of parameters for each model
   - 1. For finding the best configuration of parameters, use 5% of the data chosen randomly from the whole set
   - 2. Use a sensible grid for the parameters (for example, three options for each parameter) for each predictive model 
   - 3. Use the same splits of training and test data when comparing performances among the algorithms
   
2. Working with the larger dataset. Once you have found the best parameter configurations for each algorithm in the smaller subset of the data, use the full dataset to compare the performance of the two algorithms in the cluster
   - 1. Use the best parameters found for each model in the smaller dataset of the previous step, for the models used in this step
   - 2. Once again, use the same splits of training and test data when comparing performances between the algorithms

# Senior Data Analyst
## Senior Data Analyst at Intelligent Insurances Co.

You are hired as a Senior Data Analyst at Intelligent Insurances Co. The company wants to develop a predictive model that uses vehicle characteristics to accurately predict insurance claim payments. Such a model will allow the company to assess the potential risk that a vehicle represents.
The company puts you in charge of coming up with a solution for this problem and provides you with a historic dataset of previous insurance claims. **The claimed amount can be zero or greater than zero and it is given in US dollars**. A more detailed description of the problem and
the available historic dataset is *[here](https://www.kaggle.com/c/ClaimPredictionChallenge)*. The website contains several files. You only need to work with the .csv file in **train_set.zip**.

1. Preprocessing
   - 1. The dataset has several fields with missing data. Choose a method to deal with missing data (e.g. remove the rows with missing fields or use an imputation method)
   - 2. convert categorical values to a suitable representation
   - 3. the data is highly unbalanced: most of the records contain zero claims. When designing your predictive model, you need to account for this
  
2. Prediction using linear regression. You can see the problem as a regression problem where the variable to predict is continuous. Be careful about the preprocessing step above. The performance of the regression model will depend on the quality of your training data.
   - 1. Use linear regression in PySpark as the predictive model. Partition your data into training and test (percentages according to your choice) and report the mean absolute error and the mean squared error
  
3. Prediction using a combination of two models. You can build a prediction model based on two separate models in tandem (one after the other). Once again, be careful about the preprocessing step above. For this step, use the same training and test data that you used in 2.a
   - 1. The first model will be a binary classifier (of your choice) that will tell whether the claim was zero or different from zero. The performance of the classifier will depend on the quality of your training data
   - 2. For the second model, if the claim was different from zero, train a Gamma regressor (a GLM) to predict the value of the claim. Report the mean absolute error and the mean squared error




