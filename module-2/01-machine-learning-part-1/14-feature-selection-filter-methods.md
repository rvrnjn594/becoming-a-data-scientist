# Feature Selection (Filter Methods)

Learn about Feature Selection which refers to the process of selecting the most appropriate features for making the model.

> We'll cover the following:
>
> - Feature Selection
>   - Filter Methods
>     - Removing features with low variance
>     - Univariate Selection Methods
>     - Coding examples
>       - Code 1 to 5.

## Feature Selection

Feature or Variable Selection refers to the process of selecting features that are used in predicting the target or output. The purpose of Feature Selection is to select the features that contribute the most to output prediction.

> The following line from the abstract of Machine Learning Journal sums up the purpose of Feature Selection.
>
> **_"The objective of variable selection is three-fold: improving the prediction performance of the predictors, providing faster and more cost-effective predictors, and providing a better understanding of the underlying process that generated the data."_**

Usually these benefits of Feature Selection are quoted:

- **Reduces overfitting:**  
   If the model is overfitting(high variance), reducing the number of features is one of the methods to reduce overfitting.
- **Improves accuracy:**  
   Less overfitting would perform well on the unseen dataset, so it ultimately leads to the improved accuracy of the model.
- **Reduces training time:**  
   A smaller number of features means that there will be less data to train and training will be faster.

Feature Selection Methods are categorized into the following methods:

### Filter Methods

The Filter Methods involve **selecting features based on their various statistical scores with the output column.** The selection of features is independent of any Machine Learning algorithm.  
The following rules of thumb are as follows:

- The more the features are correlated with the output column or column to be predicted, the better the performance of the model.
- Features should be least correlated with each other. If some of the input features are correlated with some additional input features, this situation is known as **Multicollinearity.**  
   (We recommend getting rid of such a situation for better performance of the model.)

#### Removing features with low variance

In Scikit Learn, **VarianceThreshold** is a simple baseline approach to Feature Selection.  
It removes all features whose variance doesn't meet some threshold.  
 This involves removing the features having the same value (zero-variance features) in all of their rows or to a specified number of rows.  
 Such features provide no value in building the machine learning predictive model.

## Univariate Selection Methods

Univariate Feature Selection methods selects the best features based on Univariate Statistical tests.  
Scikit Learn provides the following methods in the Univariate Feature Selection methods.

- SelectKBest
- SelectPercentile

These two above are the most commonly used methods.

- **SelectKBest:**  
   It gives us the K best features. It takes in two arguments, k which tells how many features to select and score_func which tells us which statistical test to use.  
   The k value can be specified as all, which gives us the score of all the input features with the output column.
- **score_func:**  
   It can be one of the following scoring functions:

  1.  **For regression:** f_regression, and mutual_info_regression
  2.  **For classification:** chi2, f_clasif, and mutual_info_classif

  **f_regression:** It is meant for Regression Problems. It calculates the correlation between each input feature and the output column. It is converted to an F score then to a p-value.

  **mutual_info_regression:** Mutual Information (MI) is the measure of mutual dependence between two variables. It is a non-negative value.  
  If Mutual Information (MI) value is zero, it shows that the variables under consideration are independent.  
   If the Mutual Information (MI) value is high, it shows a high dependence between the variables.  
   This scoring function is meant for Regression Problems only, meaning when the output variable is a continuous-valued output.

  Mutual Information requires a greater number of samples to between estimate dependence between two variables.

  **chi2:** It is meant for classification problems. It computes the chi-squared stats χ2 between each non-negative feature and the output categorical variable.  
   Chi-square test measures dependency between variables and helps us exclude the variables that are independent of the target variables.

  **f_classif** It is the alternative for f_regression in classification problems. It is best recommended for numerical inputs and categorical outputs.

  **mutual_info_classif** It is the alternative for mutual_info_regression in classification problems.

  - **SelectPercentile:** It selects features according to a percentile of the highest scores.  
    It takes in two arguments, score_func which is the same argument as seen above in the case of SelectKBest.  
    The second argument is percentile which denotes how many percentile of features to keep.
  - **Correlation Matrix:** It simply gives us the pairwise correlation measure between the features.

---

#### Coding Examples

The coding examples below demonstrate use cases for the above measures.

###### Code 1

        from sklearn.datasets import make_regression
        from sklearn.feature_selection import SelectKBest
        from sklearn.feature_selection import f_regression

        # generate dataset
        X, y = make_regression(n_samples=100, n_features=100, n_informative=10)
        # define feature selection
        fs = SelectKBest(score_func=f_regression, k=10)
        # apply feature selection
        X_selected = fs.fit_transform(X, y)

        print(X_selected.shape)

