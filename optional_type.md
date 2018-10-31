## Optional (Nullable) Type
* a regular variable can not hold null
* to allow nulls, use nullable operator `?`
```
var a: String = "abc"
a = null // compilation error

var b: String? = "abc"
b = null // ok
```

## Dealing with Nullable
Type system distinguishes between references that can hold null (nullable references) and those that can not (non-null references). For non-nullable type, it's guaranteed not to cause an NPE. 
For nullable type, compiler shows error if there is possibilty of NPE.
* **Checking for null in conditions:** `val l = if (b != null) b.length else -1`
* **Safe call (same as C#):** `x?.length` (returns length if `x` is not `null`, and `null` otherwise)
* **Elvis operator(`?:` => C# `??`):** `val personName = name ?: "Hassan"`
* **Elvis operator with safe call:** `val personName = person?.name ?: "Hassan"`
* **`let` keyword:**
```
val listWithNulls: List<String?> = listOf("A", null, null, "B")
for (item in listWithNulls) {
     item?.let { 
        println(it)  // prints A, B and ignores null
     } 
}
```
**Note: scope of `it`(non-null item) is `let {}` block**

## Forced unwrapping
Not-null assertion operator `!!` (for NPE lovers) will return a non-null value of `x` or throw an NPE if `x` is `null`
```
val len = name!!.length  // NPE if name is null

if(name != null){
    val len = name!!.length  // compiler understands name.length is safe here
}
```

## Using elvis operator as like swift guard operator
```
fun foo(node: Node): String? {

    val parent = node.getParent() ?: return null  // early exit
    
    val name = node.getName() ?: throw IllegalArgumentException("name expected")
    
    val x = node?.let { it.x } ?: return
    
    // ...
}
```

## Collections of nullable type
If you have a collection of elements of a nullable type and want to filter non-null elements, you can do so by using filterNotNull
```
val nullableList: List<Int?> = listOf(1, 2, null, 4)
val intList = nullableList.filterNotNull()
```
