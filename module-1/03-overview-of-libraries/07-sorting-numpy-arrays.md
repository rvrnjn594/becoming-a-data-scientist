# Sorting Numpy Arrays

In this lesson, you'll continue learning about Numpy arrays and their functions.

> We'll cover the following:
>
> - Ordering operations
>   - np.argmax
>   - np.argmin
>   - np.sort

## Ordering operataions

#### np.argmax

It provides the indices of maximum values along an axis. It takes in a parameter axis, which if not specified, the index of maximum entry is returned from the flattened version of the array.  
 If this is specified as zero, the indices of maximum values along the columns are returned and vice versa.

#### np.argmin

It works the same way as argmax, except now the minimum value is returned.

#### np.sort

It sorts the Numpy array. It takes in a parameter of kind to sort from different sorting algorithms like quicksort, mergesort, and heapsort.  
It also takes in a parameter of axis.

- If the axis is specified as None, it flattens the Numpy array, and then sorts it.
- It specified as zero, it sorts along the first axis.
- It left blank, the Numpy array is sorted along the last axis by default.
