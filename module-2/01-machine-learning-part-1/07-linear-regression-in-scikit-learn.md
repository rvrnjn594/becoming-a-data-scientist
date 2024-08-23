# Linear Regression in Scikit Learn

Scikit Learn provides an easy-to-use implementation of Linear Regression. You can discover more about that implementation here.

> We'll cover the following:
>
> - Linear Regression in Scikit Learn
>   - Implementation 1
>   - Implementation 2

## Linear Regression in Scikit Learn

We will be looking into how to use Scikit Learn, the famous library for classical Machine Learning, for Linear Regression.

#### Implementation 1

The following code snippet illustrates how LinearRegression() class is used in the implementation.

        # necessary modules imported
        import pandas as pd
        from sklearn import linear_model
        from sklearn.metrics import mean_squared_error
        from sklearn.model_selection import train_test_split

        # loads the dataset
        dataset = pd.read_csv("tips.csv")

        # extract the relevant independent and dependent columns
        X = dataset[["total_bill"]]
        y = dataset[["tip"]]

        # divide dataset into training and test dataset
        X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0, train_size=0.7)

        reg = linear_model.LinearRegression()
        # fits the Regression model on the training dataset
        reg.fit(X_train, y_train)
        # uses trained model to predict the values for the test dataset.
        y_pred = reg.predict(X_test)

        # displays the Mean Squared Error on the test dataset. Lesser value indicate that the model has trained well and vice versa
        print("The MSE on test set is {0:.4f}".format(mean_squared_error(y_test, y_pred)))

#### Implementation 2

In implementation 2, SGDRegressor() class is used as illustrated below.  
 It has the same underlying implementation that works to find the optimal parameters as gradient descent.

        import pandas as pd
        from sklearn import linear_model
        from sklearn.metrics import mean_squared_error
        from sklearn.model_selection import train_test_split

        dataset = pd.read_csv("tips.csv")

        X = dataset[["total_bill"]]
        y = dataset[["tip"]]

        X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0, train_size=0.7)

        # passes in loss = "squared_loss" which is meant for Linear Regression. max_iter=1000 specifies the epochs.
        # Epoch is the number of passes done over the training data to fully train the model.
        reg = linear_model.SGDRegressor(loss='squared_loss', max_iter=1000)
        reg.fit(X_train, y_train)
        y_pred = reg.predict(X_test)

        print("The MSE on test set is {0:.4f}".format(mean_squared_error(y_test, y_pred)))

> **Things to be noted:**
>
> The above concepts are illustrated for you to get familiar with the classes and functions. As we move forward in the course, we will dig into concepts like:
>
> - Data Wrangling
> - Exploratory Data Analysis
> - Feature Engineering
> - Feature Selection
> - Model Selection and Evaluation
> - Hyper-parameter optimization
>
> These are very important concepts to grasp because they are helpful while working in the industry.
> Many online courses just list down the topics without actually going into how they are used.
