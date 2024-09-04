# Series

Learn about the pandas Series object for 1-D data.

> We'll cover the following:
>
> - Chapter Goals:
> - A. 1-D data
> - B. Index
> - C. Dictionary input

## Chapter Goals

- Learn about the pandas Series object and its basic utilities.
- Write code to create several Series objects

## A. 1-D data

Similar to NumPy, pandas frequently deals with 1-D and 2-D data.  
 However, we use two separate objects to deal with 1-D and 2-D data in pandas.  
 For 1-D data, we use the pandas.Series objects, which we'll refer to simply as a Series.

A Series is created through the pd.Series constructor, which takes in no required arguments but does have a variety of keyword arguments.

> The first keyword argument is data, which specifies the elements of the Series. If data is not set, pd.Series returns an empty Series.  
>  Since the data keyword argument is almost always used, we treat it like a regular first argument (i.e. skip the data=prefix).
>
> Similar to the np.array constructor, pd.Series also takes in the **dtype keyword argument for manual casting**.

        import pandas as pd
        import numpy as np

        # Creating an empty series, will result in DeprecationWarning
        #series = pd.Series()

        # Passing dtype as a parameter to Series for an empty series to avoid DeprecationWarning
        # Creating an empty series
        series = pd.Series(dtype='float64')
        # Newline to separate series print statements
        print('{}\n'.format(series))

        series = pd.Series(5)
        print('{}\n'.format(series))

        series = pd.Series([1, 2, 3])
        print('{}\n'.format(series))

        series = pd.Series([1, 2.2]) # upcasting
        print('{}\n'.format(series))

        arr = np.array([1, 2])
        series = pd.Series(arr, dtype=np.float32)
        print('{}\n'.format(series))

        series = pd.Series([[1, 2], [3, 4]])
        print('{}\n'.format(series))

        ---
        Series([], dtype: float64)

        0    5
        dtype: int64

        0    1
        1    2
        2    3
        dtype: int64

        0    1.0
        1    2.2
        dtype: float64

        0    1.0
        1    2.0
        dtype: float32

        0    [1, 2]
        1    [3, 4]
        dtype: object
        ---

> In our examples, we initialized each Series with its values by setting the first argument using a scaler, list, or NumPy array.
>
> NOTE that pd.Series upcasts values in the same way as np.array.  
> Furthermore, since Series objects are 1-D, the ser variable represents a Series with lists as elements, rather than a 2-D matrix.

## B. Index

In the previous examples, you may have noticed the zero-indexed integers to the left of the elements in each Series.  
 These integers are collectively referred to as the **index of a Series,** and **each individual index element is referred to as a label.**

The default index is integers from 0 to n - 1, where n is the number of elements in the Series.  
 However, we can specify a custom index via the index keyword argument of pd.Series.

        series = pd.Series([1, 2, 3], index=['a', 'b', 'c'])
        print('{}\n'.format(series))

        series = pd.Series([1, 2, 3], index=['a', 8, 0.3])
        print('{}\n'.format(series))

        ---
        a    1
        b    2
        c    3
        dtype: int64

        a      1
        8      2
        0.3    3
        dtype: int64
        ---

The index keyword argument needs to be a list or array with the same length as the data argument for pd.Series. The values in the index list can be any hashable type (e.g. integer, float, string).

## C. Dictionary input

Another way to set the index of a Series is by using a Python dictionary for the data argument.  
 The keys of the dictionary represent the index of the Series, while each individual key is the lacel for its corresponding value.

> The code below shows how to use pd.Series with a Python dictionary as the first argument.  
>  In our example, we set 'a', 'b', and 'c' as the Series index, with corresponding values 1, 2, and 3.

        series = pd.Series({'a':1, 'b':2, 'c':3})
        print('{}\n'.format(series))

        series = pd.Series({'b':2, 'a':1, 'c':3})
        print('{}\n'.format(series))

        ---
        a    1
        b    2
        c    3
        dtype: int64

        b    2
        a    1
        c    3
        dtype: int64
        ---
