# Support Vector Regression

**Support Vector Regression is a powerful Model that works on the principles of Support Vector Classification.**  
 However, it is used for Regression problems.

> We'll cover the following:
>
> - Support Vector Regression
>   - Implementation in Scikit Learn

## Support Vector Regression

The idea of Support Vector Regression has been borrowed from Support Vector Machines.

In classification, we predict a discrete-valued output.  
Here are some things to note:

- As the name suggests **Support Vector Regression** is used for predicting the real-valued output.
- The model produced by **Support Vector Regression** depends only on a subset of the training data.
- There is a concept of **Kernel**, which involves mapping the features or columns or dimensions to higher dimensions to make the problem solvable.

#### Implementation in Scikit Learn

SVR class implements the Support Vector Regression.

        import pandas as pd
        from sklearn.svm import SVR
        from sklearn.metrics import mean_squared_error
        from sklearn.model_selection import train_test_split

        dataset = pd.read_csv("tips.csv")

        X = dataset[["total_bill"]]
        y = dataset[["tip"]]

        X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0, train_size=0.7)

        reg =  SVR(kernel="linear")
        reg.fit(X_train, y_train)
        y_pred = reg.predict(X_test)

        print("The MSE on test set is {0:.4f}".format(mean_squared_error(y_test, y_pred)))
