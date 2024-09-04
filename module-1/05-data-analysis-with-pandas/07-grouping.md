# Grouping

Learn how DataFrame can be grouped based on particular columns.

> We'll cover the following:
>
> - Chapter Goals:
> - A. Grouping by column
> - B. Multiple columns

## Chapter Goals:

- Learn how to group DataFrames by columns
- Write code to retrieve home run statistics through DataFrame grouping

## A. Grouping by column

When dealing with large amounts of data, it is usually a good idea to group the data by common categories.  
 For example, we could group a large dataset of MLB player statistics by year, so we can deal with each year's data separately.

With pandas DataFrames, we can **perform dataset grouping with the groupby function.**  
 A common usage of the function is to group a DataFrame by values from a particular column, e.g. a column representing years.

The code below shows how to use the groupby function, with the example of grouping MLB data by year.

        # Predefined df of MLB stats
        print('{}\n'.format(df))

        groups = df.groupby('yearID')
        for name, group in groups:
            print('Year: {}'.format(name))
            print('{}\n'.format(group))

        print('{}\n'.format(groups.get_group(2016)))
        print('{}\n'.format(groups.sum()))
        print('{}\n'.format(groups.mean()))

        ---

        yearID teamID     H    R
        0    2017    CLE  1449  818
        1    2015    CLE  1395  669
        2    2016    BOS  1598  878
        3    2015    DET  1515  689
        4    2016    DET  1476  750
        5    2016    CLE  1435  777
        6    2015    BOS  1495  748
        7    2017    BOS  1461  785
        8    2017    DET  1435  735

        Year: 2015
        yearID teamID     H    R
        1    2015    CLE  1395  669
        3    2015    DET  1515  689
        6    2015    BOS  1495  748

        Year: 2016
        yearID teamID     H    R
        2    2016    BOS  1598  878
        4    2016    DET  1476  750
        5    2016    CLE  1435  777

        Year: 2017
        yearID teamID     H    R
        0    2017    CLE  1449  818
        7    2017    BOS  1461  785
        8    2017    DET  1435  735

        yearID teamID     H    R
        2    2016    BOS  1598  878
        4    2016    DET  1476  750
        5    2016    CLE  1435  777

                H     R
        yearID
        2015    4405  2106
        2016    4509  2405
        2017    4345  2338

                        H           R
        yearID
        2015    1468.333333  702.000000
        2016    1503.000000  801.666667
        2017    1448.333333  779.333333
        ---

The grouping code example produced three DataFrames for the years 2015, 2016, and 2017. The three DataFrame groups are contained in the groups variable, and we used its sum and mean functions to retrieve the total and average per-year statistics.

In addition to aggregation functions like sum and mean, we can also filter the groups using filter.  
 The filter function takes in another function as its required argument, which specifies how we want to filter the groups.  
 The output of filter is the concatenation of all the groups that pass the filter.

> The code below shows how to use the filter function.
>
>        no2015 = groups.filter(lambda x: x.name > 2015)
>        print(no2015)
>
> In the above code example, the lambda function passed into filter returns True if the group (represented as x) represents a year greater than 2015. The output is the concatenation of the 2016 and 2017 groups.

## B. Multiple columns

DataFrame grouping is not just limited to a single column. Rather than passing a single column label into groupby, we can **use a list of column labels to specify grouping by multiple columns.**

Grouping by multiple columns can be useful when multiple data features have many different values.  
 For example, if our dataset consisted of MLB players, grouping by both team and year would give us an organized way to view a team's roster throughout the years.

        # player_df is predefined
        groups = player_df.groupby(['yearID', 'teamID'])

        for name, group in groups:
            print('Year, Team: {}'.format(name))
            print('{}\n'.format(group))

        print(groups.sum())

        ---
        Year, Team: (2016, 'BOS')
        yearID   playerID teamID    H
        1    2016  bettsmo01    BOS  214
        2    2016  bogaexa01    BOS  192
        4    2016  pedrodu01    BOS  201

        Year, Team: (2016, 'HOU')
        yearID   playerID teamID    H
        0    2016  altuvjo01    HOU  216
        3    2016  correca01    HOU  158

        Year, Team: (2017, 'BOS')
        yearID   playerID teamID    H
        6    2017  bettsmo01    BOS  166
        7    2017  bogaexa01    BOS  156
        9    2017  pedrodu01    BOS  119

        Year, Team: (2017, 'HOU')
        yearID   playerID teamID    H
        5    2017  altuvjo01    HOU  204
        8    2017  correca01    HOU  133

                        H
        yearID teamID
        2016   BOS     607
            HOU     374
        2017   BOS     441
            HOU     337Year, Team: (2016, 'BOS')
        yearID   playerID teamID    H
        1    2016  bettsmo01    BOS  214
        2    2016  bogaexa01    BOS  192
        4    2016  pedrodu01    BOS  201

        Year, Team: (2016, 'HOU')
        yearID   playerID teamID    H
        0    2016  altuvjo01    HOU  216
        3    2016  correca01    HOU  158

        Year, Team: (2017, 'BOS')
        yearID   playerID teamID    H
        6    2017  bettsmo01    BOS  166
        7    2017  bogaexa01    BOS  156
        9    2017  pedrodu01    BOS  119

        Year, Team: (2017, 'HOU')
        yearID   playerID teamID    H
        5    2017  altuvjo01    HOU  204
        8    2017  correca01    HOU  133

                        H
        yearID teamID
        2016   BOS     607
            HOU     374
        2017   BOS     441
            HOU     337
       ---

In the code above, we grouped the MLB data by both year and team, resulting in each group's name being a tuple of year and team. Using the sum function, we obtained the annual total hits for each team.
