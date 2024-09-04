# Numpy Array Creation

This lesson will reveal more about Numpy and the functions that operate on them.

> We'll cover the following:
>
> - Numpy array creation operations
>   - np.empty
>   - np.eye
>   - np.identity
>   - np.linspace
>   - np.ones
>   - np.zeros

## Numpy array creation operations

#### np.empty

It creates a Numpy array of specified shape and size without initializing it.

#### np.eye

It creates a 2-dimensional Numpy array with diagonal entries as ones and the rest as zeros.  
 It takes in a parameter k, which is zero by default. This means that the main diagonal entries are made as one.  
 A positive value indicates making the upper diagonal entries as one, and a negative value indicates making the lower diagonal entries as one.

#### np.identity

It makes an identity array. An identity array is a square array, meaning the number of rows and columns are equal with ones on the main diagonal.

#### np.linspace

It returns an evely spaced array over a specified interval. It has a start and a stop values that indicates the first and the last value in the sequence.  
 We can exclude/include the stop of the interval specifically by setting a parameter.

#### np.ones

It makes an array of a specified shape and size intialized with only ones.

#### np.zeros

It makes an array of specified shape and size initialized with only zeros.
