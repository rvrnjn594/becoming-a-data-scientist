# Filtering

Filter DataFrame for values that fit certain conditions.

> We'll cover the following:
>
> - Chapter Goals:
> - A. Filter conditions
> - B. Filter from functions
> - C. Feature filtering

## Chapter Goals:

- Understand how to filter a DataFrame based on filter conditions
- Write code to filter a dataset of MLB statistics

## A. Filter conditions

> In the Data Manipulation section, we used relation operations on NumPy arrays to create filter conditions.  
>  These filter conditions returned boolean arrays, which represented the locations of the elements that pass the filter.

In pandas, we can also create filter conditions for DataFrames.  
 Specifically, we can **use relation operations on a DataFrame's column features,** which will return a boolean Series representing the DataFrame rows that pass the filter.

The code below demonstrates how to use relation operations as filter conditions.

        df = pd.DataFrame({
        'playerID': ['bettsmo01', 'canoro01', 'cruzne02', 'ortizda01', 'cruzne02'],
        'yearID': [2016, 2016, 2016, 2016, 2017],
        'teamID': ['BOS', 'SEA', 'SEA', 'BOS', 'SEA'],
        'HR': [31, 39, 43, 38, 39]})

        print('{}\n'.format(df))

        cruzne02 = df['playerID'] == 'cruzne02'
        print('{}\n'.format(cruzne02))

        hr40 = df['HR'] > 40
        print('{}\n'.format(hr40))

        notbos = df['teamID'] != 'BOS'
        print('{}\n'.format(notbos))

        ---
            playerID  yearID teamID  HR
        0  bettsmo01    2016    BOS  31
        1   canoro01    2016    SEA  39
        2   cruzne02    2016    SEA  43
        3  ortizda01    2016    BOS  38
        4   cruzne02    2017    SEA  39

        0    False
        1    False
        2     True
        3    False
        4     True
        Name: playerID, dtype: bool

        0    False
        1    False
        2     True
        3    False
        4    False
        Name: HR, dtype: bool

        0    False
        1     True
        2     True
        3    False
        4     True
        Name: teamID, dtype: bool
        ---

In the code above, we created filter conditions for df based on the columns labeled 'playerID', 'HR', and 'teamID'.  
 The boolean Series outputs have True for the rows that pass the filter, and False for the rows that don't.

## B. Filter from funtions

Apart from relation operations, pandas provides various functions for creating specific filter conditions. For columns with string values, we can use str.startswith, str.endswith, and str.contains to filter for specific strings. These functions work the exact same as their namesakes from the Python standard library.

The code below shows various examples of string filter conditions. In the final example using str.contains, we prepend the ~ operation, which negates the filter condition. This means our final filter condition checked for player IDs that do not contain 'o'.

        df = pd.DataFrame({
        'playerID': ['bettsmo01', 'canoro01', 'cruzne02', 'ortizda01', 'cruzne02'],
        'yearID': [2016, 2016, 2016, 2016, 2017],
        'teamID': ['BOS', 'SEA', 'SEA', 'BOS', 'SEA'],
        'HR': [31, 39, 43, 38, 39]})

        print('{}\n'.format(df))

        str_f1 = df['playerID'].str.startswith('c')
        print('{}\n'.format(str_f1))

        str_f2 = df['teamID'].str.endswith('S')
        print('{}\n'.format(str_f2))

        str_f3 = ~df['playerID'].str.contains('o')
        print('{}\n'.format(str_f3))

        ---
            playerID  yearID teamID  HR
        0  bettsmo01    2016    BOS  31
        1   canoro01    2016    SEA  39
        2   cruzne02    2016    SEA  43
        3  ortizda01    2016    BOS  38
        4   cruzne02    2017    SEA  39

        0    False
        1     True
        2     True
        3    False
        4     True
        Name: playerID, dtype: bool

        0     True
        1    False
        2    False
        3     True
        4    False
        Name: teamID, dtype: bool

        0    False
        1    False
        2     True
        3    False
        4     True
        Name: playerID, dtype: bool
        ---

We can also create filter conditions that check for values in a specific set, by using the isin function.  
 The function only takes in one argument, which is a list of values that we want to filter for.

