# import
```python
import bevrages
from bevrages import *
from bevrages import soda,tea,coffee
from workspace.beverages import soda
print(workspace.beverages)
import function.main
from workspace.beverages import soda as sondi
```
example
```python
#-----main.py----
def black_tea( name = "tejas", should_add_sugar = True, tell_me = False):
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
def soda(name, Type):
    output = f"{Type} soda made for {name}!"
    return output
def family(names,preferences):
    if  len(names) != len(preferences):
        print("errro")
        return
    return [black_tea(*item) for item in zip(names,preferences)]i
if __name__ = "__main__":
    print(family(["tejas","shiv","mia","shonit"],[True,True,False,False]))
```
---
```python
#---bevrage.py---
import beverages
no_of_family_members = int(input("Enter no of family members:"))
names = []
wants_sugar = []
for i in range(no_of_family_members):
    names.append(input("family member name:"))
    wants_sugar.append(int(input("Their preference O:Yes 1:No")))
print()
for tea in zip(names,wants_sugar):
    print(beverages.black_tea(*tea))
```
# modules
module is a file conatining code which can be used by other file
# packages
packages consists of modules
# gloabals
