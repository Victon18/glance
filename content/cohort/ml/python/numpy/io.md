#  i/o handling
I/O handling  refers to the process of inputting and outputting of data.
reading from files and writing to files

functions for I/O handling

1. numpy.loadtext()
    This function is use to load data from a text or a CSV file into numpy array
2. numpy.genfromtext()
    This function is use to load data from a text or a CSV file into numpy array
    can handel more complex data structures as missing values, variable number of columns
3. numpy.savetext()
    This function is use to save data from numpy array to a text or CSV file
4. numpy.save()
    This function is use to save data from numpy array to a binaary file
    can be loaded later using numpy.load() function
5. numpy.load()
    This function is use to load data from binary file created using numpy.save()
```python
# saving data to text file
data = np.array([[1,2,3],[4,5,6]])
np.savetxt("datadoc.txt",data,delimiter = ",")

loaded_txt = np.loadtext("datadoc.txt",delimiter =  ",")
np.save("data.npy",data)
loaded_data = np.load("data.npy")

# Load data from text file
data = np,genfromtxt("datadoc.text",delemiter = ",", missing values = " ", fitting_values = 0)
print(data)

# compressing arrays for efficient storage

np.savez_compressed("data_compressed.npy",data)
print(data)
```
