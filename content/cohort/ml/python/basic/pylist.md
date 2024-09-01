# list
DIR
```
__add__', '__class__', '__class_getitem__', '__contains__', '__delattr__', '__delitem__', '__dir__
__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getstate__
__gt__', '__hash__', '__iadd__', '__imul__', '__init__', '__init_subclass__', '__iter__
__le__', '__len__', '__lt__', '__mul__', '__ne__
__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__rmul__
__setattr__', '__setitem__', '__sizeof__', '__str__', '__subclasshook__
append
clear
copy
count
extend
index
insert
pop
remove
reverse
sort
```
# tuple
DIR
```
__add__', '__class__', '__class_getitem__', '__contains__', '__delattr__', '__dir__
__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__
__getnewargs__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__
__iter__', '__le__', '__len__', '__lt__', '__mul__', '__ne__', '__new__', '__reduce__
__reduce_ex__', '__repr__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__
count
index
```
----
```python
x = (1,2,3,4,5)
```
# dictionary
DIR
```
__class__', '__class_getitem__', '__contains__', '__delattr__', '__delitem__
__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__
__getitem__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__
__ior__', '__iter__', '__le__', '__len__', '__lt__', '__ne__', '__new__', '__or__
__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__ror__', '__setattr__
__setitem__', '__sizeof__', '__str__', '__subclasshook__
clear
copy
fromkeys
get
items
keys
pop
popitem
setdefault
update
values
```
```python
phonebook = {'taj':121322,
             'me':44234,
             'riya':42345}
print(len(phonebook))
print(x['me'])
x['me']=11144535
del x['me']
z = (x:x+1 for x in range (10))
```
# set
DIR
```
__and__', '__class__', '__class_getitem__', '__contains__', '__delattr__', '__dir__
__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__
__gt__', '__hash__', '__iand__', '__init__', '__init_subclass__', '__ior__', '__isub__
__iter__', '__ixor__', '__le__', '__len__', '__lt__', '__ne__', '__new__', '__or__
__rand__', '__reduce__', '__reduce_ex__', '__repr__', '__ror__', '__rsub__', '__rxor__
__setattr__', '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__xor__
add
clear
copy
difference
difference_update
discard
intersection
intersection_update
isdisjoint
issubset
issuperset
pop
remove
symmetric_difference
symmetric_difference_update
union
update

```
```python
x = {i for i in range (10)}
```
# index and slicing
indexing and slicing is for list, tuple and dictionary
```python
x = [1,2,3,"string",23.45,54.67,None,True,34.56]
print(x[2])
print(x[-3])
```
---
```python

print(x[1:6])
print(x[:2])
print(x[::-1])
del x[3]
len(x)
```
----
```python
x=[i+1 for i in range(50) ]
```
# nesting
```python
x = [1,2,3,[1,2,3,]4,5]
y = (1,2,3,(1,2,3),4,5)
z = {1:}
t = {1,2,3,4} # nesting is not allowed in sets
```
