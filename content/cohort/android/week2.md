# driver class
the class that works as a first start of the engine

```java
// app/java/com.google.app1/Driver.java

class Driver{
// It is blueprint of data which houses homogenous elements

}
```
---
In kotlin we use object same as the driver class
```kotlin
object Driver{
    @JvmStatic // creates one instance for entire scope of project
    fun main(args: Array<String>){
        val rollNo: Int = 13123
        println(rollNo)
        val bigRollNo: Long = 2442351235
        println(bigRollNo)
        val character: Char = "W"
        println(character)
        val name: String = "chupapi"
        println(name)
        println(character+name)

    }
}
```
# function
```kotlin
object Driver{
    @JvmStatic // creates one instance for entire scope of project
    fun main(args: Array<String>){
    val num=display(5)
    print(num)

    }

    fun display(num: Int):Int{
        val rollNo: Int = 13123
        println(rollNo)
        val bigRollNo: Long = 2442351235
        println(bigRollNo)
        val character: Char = "W"
        println(character)
        val name: String = "chupapi"
        println(name)
        println(character+name)
        val ans = "number you got"+num
        return answer
    }
}
```
# oops
```kotlin
object Driver{
    @JvmStatic // creates one instance for entire scope of project
    fun main(args: Array<String>){
    val student1:Student = Student(1, "N", "Neuman")
    println (student1)
    }
    class Student(val rollNo:Int, val firstChar:Char, val name:String){
        ovverride fun toString():String{
         return "Roll-No: "+ rollNo+ "First Character: "+ firstChar + "Name: " + name

        }
    }

}
```
