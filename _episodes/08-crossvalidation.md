---
title: "Cross Validation"
teaching: 30
exercises: 10
questions:
- What is cross validation?- 
objectives:
- "Gain an overview of what cross validation is good for"
- "Understand overfitting and underfitting"
- "Understand use and abuse of cross validation"
- "Understand limitations and assumptions behind cross validation"
- "Understand relationship between cross validation and model optimization"
keypoints:
- 
---

# Validation and Verification

Engineering terminology: 

- verification: making sure the model complies with specifications (spec sheet)
- validation: making sure the model is fit for purpose = meets the application needs

In the context of machine learning (and this lecture), we almost always talk about *verification*.

## Ingredients

- figures of merit: numbers that measure the properties we're interested in  
    + MSE, RMSE, relative RMSE, MAE, R², accuracy, error rate, specificity, sensitivity, predictive values, precision, recall, Brier's score, AuROC...  
  + *predictive ability*: how well does the model predict (new data from the same population/distribution)
  + *stability*: how stable is the model training process against changes (perturbations), e.g. a slightly different training data set
  + *ruggedness*: how stable are the predictions to changing e.g. environmental conditions
- data plan: 
  + How to get samples (cases) for testing? autoprediction/residuals, resampling (e.g. cross validation), test set, validation study
  + Which?
  + How many?


### Figures of merit: Regression

- MAE: mean absolute error
- MSE: mean squared error
- RMSE: root mean squared error
- R2: coefficient of determination = fraction of y-variance captured by the predictions

### Figures of merit: Classification

- Proportions: fractions of tested cases
    + accuracy: fraction of correctly classified test cases 
    + 

- fractions have high variance 


### Bias (accuracy) and variance (precision)






## Resampling

Resampling *simulates* obtaining new unknown cases. 



- The quality of resampling verification depends crucially on how good this simulation is!
- Crucial: cases must be really unknown aka *independent*
  this is really difficult in practice!
- Knowing what factors threaten independence requires domain knowledge
- Data leak = violating independence => optimistic bias



- e.g. hold out: single split of available data
- 

## Independence

When you train on some cases from such a cluster/group, the model may learn the group. (This is a particular type of overfitting, see below). When testing with other examples from the known group, the model may perform much better than for unknown examples of an unknown cluster/group, causing the test results to be systematically too optimistic, i.e. an optimistic bias.

- cases (rows) in test independent of cases (rows) in training
    + independent: there is no (known or unknown) factor that makes some data rows more similar to each other than others - except the dependent $y$ we're trying to predict.
    + clustered (grouped, hierarchical data) e.g. repeated measurements must all be either in trainig xor in test  
        stats terminology: *nested* structure. 1 : n relationship  

    + possible temporal: predict future from past, but not the other way round  
      even for data that are not time series, there may be detector drift => break by randomized measurement order if possible
    + possible spatial relation: suitable "safety margin" between training and test cases
- reference $y$ independent of case-data $X$: e.g. no labeling via cluster analysis
- careful: self-fulfilling prophecies due to reference labeling procedure  
- pre-processing can break independence => splitting must be done *before* first pre-processing step that involves multiple cases.
- Model optimization/hyperparameter tuning can break independence => use verification data that is independent of the tuning process.

## Stratification




# Cross validation


# Model complexity: Underfitting and Overfitting

*polynomial regression as example*
*SVM? as classification example*

Caution: humans are likely hard-wired to overfit!

# Using cross validation for model optimization aka hyperparameter tuning

## What are hyperparameters?

- hyperparameters steer the overall behaviour of the training algorithm.
- From the application task point of view: hyperparameters are like parameters: numbers that need to be fixed somehow to obtain a *final* useable model.
- hyperparameters are model parameters for which the training algorithm developers did not (could not) specify how to estimate/fix them.  
 Typically because they vary too much between data sets/applications.

Excercise: What are some hyperparameters for models you've encountered already?
 - polynomial order
 - pre-processing steps (which, order)
 - dimensionality reduction: target complexity e.g. number of PCs
 - k-NN: number of neighbours (k), variants e.g. maximum distance
 - random forest: fraction of variables, number of trees
 - SVM: kernel & kernel-specific parameters e.g. cost + gamma


## Some History

1. For very low-complexity models (e.g. univariate linear $y = ax + b$ with scalar x and y), we can easily get n >> p.  
Overfitting is not a problem, it is thus sufficient to look at residuals aka training error.   
2. Models got more complex. People realized that there are problems with overfitting *which is not detected by training error*  
  In consequence, models need to be validated 
3. 



