# TOC
* [Optional type](/optional_type.md#optional-type)
* [Null stafety](/optional_type.md#null-stafety)
* [Forced unwrapping](/optional_type.md#forced-unwrapping)
* [Using elvis operator as like swift guard operator](/optional_type.md#using-elvis-operator-as-like-swift-guard-operator)
* [Collections of nullable type](/optional_type.md#collections-of-nullable-type)

## Optional type
* type system distinguishes between references that can hold null (nullable) and those that can not
* a regular variable can not hold null
* to allow nulls, use nullable operator `?`
```kotlin
var a: String = "abc"
a = null // compilation error

var b: String? = "abc"
b = null // ok
```

## Null stafety
For non-nullable type, it's guaranteed not to cause an NPE. For nullable type, compiler shows error if there is possibilty of NPE.
* **Checking for null in conditions:** `val l = if (b != null) b.length else -1`
* **Safe call:** `x?.length` (returns length if `x` is not `null`, and `null` otherwise) 
* **Elvis operator:** `val personName = name ?: "Hassan"` (`?:` => C# `??`)
* **Elvis operator with safe call:** `val personName = person?.name ?: "Hassan"`
* **Safe casts:** `val x: Int? = a as? Int` (`null` if casting fails, instead of throwing `ClassCastException`)
* **`let` keyword:**
```kotlin
val listWithNulls: List<String?> = listOf("A", null, null, "B")
for (item in listWithNulls) {
     item?.let { 
        println(it)  // prints A, B and ignores null
     } 
}
```

## Forced unwrapping
Not-null assertion operator `!!` (for NPE lovers) will return a non-null value of `x` or throw an NPE if `x` is `null`
```kotlin
val len = name!!.length  // NPE if name is null

if(name != null){
    val len = name!!.length  // compiler understands name.length is safe here
}
```

## Using elvis operator as like swift guard operator
```kotlin
fun foo(node: Node): String? {

    val parent = node.getParent() ?: return null  // early exit
    
    val name = node.getName() ?: throw IllegalArgumentException("name expected")
    
    val x = node?.let { it.x } ?: return
    
    // ...
}
```

##### guard extension function
```kotlin
// Declare an extension function that calls a lambda called block if the value is null
inline fun <T> T.guard(block: T.() -> Unit): T {
    if (this == null) block(); return this
}

val thing: String? = null
//if the thing is null it will return. Otherwise it will assign the value to notNullThing val
val notNullThing = thing.guard { return }
```

## Collections of nullable type
If you have a collection of elements of a nullable type and want to filter non-null elements, you can do so by using filterNotNull
```kotlin
val nullableList: List<Int?> = listOf(1, 2, null, 4)
val intList = nullableList.filterNotNull()
```
