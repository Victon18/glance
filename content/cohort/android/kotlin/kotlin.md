---
id: kotlin
aliases: []
tags: []
---

# Packages and import
Packages
----
```kotlin
package org.example

fun printMessage() { /*...*/ }
class Message { /*...*/ }

// ...
```
Imports
---
```kotlin
import org.example.Message // Message is now accessible without qualification
import org.example.* // everything in 'org.example' becomes accessible
import org.example.Message // Message is accessible
import org.test.Message as TestMessage // TestMessage stands for 'org.test.Message'
```

# keyword
[[ktkeyword]]
# kotlin entry point
```kotlin
fun main() {
    println("Hello world!")
}
```
----
```kotlin
fun main(args: Array<String>) {
    println(args.contentToString())
}
```
# Variables
Val
----
```kotlin
fun main() {
    print("Hello")
    print("Welcome")
    val numberOfPhotos = 100
    println(numberOfPhotos)
    val photosDeleted = 10
    println("$numberOfPhotos photos")
    println("$photosDeleted photos deleted")
    println("${numberOfPhotos - photosDeleted} photos left")
}

```
----
Var
-----
```kotlin
fun main() {
    var count = 10
    println("You have $count unread messages.")
    count--
    println("You have $count unread messages.")
    count++
    println("You have $count unread messages.")
}
```
# Datatypes
Numbers
---
- Integer
---

| Type  | Size (bits) | Min value                         | Max value                           |
| ----- | ----------- | --------------------------------- | ----------------------------------- |
| Byte  | 8           | -128                              | 127                                 |
| Short | 16          | -32768                            | 32767                               |
| Int   | 32          | -2,147,483,648 (-231)             | 2,147,483,647 (231 - 1)             |
| Long  | 64          | -9,223,372,036,854,775,808 (-263) | 9,223,372,036,854,775,807 (263 - 1) |

- Floating Point
----

| Type   | Size (bits) | Significant bits | Exponent bits | Decimal digits |
| ------ | ----------- | ---------------- | ------------- | -------------- |
| Float  | 32          | 24               | 8             | 6-7            |
| Double | 64          | 53               | 11            | 15-16          |


Boolean
---
```kotlin
val myTrue: Boolean = true
val myFalse: Boolean = false
val boolNull: Boolean? = null

println(myTrue || myFalse)
// true
println(myTrue && myFalse)
// false
println(!myTrue)
// false
println(boolNull)
// null
```

Characters
----
- Characters are represented by the type Char. Character literals go in single quotes: '1'.
- Speacial Characters
```
\t – tab
\b – backspace
\n – new line (LF)
\r – carriage return (CR)
\' – single quotation mark
\" – double quotation mark
\\ – backslash
\$ – dollar sign
```

- To encode any other character, use the Unicode escape sequence syntax: .
- If a value of character variable is a digit, you can explicitly convert it to an Int number using the digitToInt() function.

```kotlin
val aChar: Char = 'a'
println('\uFF00')
```
Strings
----
Kotlin has two types of string literals:
- Escaped strings
----
```kotlin
val s = "Hello, world!\n"
```
- Multiline strings
----
To remove leading whitespace from multiline strings, use the trimMargin() function:
```kotlin
val text = """
    |Tell me and I forget.
    |Teach me and I remember.
    |Involve me and I learn.
    |(Benjamin Franklin)
    """.trimMargin()
```
By default, a pipe symbol | is used as margin prefix, but you can choose another character and pass it as a parameter, like trimMargin(">").

Array
---


# Comment
```kotlin
/*
 * This program displays the number of messages
 * in the user's inbox.
 */
fun main() {
    // Create a variable for the number of unread messages.
    var count = 10
    println("You have $count unread messages.")

    // Decrease the number of messages by 1.
    count--
    println("You have $count unread messages.")
}

```
# Function
```kotlin
fun birthdayGreeting(name: String = "Rover", age: Int): String {
    return "Happy Birthday, $name! You are now $age years old!"
}
fun main(){
    println(birthdayGreeting(age = 5))
    println(birthdayGreeting("Rex", 2))
}
```