The code below demonstrates how to use the isin function for filter conditions.

        df = pd.DataFrame({
        'playerID': ['bettsmo01', 'canoro01', 'cruzne02', 'ortizda01', 'cruzne02'],
        'yearID': [2016, 2016, 2016, 2016, 2017],
        'teamID': ['BOS', 'SEA', 'SEA', 'BOS', 'SEA'],
        'HR': [31, 39, 43, 38, 39]})

        print('{}\n'.format(df))

        isin_f1 = df['playerID'].isin(['cruzne02',
                                    'ortizda01'])
        print('{}\n'.format(isin_f1))

        isin_f2 = df['yearID'].isin([2015, 2017])
        print('{}\n'.format(isin_f2))

        ---
            playerID  yearID teamID  HR
        0  bettsmo01    2016    BOS  31
        1   canoro01    2016    SEA  39
        2   cruzne02    2016    SEA  43
        3  ortizda01    2016    BOS  38
        4   cruzne02    2017    SEA  39

        0    False
        1    False
        2     True
        3     True
        4     True
        Name: playerID, dtype: bool

        0    False
        1    False
        2    False
        3    False
        4     True
        Name: yearID, dtype: bool
        ---

In pandas, when a Series or DataFrame has a missing value at a location, it is represented by NaN.  
 **The NaN value in pandas is equivalent to np.nan in NumPy.**

Similar to Numpy, we cannot use a relation operation to create a filter condition for NaN values.  
 Instead, we **use the isna and notna functions.**

        df = pd.DataFrame({
        'playerID': ['bettsmo01', 'canoro01', 'doejo01'],
        'yearID': [2016, 2016, 2017],
        'teamID': ['BOS', 'SEA', np.nan],
        'HR': [31, 39, 99]})

        print('{}\n'.format(df))

        isna = df['teamID'].isna()
        print('{}\n'.format(isna))

        notna = df['teamID'].notna()
        print('{}\n'.format(notna))

        ---
            playerID  yearID teamID  HR
        0  bettsmo01    2016    BOS  31
        1   canoro01    2016    SEA  39
        2    doejo01    2017    NaN  99

        0    False
        1    False
        2     True
        Name: teamID, dtype: bool

        0     True
        1     True
        2    False
        Name: teamID, dtype: bool
        ---

The isna function returns True in the locations that contain NaN and False in the locations that don't, while the notna function does the opposite.

## C. Feature filtering

It is really easy to filter a DataFrame's rows based on filter conditions.  
 Similar to direct indexing of a DataFrame, we use square brackets.  
 However, the inside of the square brackets will now contain a filter condition.

When applying filter conditions within square brackets, we retrieve the rows of the DataFrame that pass the filter condition (i.e. the rows for which the filter condition is True).

The code below shows how to filter using square brackets and filter conditions.

        df = pd.DataFrame({
        'playerID': ['bettsmo01', 'canoro01', 'cruzne02', 'ortizda01', 'bettsmo01'],
        'yearID': [2016, 2016, 2016, 2016, 2015],
        'teamID': ['BOS', 'SEA', 'SEA', 'BOS', 'BOS'],
        'HR': [31, 39, 43, 38, 18]})

        print('{}\n'.format(df))

        hr40_df = df[df['HR'] > 40]
        print('{}\n'.format(hr40_df))

        not_hr30_df = df[~(df['HR'] > 30)]
        print('{}\n'.format(not_hr30_df))

        str_df = df[df['teamID'].str.startswith('B')]
        print('{}\n'.format(str_df))

        ---
        playerID  yearID teamID  HR
        0  bettsmo01    2016    BOS  31
        1   canoro01    2016    SEA  39
        2   cruzne02    2016    SEA  43
        3  ortizda01    2016    BOS  38
        4  bettsmo01    2015    BOS  18

        playerID  yearID teamID  HR
        2  cruzne02    2016    SEA  43

            playerID  yearID teamID  HR
        4  bettsmo01    2015    BOS  18

            playerID  yearID teamID  HR
        0  bettsmo01    2016    BOS  31
        3  ortizda01    2016    BOS  38
        4  bettsmo01    2015    BOS  18
        ---
