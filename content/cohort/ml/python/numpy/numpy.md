# numpy-arrays
grid of homogenous data type

```python
import numpy as np
# creating array
a = np.array([1,2,3,4,5])
b = np.array([5,7,17,116])
print("sum: ",a+b)
print("product: ",np.dot(a,b))
```
memory usage of numpy array and list

```python
import sys
a = [1,2,3,4,5]
b = np.array([1,2,3,4,5])
print("List -> ", sys.getsizeof(a))
print("Array -> ", b.nbytes)
```
# types of array and its creation
1. converting python sequences to numpy arrays

```python
#1D
lst1 = [1,2,3,4,5]
arr1 = np.arrray(lst1)
print(arr1)
tup1 = [1,2,3,4,5]
arr2 = np.array(tup1)
print(arr2)

#2D
arr2 = np.array([[1,2],[3,4]])
print(arr2)
#3D
arr3 = np.array([[[1,2,3],[3,4,6]]])
print(arr3)
```

2. array creation function
- np.zeros
- np.ones
- np.empty
- np.arange
- np.linspace
- np.logspace
- np.full
- np.eye

```python
#1D
np.arange(2,10)
np.arange(2,10, dtype = float)
np.arange(2,10,0.5)
np.linspace(2.0,3.0,num = 5)
#2D
np.eye(2,3)
#3D
np.zeroes((2,1))
np.ones((3,2))
np.empty([2,3], dtype = int)
```
# operation
```python
import numpy as np
a = np.array([1,2,3,4,5])
b = np.array([2,3,4,5,6])
# addition
print(a+b)
# substraction
print(a-b)
# multiplication
print(a*b)
# division
print(a/b)
# modulo
print(a%b)
# exponential
print(a**b)
# matrix multiplication
c = np.array([[1,2],[3,4]])
d = np.array([[3,4],[6,7]])
print(np.dot(c,d))
# trignometric function
trig = np.array([0,15,30,60])
trig1 = np.deg2rad(trig) # degree to radian

print("Sin :", np.sin(trig1))
print("Cos :", np.cos(trig1))
print("Tan :", np.tan(trig1))
# logrithemic functions
print(np.log(a))
print(np.log10(a))
# bitwise operations
bit1 = np.array([1,2,3,4,5],dtype = np.uint8)
bit2 = np.array([4,5,6,7,8],dtype = np.uint8)
print("Bitwise and : ", np.bitwise_and(bit1,bit2))
print("Bitwise or : ", np.bitwise_or(bit1,bit2))
```
# comparision
```python
print(a==b)
print(a>b)
print(a<b)
print(a!=b)
print(a>=b)
print(a<=b)
```
# aggregate function
```python
# sum
print(np.sum(a))
# mean
print(np.mean(a))
# median
print(np.median(a))
# standard deviation
print(np.std(a))
# variance
print(np.var(a))
# maximum
print(np.amax(a))
# minimum
print(np.amin(a))
```
# sorting
````python
print(np.sort(a))
print(np.sort(a)[::-1])
````

# slicing and indexing
indexing is the process of accessing individual elements of array in Numpy
```python
import numpy as np
a = np.array([3,4,5,6,7])
print(a[2])
print(a[-6])
b = np.array([1,2,3][4,5,6])
print(b[1][2])

# boolean indexing
arr = np.array([1,2,3,13,45,56,1])
arr[arr!=1] -= 1
print(arr)
```
---
slicing is the process of accessing a sub-array or a subset of elements within an array.
```python
# variable[start:stop:steps]
arr = np.array([1,2,3,4,5,6])
print(arr[2:5:2])

```
# reshape, split, stacking
reshaping is the process of converting a numpy array into a different shape without changing its data
```python
# reshape
a = np.array([[1,2,4],[2,3,4,]])
b = a.reshape(3,2)
print(b)
```
---
splitting is the process of dividing a numpy array into similar array along one or more axes
```python
# splitting
b,c = np.split(a,2,axis=0)
print(b)
print(c)
```
---
stacking is the process of combining two or more numpy array into single array along a new axis
```python
# stacking
a = np.array([1,2,3,4,5])
b = np.array([7,8,,9,0,8])
vs = np.vstack((a,b))
print(vs)
hs = np.hstack((a,b))
print(hs)
```
----
```python
# concatenate
a = np.array([1,2,3,4,5])
b = np.array([6,7,,8,9,0])
c = np.concatenate((a,b), axis = 0)
print(c)
d = np.concatenate((a,b), axis = None)
print(d)
```
----
```python
# tanspose
print(a.T)

# size
print(a.size)

# nshape
print(a.nshape)

# ndim
print(a.ndim)
```
# broadcasting
broadcasting is a feature in numpy library that allows for arithematic operation between array of diferent shapes
```python
# simple
a = np.array([1,2,3,4,5])
b = 2.0
c = a*b
print(c)

a = np.array([1,2,3,4,5])
b = np.array([[0],[2],[3]])
c = a+b
print(c)

# advance broadcasting
a = np.array([[1,2,3],[5,6,7]])
b = np.array([10,20,30])
c = a+b
print(c)
```

[[array]]
[[plotting]]
[[io]]