# Saving Data

Learn how to save and load NumPy data.

> We'll cover the following:
>
> - Chapter Goals:
> - A. Saving
> - B. Loading

## Chapter Goals:

- Learn how to save and load data in NumPy
- Write code to save NumPy data to a file

## A. Saving

After performing data manipulation with NumPy, it's good idea to save the data in a file for future use.  
 **To do this, we can use the np.save function.**

- The first argument for the function is the name/path of the file we want to save our data to.  
  The file name/path should have a ".npy" extension. It is does not, then np.save will append the ".npy" extension to it.
- The second argument for np.save is the NumPy data we want to save. The function has no return value.  
   Also, the format of the ".npy" files when viewed with a text editor is largely gibberush when viewed with a text editor.

If np.save is called with the name of a file that already exists, it will overwrite the previous file.

        arr = np.array([1, 2, 3])
        np.save('arr.npy', arr)
        np.save('arr', arr)

## B. Loading

After saving our data, we can load it again using np.load.  
 The function's required argument is the file name/path that contains the saved data.  
 It returns the NumPy data exactly as it was saved.

Note that np.load will not append the ".npy" extension to the file name/path if it is not there.

        arr = np.array([1, 2, 3])
        np.save('arr.npy', arr)
        load_arr = np.load('arr.npy')
        print(repr(load_arr))

