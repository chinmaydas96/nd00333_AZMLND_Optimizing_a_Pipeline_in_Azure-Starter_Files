# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary

* This is the link for the original [dataset](https://archive.ics.uci.edu/ml/datasets/bank+marketing).

* The data is related with direct marketing campaigns of a Portuguese banking institution. The marketing campaigns were based on phone calls. Often, more than one contact to the same client was required, in order to access if the product (bank term deposit) would be ('yes') or not ('no') subscribed.

* So this is a classification problem in which we need to predict if the customer is suscribed(1) or not(0) to the bank product. 

* So we performed both sklearn Logistic Regression model with hyperdrive hyperparameters optmization and AUTOML model.

* From which AutoML performs best with VotingEnsamble model with 0.9165 accuracy.




## Scikit-learn Pipeline

* The scikit-learn pipeline was done in train.py. In which we downloaded the dataset from the given link and then preprocessed it.

* Preprocessing steps includes converting categorical variable to numerical variable which is important step while feeding the data to the model.

* For few categorical variable we used label encoding like day, months, yes-no questions for other categorical variable like education we used one-hot encoding.

* Then we split the data to 75-25 % ratio for training and testing.

* Then we fit the Logistic model to fit the data and predict on the testset and log it's accuracy.

* This following notebook was called in the notenook with hyperdrive functionality to optimized the parameters for the model.


### Benefits of the parameter sampler used : 

* RandomParameter Sampling sometimes perform better than or equal to the Gridsearch sampling, Also RandomParameter Sampling takes very less time to complete the process than gridsearch sampling. 


### Benefits of the early stopping policy :

* This stops the model to fit further if the model is not improving anymore. This saves lot of time in order to save the processing time.

* A bandit policy is the early stopping policy that we used here, in which it compare every run and stop the runs if result are getting worst.


## AutoML

### Description of the model and hyperparameters generated by AutoML : 

* AutoML runs multiple models with different data normalisation techniques to get the best model.

* Here VotingEnsemble algorithm works best for us with giving highest accuracy amoung all.


## Pipeline comparison


* The AutoModel performed better with VotingEnsamble model (0.9165) while Hyperdrive optmisation gave 0.9151 accuracy with Logistic Regression model.

* The numerical features in AutoML is normalised in differen types in order to get the optimum one.

* The AutoModel perform many algorithms while the hyperdrive pipeline only execute one Algorithm.

## Future work

* As this is a imbalanced dataset we could try for F1-score metrics to use here in order for better model.

* We could try to derive more feature from the data.

* Impute missing value would definately increase the model accuracy.

* We can try with different model in hyperdrive to check the result.

* After finding the optimum value and parameter we can train the model with whole data and deploy it.