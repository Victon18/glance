DIR
```
__annotations__
__builtins__
__call__', '__class__', '__closure__', '__code__', '__defaults__', '__delattr__
__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__get__
__getattribute__', '__getstate__', '__globals__', '__gt__', '__hash__', '__init__
__init_subclass__', '__kwdefaults__', '__le__', '__lt__', '__module__', '__name__
__ne__', '__new__', '__qualname__', '__reduce__', '__reduce_ex__', '__repr__
__setattr__', '__sizeof__
__str__
__subclasshook__
```
# function
```python
def make_black_tea( name = "tejas", should_add_sugar = True, tell_me = False):
    if tell_me:
        print("1. Boiling Water")
        print("2. Adding powder")
        if should_add_sugar:
            print("3. Add sugar")
        print("Boiling Some more cup")
        print("Pour in a cup")
    output = f"Black tea made for {name}!"
    if should_add_sugar:
        output = output + "(with sugar)"
    else:
        output = output + "(without sugar )"
    return output
print(make_black_tea())
print(make_black_tea ("Mitr", should_add_sugar = False))
# collections
family = [
    ("jamu",True),
    ("uncle",False),
    ("brother",True),
    ("sis",False),
]
for person in family:
    print(make_black_tea(**person))

tree = [
    ("jamu",),
    ("uncle",),
    ("brother",),
    ("sis",),
]
for person in family:
    print(make_black_tea(*person))
```
# lambda
```python
multiplication = lambda x,y: x*y
print(multiply(123,23))
```
# recursion
```python

```
# map, filter, reduce
```python
from functools import reduce
print("----------------")
x = [2,3,4,5,1.5,1000]
square = lambda x: x * x * 2
x = map (square,map)
for i in x:
    print(i)
print(x)
print("----------------")
is_even  = lambda x: x
x = filter( is_even, x)
for i in x:
    print(i)
print(x)
print("----------------")
sum_up = lambda a,b: a / b
x = reduce(sum_up, x, 5)
print(x)
print("----------------")
```
# your own higher order function
```python
def map(func, list):
    output = []
    for value in list:
        output.append(func(value))
    return iter (output)
x = [2,3,4,5,6,7]
square = lambda x: x*x*2
x = map(square,x)
for i in x:
    print(i)
print(x)
```

