# Feature Selection (Wrapper Methods)

Learn about Feature Selection, which refers to the process of selecting the most appropriate features for making the model.

> We'll cover the following:
>
> - Wrapper Methods
>   - Forward Selection
>   - Backward Elimination
>   - Exhaustive Search
>   - Recursive Feature Elimination

## Wrapper Methods

In Wrapper Methods the problem of Feature Selection is reduced to a search problem.  
 A model is built using a set of features and its accuracy is recorded. Based on the accuracy, more features are added or removed, and the process is repeated.

We have the following methods in Wrapper Methods.

#### Forward Selection

Forward Selection is an iterative method.  
In this method, we start with one feature and we keep on adding until no improvement in the model is observed. The search is stopped after a pre-set criteria is met.  
 This is greedy approach because it always targets the features in a forward fashion, which gives a boost to the performance.  
 _(If the number of features are large, it can be computationally expensive.)_

#### Backward Elimination

This process is the opposite of the Forward Selection Method.  
 It starts initially with all the features and keeps on removing features until no improvement is observed.

#### Exhaustive Search

This Feature Selection Method tries all the possible combinations of features to select the best model.  
 This method is quite computationally expensive.  
 For example, if we have five features, we will be evaluating 2^5=32 models before finalizing a model with good accuracy.

#### Recursive Feature Elimination

Recursively Feature Elimination (RFE) involves the following steps:

1. We train the model on the initial set of features and the importance of each feature is calculated.
2. In the second iteration, a model is built again using the most important features and excluding the least important features.
3. These steps are repeated recursively until we are left with the most important features for the problem under consideration.

Scikit learn library provides function for Recursive Feature Elimination.
