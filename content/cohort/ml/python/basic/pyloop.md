# iteration
```python
iterator = iter({'Hi': 1, 'World' : 2, 'Check' : 3}.values())
print(next(iterator))
print(next(iterator))
print(next(iterator))
print(next(iterator))
```
# range
DIR
```
__bool__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__
__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getstate__
__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__
__lt__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__
__setattr__', '__sizeof__', '__str__', '__subclasshook__
count
index
start
step
stop
```
```python

print(list(range(10)))
print(iter(range(10)))
```
---
```python
i = int(input())
for idx, i in enumerate(range(1,i,2)):
    print('*'* (i+1), idx * 2)
```
# for looop
```python
names = input(" whome to wish? :").split(" ")
for i in range(len(names)):
    print(f"happy birthday {names[i]}")
```
# while loop
```python
i = 1

while i <= 100:
    print(i)
    i += 1
```
----
```python
while True:
    print(i)
    i += 1
```
# transfer statements
```python
number = int(input())
for i in range(number):
    if number < 2:
        pass
    elif i in [0,1]:
        continue
    elif number % i == 0:
        print("is not prime")
        break
else:
    print("is prime")
```
