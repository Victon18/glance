# function
The fn declaration enforces type-checking and memory-safe behaviours (Rust style),
while def allows no type declarations and dynamic behaviours (Python style).
```python
def greet(name):
    return "Hello, " + name + "!"
fn greet2(name: String) -> String:
    return "Hello, " + name + "!"
def main():
   print("Hello, world!")

```
## arguments
### optional argument
```python
fn pow(base: Int, exp: Int = 2) -> Int:
    return base ** exp

fn use_defaults():
    # Uses the default value for `exp`
    var z = pow(3)
    print(z)
```
However, you cannot define a default value for an argument that's declared as inout.
### keywords argument
```python
fn pow(base: Int, exp: Int = 2) -> Int:
    return base ** exp

fn use_keywords():
    # Uses keyword argument names (with order reversed)
    var z = pow(exp=3, base=2)
    print(z)
```
### variadiac arguments
```python
fn sum(*values: Int) -> Int:
  var sum: Int = 0
  for value in values:
    sum = sum+value
  return sum
```
The variadic argument values here is a placeholder that accepts any number of passed positional arguments.

Iterating over this list directly with a for..in loop currently produces a Reference for each value instead of the value itself.
Add an empty subscript operator [] to dereference the reference and retrieve the value:
```python
fn make_worldly(inout *strs: String):
    # Requires extra [] to dereference the reference for now.
    for i in strs:
        i[] += " world"

```
#### variadic keyword arguments

Variadic keyword arguments allow the user to pass an arbitrary number of keyword arguments.
```python
fn print_nicely(**kwargs: Int) raises:
  for key in kwargs.keys():
      print(key[], "=", kwargs[key[]])

 # prints:
 # `a = 7`
 # `y = 8`
print_nicely(a=7, y=8)
```
### Positional-only arguments
When defining a function, you can restrict some arguments so that they can only be passed as positional arguments, or they can only be passed as keyword arguments.
```python
fn min(a: Int, b: Int, /) -> Int:
    return a if a < b else b
```
### keyword-only argument
```python
fn sort(*values: Float64, ascending: Bool = True): ...

#if the function doesn't accept variadic arguments, you can add a single star (*) to the argument list to separate the keyword-only arguments
fn kw_only_args(a1: Int, a2: Int, *, double: Bool) -> Int:
    var product = a1 * a2
    if double:
        return product * 2
    else:
        return product
```
## Overloaded functions
To work with different data types, you need to implement separate versions of the function that each specify different argument types
```python
fn add(x: Int, y: Int) -> Int:
    return x + y

fn add(x: String, y: String) -> String:
    return x + y
```
---
```python
@value
struct MyString:
    fn __init__(inout self, string: StringLiteral):
        pass

fn foo(name: String):
    print("String")

fn foo(name: MyString):
    print("MyString")

fn call_foo():
    var string = "Hello"
    # foo(string) # This call is ambiguous because two `foo` functions match it
    foo(MyString(string))
```