# Opeartor and special symbol
```
+, -, *, /, % - mathematical operators
    * is also used to pass an array to a vararg parameter.
=
    assignment operator.
    is used to specify default values for parameters.
+=, -=, *=, /=, %= - augmented assignment operators.
++, -- - increment and decrement operators.
&&, ||, ! - logical 'and', 'or', 'not' operators (for bitwise operations, use the corresponding infix functions instead).
==, != - equality operators (translated to calls of equals() for non-primitive types).
===, !== - referential equality operators.
<, >, <=, >= - comparison operators (translated to calls of compareTo() for non-primitive types).
[, ] - indexed access operator (translated to calls of get and set).
!! asserts that an expression is non-nullable.
?. performs a safe call (calls a method or accesses a property if the receiver is non-nullable).
?: takes the right-hand value if the left-hand value is null (the elvis operator).
:: creates a member reference or a class reference.
.., ..< create ranges.
: separates a name from a type in a declaration.
? marks a type as nullable.
->
    separates the parameters and body of a lambda expression.
    separates the parameters and return type declaration in a function type.
    separates the condition and body of a when expression branch.
@
    introduces an annotation.
    introduces or references a loop label.
    introduces or references a lambda label.
    references a 'this' expression from an outer scope.
    references an outer superclass.
; separates multiple statements on the same line.
$ references a variable or expression in a string template.
_
    substitutes an unused parameter in a lambda expression.
    substitutes an unused parameter in a destructuring declaration.

Here is the complete list of bitwise operations:
    - shl(bits) – signed shift left
    - shr(bits) – signed shift right
    - ushr(bits) – unsigned shift right
    - and(bits) – bitwise AND
    - or(bits) – bitwise OR
    - xor(bits) – bitwise XOR
    - inv() – bitwise inversion

```
# conditional expression
```kotlin
fun maxOf(a: Int, b: Int): Int {
    if (a > b) {
        return a
    } else {
        return b
    }
}
```
---
```kotlin
fun maxOf(a: Int, b: Int) = if (a > b) a else b
```
# for loop
```kotlin
val items = listOf("apple", "banana", "kiwifruit")
for (item in items) {
    println(item)
}
```
---
```kotlin
val items = listOf("apple", "banana", "kiwifruit")
for (index in items.indices) {
    println("item at $index is ${items[index]}")
}
```
# while loop
```kotlin
val items = listOf("apple", "banana", "kiwifruit")
var index = 0
while (index < items.size) {
    println("item at $index is ${items[index]}")
    index++
}
```
# when
```kotlin
fun describe(obj: Any): String =
    when (obj) {
        1          -> "One"
        "Hello"    -> "Greeting"
        is Long    -> "Long"
        !is String -> "Not a string"
        else       -> "Unknown"
    }
```
# ranges
```kotlin
val x = 10
val y = 9
if (x in 1..y+1) {
    println("fits in range")
}
```
---
```kotlin
val list = listOf("a", "b", "c")

if (-1 !in 0..list.lastIndex) {
    println("-1 is out of range")
}
if (list.size !in list.indices) {
    println("list size is out of valid list indices range, too")
}
```
----
```kotlin
for (x in 1..5) {
    print(x)
}
```
----
```kotlin
for (x in 1..10 step 2) {
    print(x)
}
println()
for (x in 9 downTo 0 step 3) {
    print(x)
}
```
# collection
```kotlin
for (item in items) {
    println(item)
}
```
---
```kotlin
when {
    "orange" in items -> println("juicy")
    "apple" in items -> println("apple is fine too")
}
```
---
```kotlin
val fruits = listOf("banana", "avocado", "apple", "kiwifruit")
fruits
    .filter { it.startsWith("a") }
    .sortedBy { it }
    .map { it.uppercase() }
    .forEach { println(it) }
```
# nullable and nullchecks
```kotlin
fun parseInt(str: String): Int? {
    // ...
}
```
---
```kotlin
fun printProduct(arg1: String, arg2: String) {
    val x = parseInt(arg1)
    val y = parseInt(arg2)

    // Using `x * y` yields error because they may hold nulls.
    if (x != null && y != null) {
        // x and y are automatically cast to non-nullable after null check
        println(x * y)
    }
    else {
        println("'$arg1' or '$arg2' is not a number")
    }
}
```
---
```kotlin
// ...
if (x == null) {
    println("Wrong number format in arg1: '$arg1'")
    return
}
if (y == null) {
    println("Wrong number format in arg2: '$arg2'")
    return
}

// x and y are automatically cast to non-nullable after null check
println(x * y)
```
# Type checks and automatic casts
```kotlin
fun getStringLength(obj: Any): Int? {
    if (obj is String) {
        // `obj` is automatically cast to `String` in this branch
        return obj.length
    }

    // `obj` is still of type `Any` outside of the type-checked branch
    return null
}
```
---
```kotlin
fun getStringLength(obj: Any): Int? {
    if (obj !is String) return null

    // `obj` is automatically cast to `String` in this branch
    return obj.length
}
```
---
```kotlin
fun getStringLength(obj: Any): Int? {
    // `obj` is automatically cast to `String` on the right-hand side of `&&`
    if (obj is String && obj.length > 0) {
        return obj.length
    }

    return null
}
```
#### backlinks
[[index.md]]
