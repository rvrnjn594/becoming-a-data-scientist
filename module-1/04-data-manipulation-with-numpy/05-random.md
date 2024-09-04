# Random

Generate numbers and arrays from different random distributions.

> We'll cover the following:
>
> - Chapter Goals:
> - A. Random integers
> - B. Utility functions
> - C. Distributions
> - D. Custom sampling

## Chapter Goals:

- Learn about random operations in NumPy
- Write code using the np.random submodule

## A. Random integers

Similar to the Python random module, NumPy has its own submodule for psuedo-random number generation called **np.random.**  
 It provides all the necessary randomized operations and extends it to multi-dimensional arrays.

To generate pseudo-random integers, we use the **np.random.randint** function.

        print(np.random.randint(5))
        print(np.random.randint(5))
        print(np.random.randint(5, high=6))

        random_arr = np.random.randint(-3, high=14,
                                    size=(2, 2))
        print(repr(random_arr))

The np.random.randint function takes in a single required argument, which actually depends on the high keyword argument. If high=None (which is the default value), then the required argument represents the upper (exclusive) end of the range, with the lower end being 0. Specifically, if the required argument is n, then the random integer is chosen uniformly from the range [0, n).

If high is not None, then the required argument will represent the lower (inclusive) end of the range, while high represents the upper (exclusive) end.

The size keyword argument specifies the size of the output array, where each integer in the array is randomly drawn from the specified range. As a default, np.random.randint returns a single integer.

## B. Utility functions

Some fundamental utility functions from the np.random module are np.random.seed and np.random.shuffle.

We use np.random.seed function to set the random seed, which allows us to control the outputs of the pseudo-random functions.  
 The functions takes in a single integer as an argument, representing the random seed.

        np.random.seed(1)
        print(np.random.randint(10))
        random_arr = np.random.randint(3, high=100,
                                    size=(2, 2))
        print(repr(random_arr))

        # New seed
        np.random.seed(2)
        print(np.random.randint(10))
        random_arr = np.random.randint(3, high=100,
                                    size=(2, 2))
        print(repr(random_arr))

        # Original seed
        np.random.seed(1)
        print(np.random.randint(10))
        random_arr = np.random.randint(3, high=10,
                                    size=(2, 2))
        print(repr(random_arr))

The np.random.shuffle function allows us to randomly shuffle an array. Note that the shuffling happens in place (i.e. no return value), and shuffling multi-dimensional arrays only shuffles the first dimension.

        vec = np.array([1, 2, 3, 4, 5])
        np.random.shuffle(vec)
        print(repr(vec))
        np.random.shuffle(vec)
        print(repr(vec))

        matrix = np.array([[1, 2, 3],
                        [4, 5, 6],
                        [7, 8, 9]])
        np.random.shuffle(matrix)
        print(repr(matrix))

NOTE that only the rows of matrix are shuffled (i.e. shuffling along first dimension only).

## C. Distributions

Using np.random we can also draw samples from probablity distributions.  
 For example, we can use np.random.uniform to draw pseudo-random real numbers from a uniform distribution.

        print(np.random.uniform())
        print(np.random.uniform(low=-1.5, high=2.2.))
        print(repr(np.random.uniform(size=3)))
        print(repr(np.random.uniform(low=-3.4, high=5.9, size=(2, 2))))

The function np.random.uniform actually has no required arguments. The keyword arguments low and high, represent the inclusive lower end and exclusive upper end from which to draw random samples.  
 Since they have default values of 0.0 and 1.0, respectively, the default outputs of np.random.uniform come from the range [0.0, 1.0).

The size keyword argument is the same as the one for np.random.randint, i.e. it represents the output size of the array.

**Another popular distribution we can sample from is the normal(Gaussian) distribution.**  
 The function we use is **np.random.normal.**

        print(np.random.normal())
        print(np.random.normal(loc=1.5, scale=3.5))
        print(np.random.normal(loc=-2.4, scale=4.0, size=(2, 2)))

Like np.random.uniform, np.random.normal has no required arguments. The loc and scale keyword arguments represent the mean and standard deviation, respectively, of the normal distribution we sample from.

## D. Custom sampling

While NumPy provides built-in distributions to sample from, we can also sample from a custom distribution with the np.random.choice function.

        colors = ['red', 'blue', 'green']
        print(np.random.choice(colors))
        print(repr(np.random.choice(colors, size=2)))
        print(repr(np.random.choice(colors, size=(2, 2), p=[0.8, 0.19, -.01])))

The required argument for np.random.choice is the custom distribution we sample from. The p keyword argument denotes the probablities given to each element in the input distribution.  
 Note that the list of probablities for p must sum to 1.  
 When p is not set, the probablities are equal for each element in the distribution (and sum to 1).
