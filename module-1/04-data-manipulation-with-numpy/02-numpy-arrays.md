# NumPy Arrays

Learn about NumPy arrays and how they're used.

> We'll cover the following:
>
> - Chapter Goals:
> - A. Arrays
> - B. Copying
> - C. Casting
> - D. NaN
> - E. Infinity

## Chapter Goals

- Learn about NumPy arrays and how to initialize them
- Write code to create several NumPy arrays

## A. Arrays

NumPy arrays are basically just Python lists with added features.  
In fact, you can easily convert a Python list to a Numpy array using the **np.array** function, which takes in a Python list as its required argument.  
 The function also has quite a few keyword arguments, but the main one to know is **dtype**.  
 The dtype keyword argument takes in a NumPy type and manually casts the array to the specified type.

        import numpy as np
        arr = np.array([[0, 1, 2], [3, 4, 5]], dtype = np.float32)
        print(repr(arr))

When the elements of a NumPy array are mixed types, then the array's type will be upcast to the highest level type.  
 This means that if an array input has mixed int and float elements, all the integers will be cast to their floating-point equivalents.  
 If an array is mixed with int, float, and string elements, everything is cast to strings.

        arr = np.array([0, 0.1, 2])
        print(repr(arr))

## B. Copying

Similar to Python lists, when we make a reference to a NumPy array it doesn't create a different array.  
 Therefore, if we change a value using the reference variable, it changes the original array as well. We get around this by using an array's inherent copy function. The function has no required arguments, and it returns the copied array.

In the code example below, c is a reference to a while d is a copy. Therefore, changing c leads to the same change in a, while changing d does not change the value of b.

        a = np.array([0, 1])
        b = np.array([9, 8])
        c = a
        print('Array a: {}'.format(repr(a)))
        c[0] = 5
        print('Array a: {}'.format(repr(a)))

        d = b.copy()
        d[0] = 6
        print('Array b: {}'.format(repr(b)))

## C. Casting

We cast NumPy arrays through their inherent astype function. The function's required argument is the new type for the array.  
 It returns the array cast to the new type.

        arr = np.array([0, 1, 2])
        print(arr.dtype) # int64
        arr = np.astype(np.float32)
        print(arr.dtype) # float32

## D. Nan

When we don't want a NumPy array to contain a value at a particular index, we can use np.nan to act as a placeholder.  
 A common usage for np.nan is as a filler value for incomplete data.

        arr = np.array([np.nan, 1, 2])
        print(repr(arr))

        arr = np.array([np.nan, 'abc'])
        print(repr(arr))

        # Will result in a ValueError: If we uncomment below line
        np.array([np.nan, 1, 2], dtype=np.int32)
        np.array([np.nan, 1, 2], dtype=np.float32)

## E. Infinity

To represent infinity in NumPy, we use the np.inf special value. We can represent negative infinity with -np.inf.

        print(np.inf > 10000) # true

        arr = np.array([np.inf, 5])
        print(repr(arr)) # array([inf, 5.])

        arr = np.array([-np.inf, 1])
        print(repr(arr)) # array([-inf, 1.])

        # Will result in a OverflowError: If we uncomment line 10 and run again.
        # np.array([np.inf, 3], dtype = np.int32)
        np.array([np.inf, 3], dtype = np.float32)
