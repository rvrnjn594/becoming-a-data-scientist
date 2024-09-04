# Numpy Basics

Numpy is an acronym for Numerical Python, and it consists of multi-dimensional arrays and comes with functions to operate on them.

> We'll cover the following:
>
> - Numpy
>   - ndarray data structure
> - Difference between Python List and Numpy array
> - Basic operations and manipulations with Numpy arrays
>   - Using different attributes

## Numpy

Data comes in various forms and needs to be stored and processed in Python programs. Numpy is meant for such purposes and enables a person to operate on Data in an optimized and fast way.  
 It handles matrices and multi-dimensional arrays in a very good way. It is used extensively for Linear Algebra Tasks. It comes under the umbrella of modules that are meant for scientific purposes in Python.

#### ndarray data structure

"ndarray" is short for N-dimensional array. It has a fixed size in memory, and contains elements of the same type.  
We will be looking into operations that are extensively used in the industry on Numpy arrays.

## Difference between Python List and Numpy array

All elements in a Numpy array are homogenous, meaning of the same type. A Numpy provides a vast variety of ways to create arrays.  
Elements in a Python List can be of different types. This gives the following advantages to Numpy arrays over Python Lists:

- Mathematical Functions over the homogeneous numpy arrays are extremely fast.
- Numpy arrays consume less memory. Their data types are defined which makes them more optimized than standard Python List.

## Basic operations and manipulations with Numpy array

Now, we will be jumping into extensive hands-on work with Numpy arrays and looking into the operations used extensively in the industry and day-to-day lives of data scientist.

#### Using different attributes

In the below code snippet, we will look at the most commonly used attributes of Numpy arrays.

- ndarray.ndim  
   This is used to get the number of dimensions of a ndarray.
- ndarray.shape
  This gives us the tuple showing us the size of each dimension of a Numpy array.
- ndarray.size
  This gives us the total size of the ndarray and is the multiplication of elements in the tuple obtained by ndarray.shape.
- ndarray.dtype
  This gives the datatype of the ndarray.
- ndarray.itemsize
  This gives is the size in bytes of each element of the ndarray.
- numpy.reshape(a, newshape, order='C')
  It gives us the ndarray with the same data but with a new shape. Parameter a is the ndarray that is to be reshaped.
- numpy.amin(a, axix=0), numpy.sum(a, axis=0), numpy.amax(a, axis=0)
  As the names suggests, these give us the minimum value, sum of values and maximum value of ndarray respectively. Parameter a is the ndarray on which the respective operation is to be applied.  
   Specifically the parameter axis gives us the control to either perform the operation row or column.  
   axis = 0 performs the operation column-wise, and axis = 1 performs the operation row wise.
- numpy.cumsum(a, axis = 0)
  It gives us the cumulative sum along the specified axis. Parameter a is the ndarray on which respective operation is to be applied.
- numpy.ravel(a, order='C')
  It gives us the flatten(1-D) version of the ndarray. Parameter a is the ndarray on which the respective operation is to be applied.
- ndarray.astype(dtype)
  It casts the copy of the array to a specified type.

> Let's move onto some more advanced things that we can do using the Numpy library and its N-dimensional arrays.
