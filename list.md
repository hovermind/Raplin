## List interface
```kotlin
List<T>         // immutable

MutableList<T>  // mutable
```

## Creating list
Kotlin does not have dedicated syntax constructs for creating lists or sets. 
Use methods from the standard library, such as listOf(), mutableListOf()

#### Creating immutable list
```kotlin
val items1 = ArrayList<Int>()           // java.util.ArrayList (by ctor)
val items2 = arrayListOf(1, 2, 3, 4)    // java.util.ArrayList (by library method)
val items3 = listOf<Int>()              // kotlin.collections.EmptyList (by library method)
val items4 = listOf(1, 2, 3, 4)         // java.util.Arrays.ArrayList (by library method)
```
#### Creating mutable list
```kotlin
val items1 = MutableList<Int>(5){i -> 0}	// java.util.ArrayList
val items2 = mutableListOf<Int>()        	// java.util.ArrayList
val items3 = mutableListOf(1, 2, 3, 4)   	// java.util.ArrayList
```

## List methods
```kotlin
val items = listOf(1, 2, 3, 4)

items.first()                                            // 1
items.last()                                             // 4
items.filter { it % 2 == 0 }                             // returns [2, 4]

val rwList = mutableListOf(1, 2, 3)
rwList.requireNoNulls()                                  // returns [1, 2, 3]
if (rwList.none { it > 6 }) println("No items above 6")  // prints "No items above 6"
val item = rwList.firstOrNull()
```
