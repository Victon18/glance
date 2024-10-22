# nullaeble
null
---

example -> try to access data that does not exists

```kotlin
object Driver{
    @JvmStatic
    fun main(args: Array<String>){
        val empl: Employee? = null // ? (optional) = object can be null
        println(empl)
        println(empl.employeeId)
    }
}
```
