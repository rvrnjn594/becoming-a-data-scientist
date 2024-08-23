# Decision Tree Regression

Decision Tree Regression works on the principle of Decision Tree Classification except it is used for Regression Problems.  
 Dive into the Decision Tree Regression in this lesson.

> We'll cover the following:
>
> - Decision Tree Regression
>   - Implementation in Scikit learn

## Decision Tree Regression

The idea of the Decision Tree Regression has been borrowed from Decision Tree Classification. Note that:

- Decision Trees create a tree structure from the dataset at hand. It learns the if/else structure from the dataset.
- We will look into the key algorithms to make a Decision Tree in the Classification section.  
   In the case of Regression, it just returns the continuous valued output for an instance.

#### Implementation in Scikit learn

The DecisionTreeRegressor class is used for Decision Tree Regression.

        import pandas as pd
        from sklearn.metrics import mean_squared_error
        from sklearn.model_selection import train_test_split
        from sklearn import tree

        dataset = pd.read_csv("/usr/local/notebooks/datasets/tips.csv")

        X = dataset[["total_bill"]]
        y = dataset[["tip"]]

        X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0, train_size=0.7)

        # declares the Decision Tree Regressor's object
        reg =  tree.DecisionTreeRegressor()
        reg.fit(X_train, y_train)
        y_pred = reg.predict(X_test)

        print("The MSE on test set is {0:.4f}".format(mean_squared_error(y_test, y_pred)))

- declares the Decision Tree Regressor's object. There are some important parameters passed in.  
   The details of which will be explored in the Classification section.

> Some advanced Regression algorithms are mentioned below.  
>  There explanation is out of the scope of this course.
>
> - Least Angle Regression (LARS)
> - Polynomial Regression
> - Bayesian Regression
> - Robustness Regression
> - Isotonic Regression
