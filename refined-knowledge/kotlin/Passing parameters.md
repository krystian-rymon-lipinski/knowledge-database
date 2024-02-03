up: [[Kotlin basics]]

**Parameters in Kotlin are passed-by-value, a copy of passed object will be created.** These copies are **final**, so they cannot be reassigned!

For **basic types** - original object **will not be affected**.
For **other types** - original object **will be affected**, because copy of a reference will point to the same object.

```kotlin
fun main() {
    var x = 12
    modifyInt(x)
    println(x) //12, original object not affected
    
    val aList = mutableListOf(4, 3)
    aList.myModification()
    println(aList) //[4, 3, 10], original object affected
}

fun modifyInt(number: Int) {
    //number = 21 COMPILATION ERROR (val cannot be reassigned)
    number.inc()
}

fun MutableList<Int>.myModification() {
    add(10)
}
```

---
https://stackoverflow.com/questions/44515031/is-kotlin-pass-by-value-or-pass-by-reference