- make_regression makes a sample Regression Dataset with one-hundred samples and one hundred features. Among the one-hundred features, only ten are informative. The target consists of continuous values. Input features are stored in X, and the output variale is stored into y.
- SelectKBest passes in f_regression as the scoring function and k=10 for getting the top ten scoring features.
- fit_transform applies the Feature Selection method, and last line prints the shape of the new dataset after the Feature Selection.
- In the above code, we have numerical input and the numerical output.

###### Code 2

        from sklearn.datasets import make_classification
        from sklearn.feature_selection import SelectKBest
        from sklearn.feature_selection import f_classif

        # generate dataset
        X, y = make_classification(n_samples=100, n_features=20, n_informative=2)
        # define feature selection
        fs = SelectKBest(score_func=f_classif, k=2)
        # apply feature selection
        X_selected = fs.fit_transform(X, y)
        print(X_selected.shape)

- make_classification makes a sample classification dataset with one-hundred samples and twenty features and two classes (0 and 1). Among the twenty features only two are informative. Input features are stored in X and output classes are stored into y.
- SelectKBest passes in f_classif as the scoring function and k=2 for getting the top two scoring features.
- fit_transform applies the Feature Selection method and then print the shape of the new dataset after the Feature Selection.
- In the above code, we have numerical input and the categorical output encoded as 0 and 1.

###### Code 3

        from sklearn.datasets import load_iris
        from sklearn.feature_selection import SelectKBest, chi2

        X, y = load_iris(return_X_y=True)
        print(X.shape)
        # select the two best features
        X_new = SelectKBest(chi2, k=2).fit_transform(X, y)
        print(X_new.shape)

- In the above example we load the Iris Dataset, which is having four attributes (as can be seen from the shape X.shape) sepal lenght in cm, sepal width in cm, petal lenght in cm and petal width in cm. It is contained in X above.
- The output variable contains 3 classes (Iris Setosa, Iris Versicolour, Iris Virginica). It is contained in y above and have been encoded using LabelEncoder of ScikitLearn. It assigns “0 for Iris Setosa” , "1 for Iris Versicolo and “2 for Iris Virginica”.
- then we print the shape of the dataset with input features.
- finally, we pass in chi2 scoring function and k=2 for selection the top 2 features.

###### Code 4

        from sklearn.datasets import load_digits
        from sklearn.feature_selection import SelectPercentile, chi2
        X, y = load_digits(return_X_y=True)
        print(X.shape)

        # now select features based on top 10 percentile
        X_new = SelectPercentile(chi2, percentile=10).fit_transform(X, y)
        print(X_new.shape)

- we load the Digits Dataset, which is having 64 attributes (as can be seen from the shape X.shape). These 64 attributes are the individual pixels of gray scale images with dimensions=8x8 being used as features. It is contained in X above.
- The output variable y contains 10 classes. 0,1,2,3,4,5,6,7,8,9 one for each digit from 0-9.
- we print the shape of the dataset with input features.
- we pass in chi2 scoring function and percentile=10.
- Last line shows us that the columns in the dataset are now 7 which are most correlated with the output column. We can see that only 7 features lie on the top 10 percentile and hence we select them accordingly.

###### Code 5

        from sklearn.datasets import load_iris
        import pandas as pd
        iris = load_iris()

        # Create features and target
        X = iris.data
        y = iris.target

        # Convert feature matrix into DataFrame
        df = pd.DataFrame(X, columns=["sepal_length", "sepal_width", "petal_length", "petal_width"])

        # Create correlation matrix
        corr_matrix = df.corr()
        print(corr_matrix)

- In the above example, we load the Iris Dataset, which has four attributes: sepal length in cm, sepal width in cm, petal length in cm and petal width in cm.
- The output variable y, contains three classes (Iris Setosa, Iris Versicolour, and Iris Virginica). It assigns “0 for Iris Setosa”, “1 for Iris Versicolo”, and “2 for Iris Virginica”.
- we construct the dataframe from the input features X.
- df.corr() the pairwise correlation between the input features and rhen prints that.
- The diagonal of the Matrix contains one, revealing the correlation of a feature with itself. The more values close to 1, the more the features are positively correlated. If an input feature is correlated with some other input feature, we should get rid of it to ensure good performance of the model.

> In case we have the Categorical Input features, we can use any of the encoding schemes mentioned above and then move forward with calculating the scores for Feature Selection. We can use **Ordinal Encoding Scheme using OrdinalEncoder** for the input variables and then use **LabelEncoder for the output categorical variable.** We can use either the chi2 scoring function or the mutual_info_classif scoring function to choose the top correlated features.
>
> ---
>
> Other Univariate Feature Selection Methods being used in the field are
>
> - SelectFpr, SelectFdr, or SelectFwe
> - GenericUnivariateSelect
