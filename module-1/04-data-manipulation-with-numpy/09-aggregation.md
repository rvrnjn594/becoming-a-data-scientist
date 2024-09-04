# Aggregation

Use aggregate techniques to combine NumPy data and arrays.

> We'll cover the following:
>
> - Chapter Goals:
> - A. Summation
> - B. Concatenation

## Chapter Goals:

- Learn how to aggregate data in NumPy
- Write code to obtain sums and concatenations of NumPy arrays

## A. Summation

As we know how to calculate the sum of individual values between multiple arrays.  
 To sum the values within a single array, we use **np.sum** function.

The function takes in a NumPy arrays as its required argument, and uses the axis keyword argument.  
 If the axis keyword argument is not specified, np.sum returns the overall sum of the array.

        arr = np.array([[0, 72, 3], [1, 3, -60], [-3, -2, 4]])
        print(np.suma(arr))
        print(repr(np.sum(arr, axis=0)))
        print(repr(np.sum(arr, axis=1)))

        ---
        18
        array([ -2,  73, -53])
        array([ 75, -56,  -1])
        ---

**In addition to regular sums, NumPy can perform cumulative sums using np.cumsum.**  
 Like np.sum, np.cumsum also takes in a NumPy array as a required argument and used the axis argument.  
 If the axis keyword argument is not specified, np.cumsum will return the cumulative sums for the flattened array.

        arr = np.array([[0, 72, 3],
                [1, 3, -60],
                [-3, -2, 4]])
        print(repr(np.cumsum(arr)))
        print(repr(np.cumsum(arr, axis=0)))
        print(repr(np.cumsum(arr, axis=1)))

        ---
        array([ 0, 72, 75, 76, 79, 19, 16, 14, 18])
        array([[  0,  72,   3],
            [  1,  75, -57],
            [ -2,  73, -53]])
        array([[  0,  72,  75],
            [  1,   4, -56],
            [ -3,  -5,  -1]])
        ---

## B. Concatenation

An important part of aggregation is combining multiple datasets.  
 In NumPy, this equates to combining multiple arrays into one. The function we use to do this is np.concatenate.

Like the summation functions, np.concatenate uses the axis keyword argument. However, the default value for axis is 0 (i.e. dimension 0).

Furthermore, the required argument for np.concatenate is a list of arrays, which the function combines into a single array.

> For 2-D arrays, not setting the axis argument (defaults to axis = 0) concatenates the arrays vertically.  
>  When we set axis = 1, the arrays are concatenated horizontally.

        arr1 = np.array([[0, 72, 3],
                        [1, 3, -60],
                        [-3, -2, 4]])
        arr2 = np.array([[-15, 6, 1],
                        [8, 9, -4],
                        [5, -21, 18]])
        print(repr(np.concatenate([arr1, arr2])))
        print(repr(np.concatenate([arr1, arr2], axis=1)))
        print(repr(np.concatenate([arr2, arr1], axis=1)))

        ---
        array([[0,  72,   3],
            [  1,   3, -60],
            [ -3,  -2,   4],
            [-15,   6,   1],
            [  8,   9,  -4],
            [  5, -21,  18]])
        array([[0,  72,   3, -15,   6,   1],
            [  1,   3, -60,   8,   9,  -4],
            [ -3,  -2,   4,   5, -21,  18]])
        array([[-15,   6,   1,   0,  72,   3],
            [  8,   9,  -4,   1,   3, -60],
            [  5, -21,  18,  -3,  -2,   4]])
        ---
