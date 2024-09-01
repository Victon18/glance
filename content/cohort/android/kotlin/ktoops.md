---
id: ktoops
aliases: []
tags: []
---

# Class
```kotlin
class Person { /*...*/ }
class Empty \\Empty class
```
# Constructor
A class in Kotlin has a primary constructor and possibly one or more secondary constructors.
```kotlin
class Person constructor(firstName: String) { /*...*/ }
// If the primary constructor does not have any annotations or visibility modifiers, the constructor keyword can be omitted:
class Person(firstName: String) { /*...*/ }
```
- Initializer
----
If you want to run some code during object creation, use initializer blocks
```kotlin
class InitOrderDemo(name: String) {
    val firstProperty = "First property: $name".also(::println)

    init {
        println("First initializer block that prints $name")
    }

    val secondProperty = "Second property: ${name.length}".also(::println)

    init {
        println("Second initializer block that prints ${name.length}")
    }
}
```
----
```kotlin
class Person(
    val firstName: String,
    val lastName: String,
    var age: Int, // trailing comma
    var isEmployed: Boolean = true,
) { /*...*/ }
```
---
- With visible modifiers

```kotlin
class Customer public @Inject constructor(name: String) { /*...*/ }
```

- Secondary Constructor
---
```kotlin
class Person(val name: String) {
    val children: MutableList<Person> = mutableListOf()
    constructor(name: String, parent: Person) : this(name)
\\this keyword is used as Delegation to another constructor of the same class
{
        parent.children.add(this)
    }
}
```
- Empty primary constructor with non-default visibility
----
```kotlin
class DontCreateMe private constructor() { /*...*/ }
```
# instances of class
```kotlin
val invoice = Invoice()

val customer = Customer("Joe Smith")
```
# Inheritance
```kotlin
\\ open is used to enable inheritance
open class Base(p: Int)
\\ Inheriting the class
class Derived(p: Int) : Base(p)
```
-----
multiple inheritance

```kotlin
open class Rectangle {
    open fun draw() { /* ... */ }
}

interface Polygon {
    fun draw() { /* ... */ } // interface members are 'open' by default
}

class Square() : Rectangle(), Polygon {
    // The compiler requires draw() to be overridden:
    override fun draw() {
        super<Rectangle>.draw() // call to Rectangle.draw()
        super<Polygon>.draw() // call to Polygon.draw()
    }
}
```
Overiding methods
----
```kotlin
open class Shape {
    open fun draw() { /*...*/ }
    fun fill() { /*...*/ }
}

class Circle() : Shape() {
    override fun draw() { /*...*/ }
}
```
---
```kotlin
\\ If you want to prohibit re-overriding, use final

open class Rectangle() : Shape() {
    final override fun draw() { /*...*/ }
}
```
---
Overiding properties
---
```kotlin
interface Shape {
    val vertexCount: Int
}

class Rectangle(override val vertexCount: Int = 4) : Shape // Always has 4 vertices

class Polygon : Shape {
    override var vertexCount: Int = 0  // Can be set to any number later
}
```
Superclass
---
```kotlin
open class Rectangle {
    open fun draw() { println("Drawing a rectangle") }
    val borderColor: String get() = "black"
}

class FilledRectangle : Rectangle() {
    override fun draw() {
        super.draw()
        println("Filling the rectangle")
    }

    val fillColor: String get() = super.borderColor
}
```
---
Inside an inner class, accessing the superclass of the outer class
```kotlin
class FilledRectangle: Rectangle() {
    override fun draw() {
        val filler = Filler()
        filler.drawAndFill()
    }

    inner class Filler {
        fun fill() { println("Filling") }
        fun drawAndFill() {
            super@FilledRectangle.draw()
            // Calls Rectangle's implementation of draw()
            fill()
            println("Drawn a filled rectangle with color ${super@FilledRectangle.borderColor}")
            // Uses Rectangle's implementation of borderColor's get()
        }
    }
}
```
# abstract Class

A class may be declared abstract, along with some or all of its members.
An abstract member does not have an implementation in its class

```kotlin
abstract class Polygon {
    abstract fun draw()
}

class Rectangle : Polygon() {
    override fun draw() {
        // draw the rectangle
    }
}
```
----
You can override a non-abstract open member with an abstract one.

```kotlin
open class Polygon {
    open fun draw() {
        // some default polygon drawing method
    }
}

abstract class WildShape : Polygon() {
    // Classes that inherit WildShape need to provide their own
    // draw method instead of using the default on Polygon
    abstract override fun draw()
}
```
# properties

```kotlin
\\ declaring properties

class Address {
    var name: String = "Holmes, Sherlock"
    var street: String = "Baker"
    var city: String = "London"
    var state: String? = null
    var zip: String = "123456"
}

\\ using properties

fun copyAddress(address: Address): Address {
    val result = Address() // there's no 'new' keyword in Kotlin
    result.name = address.name // accessors are called
    result.street = address.street
    // ...
    return result
}
```
---
Custom Getter and setter
----
```kotlin
class Rectangle(val width: Int, val height: Int) {
    val area: Int
        val area get() = this.width * this.height \\custom getter
}
```
----
```kotlin
var stringRepresentation: String
    get() = this.toString()
    set(value) {
        setDataFromString(value) // custom setter
    }
```
---
```kotlin
\\ visibility of getter and setter
var setterVisibility: String = "abc"
    private set // the setter is private and has the default implementation

var setterWithAnnotation: Any? = null
    @Inject set // annotate the setter with Inject
```

# Interfaces
```kotlin
\\ defining the interface

interface MyInterface {
    fun bar()
    fun foo() {
      // optional body
    }
}

\\ Implementing interfaces

class Child : MyInterface {
    override fun bar() {
        // body
    }
}
```

# data classes
Data classes in Kotlin are primarily used to hold data
```kotlin
data class Person(val name: String) {
    var age: Int = 0
}
```
---
Copying
----
```kotlin
fun copy(name: String = this.name, age: Int = this.age) = User(name, age)
val jack = User(name = "Jack", age = 1)
val olderJack = jack.copy(age = 2)
```
#### backlinks
[[kollin.md]]
