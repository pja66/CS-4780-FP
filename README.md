# CS-4780-FP
Cornell CS 4780 (Final Project)

Group members: David Schmaier (dms482), Philip Ayoub (pja66)

# Overview:	

## Basic Solution:
  
* We standardized the 6 numeric features in the test and train data by subtracting the mean and dividing by the standard deviation of each feature. We standardized the features to use with the logistic regression classifier whereas standardization is not needed for random forests.
    
* We chose to use a random forest because among different democratic counties there is a lot diversity in demographics, so we didn't think that a linear classifier would perform well. It seemed that it would be easier to find an ensemble of different decision rules that identify rural democratic counties and urban democratic counties than to find a kernel that maps these two very different types of democratic counties to the same region. We chose to also try a logistic regression classifier to serve as a baseline to compare with our random forest because it has relatively few parameters.
    
* For both the forest and the logistic regression classifiers, we performed k-fold cross validation to tune hyperparameters for the two classifiers. We  chose to use k-fold validation so we could train on the entire training set and still do validation to find the optimal parameter values. For the random forest, we tuned the hyperparameter max_depth which specifies the maximum depth of all trees in the forest. For the logistic regression classifier, the built-in scikit function LogisticRegressionCV tunes the hyperparameter for the regularizer. For the logistic regression classifier, we didn't use any L1 penalty because we didn't think that any of features were redundant and we wanted to use all of features.
    
## Creative solution:
    
*  We created several new features: the change from 2012 to 2016 in the six given numeric features in the test data (median income, migration rate, birth rate, death rate, bachelor rate, and unemployment rate), the mean of these six features among each county's neighbors (using graph.csv data), each county's own six features divided by the mean of the six features among its neighbors, the mean voting population and democratic share of the vote among each county's neighbors that are in the training set (also using graph.csv data), binary features that represent the state that each county is located in, and binary features that represent the region that each county is located in. We also added the same 6 features from the 2012 data. We also tried using an Adaboost classifier, but the test performance was better with the random forest classifier. We thought that the change in the unemployment rate from 2012 to 2016 would be particularly inforative, because between 2012 and 2016, the unemployment rate went down non uniformly between urban and rural areas. We decided to add features that summarize the features of each county's neighbors because we thought that counties that are next to each other would be likely to vote in similar ways. We also created six features that are the quotient of county's own features and the mean of its neighbor's features to identify counties that are very different from their neighbors. We thought this could be useful for identifying cities and suburbs. We also created features that capture the geographical region and state of each county because obviously different states and regions generally have different political preferences.
