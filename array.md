# TOC
* [Creating array by constructor](#)
* [Creating array by standard library functions](#)
* [Creating empty array](#)
* [Size propery & count method](#)


## Creating array by constructor
```kotlin
var numbers = Array<Int>(size, lambda)
// lambda will be called 'size' times (starting with 0) & return value

// or
var numbers = IntArray(size, lambda)
```

## Creating array by standard library functions
`arrayOf()`
```kotlin
val myArray = arrayOf(4, 5, 7, 3, "Chike", false)  // Any ~ Object
var numbers = intArrayOf(1, 2, 3)

// array with default value 0
var numbers = Array<Int>(5){ i -> 0 }      // <= var numbers = Array<Int>(5, { i -> 0 })

// array of 1, 2, 3, 4, 5
var numbers = Array<Int>(5){ i -> i + 1 }  // or var numbers = intArrayOf(1, 2, 3 4, 5)
```
## Creating empty array
* It's an empty array, you can't add/read anything to/from it. 
* It may seem useless, but sometimes you have to pass an array somewhere and this allows you to construct an empty array easily.
* when used in a data class to initialize an array, arrayOf causes a java.util.concurrent.ExecutionException while emptyArray() doesn't
```kotlin
//standard library functions:  arrayOfNulls
val myArray = arrayOfNulls<String>(5)

//standard library functions: emptyArray
val myArray = emptyArray<String>()
```

## Size propery & count method
```kotlin
val myArrayLength = myArray.size
val myArrayLength = myArray.count()
```

**See:** [stdlib](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-array/)
