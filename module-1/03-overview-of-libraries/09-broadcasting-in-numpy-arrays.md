# Broadcasting in Numpy Arrays

Learn to broadcast in Numpy arrays.

> We'll cover the following:
>
> - Indexing, slicing, and iterating
> - Broadcasting

## Indexing, slicing, and iterating

Numpy arrays can be indexed, sliced, and iterated like other Python data structures.

## Broadcasting

Broadcasting is meant to vectorize the array operations. Numpy is written is C language.  
Broadcasting operation vectorize Numpy arrays, so the traversing operation of arrays occurs in C language which makes it very fast. It also avoids making extra copies of the array, which makes it consume less memory.

Numpy operations, on a pair of arrays, usually happen on an element-by-element basis.  
 For example, suppose we multiply two arrays of the same shape.

        import numpy as np
        a = np.array([1.0, 2.0, 3.0])
        b = np.array([2.0, 2.0, 2.0])
        print(a * b)

As you can see below, Numpy Broadcasting will relax the requirement of having the same shape for multiplication.

        import numpy as np
        a = np.array([1.0, 2.0, 3.0])
        b = 2.0
        print(a * b)

The output is the same. Numpy is smart to use only the Scaler to do the calculation instead of making multiple copies. This saves memory.
