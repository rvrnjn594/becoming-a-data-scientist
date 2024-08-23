# Nearest Neighbour Regression

Learn about the details of the Nearest Neighbour Regression, which is used for Regression Problems and predicts the outcome based on the nearest neighbors of an instance.

> We'll cover the following:
>
> - Nearest Neighbors Regression
>   - Implementation in Scikit Learn

## Nearest Neighbors Regression

The idea of Nearest Neighbor Regression has been borrowed from **Nearest Neighbors Classification**. Note that:

- The principle behind the nearest neighbors algorithm in regression is to find the nearest, let's say, k neighbors.  
   The neighbors are calculated based on some measure of **similarity or distance** calculation.  
   Based on the value K chosen and neighbors retrieved, this algorithm is also called **K-Nearest neighbors**.
- K is a parameter that can be tuned.
- The output value for a new instance is returned by taking the mean of its nearest neighbors in case of Regression.  
   The important thing to remember is that no equation is constructed and no parameters are optimized.
- The **nearest neighbors algorithms remembers all the training dataset and comes under the category of non-generalizing algorithms** of Machine Learning.  
   It stores the training dataset in some efficient data structures.

#### Implementation in Scikit Learn

The KNeighborsRegressor class implements the KNN algorithm.

        import pandas as pd
        from sklearn.metrics import mean_squared_error
        from sklearn.model_selection import train_test_split
        from sklearn.neighbors import KNeighborsRegressor

        dataset = pd.read_csv("/usr/local/notebooks/datasets/tips.csv")

        X = dataset[["total_bill"]]
        y = dataset[["tip"]]

        X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0, train_size=0.7)

        reg =  KNeighborsRegressor(n_neighbors=5)
        reg.fit(X_train, y_train)
        y_pred = reg.predict(X_test)

        print("The MSE on test set is {0:.4f}".format(mean_squared_error(y_test, y_pred)))
