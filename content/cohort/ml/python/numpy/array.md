# masking of array
it involves creating a boolean mask(an array of same shape as original, either true or false)
to filter out or manipulate specific elements based on a condition, by using mask to index the original array
```python
import numpy as np
arr = np.array([1,2,3,4,5])
mask = arr>3
result = arr[marks]
print(result)

# mask
# ['False','False','False','True','True']
```
---
```python
arr = np.array([-2,-1,0,1,2])
mask = arr<0
arr[mask]=0
print(arr)

# mask
# ['True','True','False','False','False']
```
# structured arrays
ndarrays whose datatype is a composition of simpler datatypes organized as a sequence of named feild.

```python
import numpy as np

# define the datatype of each feild
dt = np.dtype([('name','S10'),('age','i4'),('heigth','f8')])
# created the structured array
people = np.array([('John',32,1.83),('Jane',28,1.62)],dtype=dt)
# access the first record
person = people[0]
# access the name feild of the first record
name = person['name']
print(name)
# access the age feild of the first record
age = person['age']
print(age)
# access the height feild of the first record
height = person['height']
print(height)
# calculate the average heigth of all people
avg_heigth = people['height'].mean()
print(avg_height)
# find all people who are older than 30
older_than_30 = people[people['age']>30]
print(older_than_30)
# other features
# define a custom data type for dates
data_dtype = np.dtype([('yaer','i4'),('match','i2'),('day','i2')])
# define the data type for each feild
dt = np.dtype([('name','S10'),('age','i4'),('birthdate', data_dtype),('height','f8')])
# create the structured array
people = np.array([('John',32,(1990,12,25),1.83),('Jane',28,(1993,2,15),1,62)], dtype = dt)
# accessiing the nested lists
# access the birthdate of the first person
birthdate = people[0]['birthdate']
print(birthdate)
# access the year of birth of the first person
year_of_birth = birthdate['year']
print(year_of_birth)
# sorting structured arrays
sorted_people = np.sort(people, order = 'age')
# modifying feilds
# increase the age of all people by 1
people['age']+=1
print(people['age'])
# change the height of the first person
people[0]['height']=1.90
print(people[0]['height'])
```



