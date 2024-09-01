# keywords
there are 33 keywords in python

- Boolean -> **False**, **True**,
- Boolean operator -> **and**, **not**, **or**,
- if-else -> **if**, **elif**, **else**,
- loop -> **for**, **while**
- loop-control -> **break**, **continue**, **pass**,
- exception and error -> **except**, **finally**, **try**, **raise**, **with**, **assert**,
- function -> **def**, **return**, **global**, **lambda**, **nonlocal**, **yield**
- import -> **as**, **from**, **import**
- asynchronous ->  **async**, **await**
- oops ->  **class**
- **None** -> it is a datatype signifying nothing
- **in** -> to check for membership
- **del** -> to delete objects, variables, lists, dictionaries, and items from them
- **is** -> to check for equality

# Identifier

```
An identifier that starts with __ is defining a private identifier
An identifier that strats and ends with __ , __add__ is known as magic method
```
----
```python
x = 900
y = 900
print(id (x)) #132285595760592
print(id (y)) #132285595760592
x = 200
print(id(x)) #135138382866792
print(id(y)) #135138374818800
```
# Strings
[[pystrings]]
# Integer
[[pynum]]
# operator
[[pyoperator]]
# truthiness
[[pytruth]]
# Type-casting
```python
print(int(23.5))
print(complex(20))
print(float("23.5"))
```
# Input and Output
```python
firstName = input("What's your name -> ")
age = int(input("Your age ? -> "))
print("IS your name",firstName,"? And your age is ",age, end=" ")
```
# Conditional
```python
age = int(input("What's your age?"))
presidentSelection = """
Select president you want
1 - Punit
2 - Binod
3 - Hari
4 - Sharma
Option:
    """
if age < 0:
    print("Please enter valid age")
elif age > 18:
    print("You are eligible")
    presidentVoted = input(presidentSelection)
    if presidentVoted == 1:
        presidentName = "Punit"
    elif presidentVoted == 2:
        presidentName = "Binod"
    elif presidentVoted == 1:
        presidentName = "Hari"
    else:
        presidentName = "Sharma"
    print(f"You voted for : {presidentName}")
else:
    print("You are not eligible")
    print(f"You can vote for another {18-age} years")
```
# list
[[pylist]]
# loops
[[pyloop]]
# functions
[[pyfun]]

builtins: [[builtins]]
pyhton-modules: [[pymodules]]
python objesct-oriented programming: [[pyoops]]

# Modules

- Numpy: [[numpy]]
- pandas: [[pandas]]
- multithreading: [[multithreading]]
