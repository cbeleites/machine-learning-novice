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
- validation: making sure the model is fit for purpose

## Ingredients

- figures of merit: numbers that measure the properties we're interested in
    + 
- data plan: how to get samples (cases) for testing
    + 

## Independent test set

### What is good test data?

- related: self-fulfilling prophecies via consensus labelling


## Stratification

## Grouped aka hierarchical aka clustered data

- groups of data (rows) that are more similiar to each other
- example: repeated measurements

When you train on some cases from such a cluster/group, the model may learn the group. (This is a particular type of overfitting, see below). When testing with other examples from the known group, the model may perform much better than for unknown examples of an unknown cluster/group.

example


# Cross validation

## What does *independent split* mean?

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



