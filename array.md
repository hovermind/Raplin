# TOC
* [Array in kotlin](#Array-in-kotlin)
* [Specialized class for array](#Specialized-class-for-array)
* [Creating array](#Creating-array)
* [Size propery and count method](#Size-propery-and-count-method)

## Array in kotlin
* arrays in Kotlin are represented by the Array class
* it has size property & get/set functions (that turn into []), along with a few other useful member functions
```kotlin
class Array<T> private constructor() {
    val size: Int
    operator fun get(index: Int): T
    operator fun set(index: Int, value: T): Unit

    operator fun iterator(): Iterator<T>
    // ...
}
```

## Specialized class for array
Kotlin also has specialized classes (`ByteArray`, `ShortArray`, `IntArray`) to represent arrays of primitive types without boxing overhead:
```kotlin
val x: IntArray = intArrayOf(1, 2, 3)
x[0] = x[1] + x[2]
```

## Creating array
#### by constructor
`Array<Int>(size, lambda)` : lambda will be called 'size' times (starting with 0) & return value
```kotlin
var numbers = Array<Int>(5){ i -> 0 }      // syntactic sugar of: var numbers = Array<Int>(5, { i -> 0 })

var numbers = Array<Int>(5){ i -> i + 1 }
```

#### by `arrayOf()` library function
```kotlin
val foo = arrayOf(4, 5, 7, 3, "Chike", false)
val numbers = intArrayOf(1, 2, 3)
```

#### `arrayOfNulls()`
```kotlin
val myArray = arrayOfNulls<String>(5)
```

#### `emptyArray()`
```kotlin
val myArray = emptyArray<String>()
```

**Notes:**
* it's an empty array, you can't add/read anything to/from it. 
* it may seem useless, but sometimes you have to pass an array somewhere and this allows you to construct an empty array easily.
* when used in a data class to initialize an array, arrayOf causes a java.util.concurrent.ExecutionException while emptyArray() doesn't

## Size propery and count method
```kotlin
val myArrayLength = myArray.size

val myArrayLength = myArray.count()
```

**See:** [stdlib](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-array/)
