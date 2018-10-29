## Tuple
In mathematics, a tuple is a finite ordered list of elements. An n-tuple is a sequence (or ordered list) of n elements.

Kotlin data class provides all the underlying support to create a Tuple
```
data class Tuple<out A, out B, out C, ...>(val first: A, val second: B, third: C, ...)
```
**Note: kotlin does not have `Tuple` type, it uses data class to provide `Pair` & `Triple`**   

See: [Tuples.kt](https://github.com/JetBrains/kotlin/blob/master/libraries/stdlib/src/kotlin/util/Tuples.kt)


## Pair
Represents a generic pair of two values. (`Pair` type is an alias for Tuple with 2 elements)
```
public data class Pair<out A, out B>(public val first: A, public val second: B) : Serializable { }
```

#### Creating `Pair`
```
val fooPair = Pair<Int, Int>(first: 100, second: 200)
val fooPair = Pair<Int, Int>(100, 200)
val fooPair = Pair(100, 200)  // type inference
// fooPair.first = 100
// fooPair.second = 200

// mix type
val fooPair = Pair(100, "foo")
```

#### Destructing `Pair`
```
var (x, y) = Pair(100, "foo") // type inference
// x = 100
// y = "foo"
```

## Triple
Represents a triad of values (`Triple` type is an alias for Tuple with 3 elements)
```
public data class Triple<out A, out B, out C>(public val first: A, public val second: B, public val third: C) : Serializable { }
```

**Creating & destructing are same as `Pair`**
