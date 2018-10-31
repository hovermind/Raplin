## Optional (nullable) type
A regular variable (even string) can not hold `null` (in other languages i.e. C#, Java => string can hold `null`)

```
var name = "Hassan"
name = null        // compilation error
```
If you call a method or access a property on `name`, it's guaranteed not to cause an `NullPointerException`
```
val len = name.length
```
`type?` (i.e. `String?`) allows a variable to hold `null` value
```
var name: String? = "Hassan"
name = null        // OK
```
Now if you want to access the same `length` property, the compiler reports an error
```
val len = name.length    // error: variable 'name' can be null
```
## Using optional variables

**Checking for null in conditions**
```
var name = "Hassan"

val len = if (name != null) name.length else -1
```
**Elvis Operator `?:` with safe call**
```
var name = "Hassan"

val len = name?.length ?: -1    // returns length if name is not null, and null otherwise
```
* `?:` => Elvis Operator (same as C# null coalescing `??`)
* `x?.` => safe call (same as C# conditional access/safe navigation)

**`let` keyword**
```
val listWithNulls: List<String?> = listOf("A", null)

for (item in listWithNulls) {

     item?.let { 
        println(it)  // prints A and ignores null
     } 
}
```

**The `!!` Operator**
For NPE-lovers `x!!` will return a non-null value of `x` or throw an NPE if `x` is `null`
```
var name = "Hassan"

val len = name!!.length
```

## Extra
**Using `elvis` as like Swift guard operator**
```
fun foo(node: Node): String? {

    val parent = node.getParent() ?: return null  // early exit
    
    val name = node.getName() ?: throw IllegalArgumentException("name expected")
    
    // ...
}
```
**Collections of Nullable Type**    
If you have a collection of elements of a nullable type and want to filter non-null elements, you can do so by using filterNotNull
```
val nullableList: List<Int?> = listOf(1, 2, null, 4)
val intList = nullableList.filterNotNull()
```
