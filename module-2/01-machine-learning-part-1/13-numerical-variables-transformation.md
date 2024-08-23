# Numerical Variables Transformation

Numerical Variables Transformation refers to applying operations on the Numerical Columns to have better performance of Machine Learning models.

> We'll cover the following
>
> - Numerical Variables Transformation

## Numerical Variable Transformation

In the lesson of Probablity Distributions, while discussing Gaussian Distributions, we discussed that algorithms in Machine Learning like Linear Regressoim or Logistic Regression assume the Features' underlying distribution to be Gaussian.  
 If not, the model might perform badly. If the distribution is not Gaussian, we can apply Transformations to make it Gaussian.

Machine Learning models that assume the underlying distribution of the variables to be Gaussian are:

- Linear Regression
- Logisitic Regression
- Linear Discriminant Analysis
- Naive Bayes

We can apply following transformations on the dataset's individual features after analyzing them.  
 **Transformations can help us to achieve good results by making the underlying features more Gaussian-like.**

- **Logarithm Transformation:**  
   This transformation is used on the features that have positive values. This logarithm is the Natural Logorithm.
- **Reciprocal Transformation (1/x where x is one of the values of the feature)**  
   This transformation can be applied to negative values and is not applied to the value 0.
- **Square Root or Cube Root Transformation:**  
   This transformation comes under the category of Power Transformations and it involves taking the power x^(1/2) or x^(1/3) where x is the individual values of a feature.
- **Exponential or Power Transformations:**  
   It involves taking the power of an individual value of a feature (i.e. x^λ), where λ is any number. The goal is to try different values of λ, and see which works best for the case at hand.
- **Box-Cox Transform:**  
   Box-Cox Transform performs transformations under the different values of the parameter λ. The boxcox() SciPy function implements the Box-Cox transformation.  
   It takes an argument, called λ, that controls the type of transform to perform.

> ## Below are some common values of lambda:
>
> - λ = -1 is a reciprocal transform
> - λ = -0.5 is a reciprocal square root transform
> - λ = 0.0 is a log transform
> - λ = 0.5 is a square root transform
> - λ = 1.0 is no transform
> - if λ is not specified then an optimal value is chosen by the function based on the underlying distribution.
