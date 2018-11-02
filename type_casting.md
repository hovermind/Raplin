## Casting
* kotlin does not support implicit conversion
* types in kotlin are objects thus have associated helper methods
* helper methods can be used in both directions - widening (safe) & narrowing (loss of data)
```kotlin
var intVal: Int = 55;
var longVal: Long = intVal  // Error: type mismatch
```

##### Helper methods
* toByte() 
* toShort()
* toInt()
* toLong()
* toFloat()
* toDouble()
* toChar()
```kotlin
var intVal = 55  // Int
var longVal = intVal.toLong()
var reIntVal = longVal.toInt()
```

## Type check with is
```kotlin
if (obj is String) {
    print("a String")
}

if (obj !is String) {      // same as !(obj is String)
    print("Not a String")
}
```

## Smart cast with is
```kotlin
fun demo(x: Any) {
    if (x is String) {
        print(x.length)   // x is automatically cast to String
    }
}

if (x !is String) return
print(x.length)           // x is automatically cast to String

// x is automatically cast to string on the right-hand side of `||`
if (x !is String || x.length == 0) return

// x is automatically cast to string on the right-hand side of `&&`
if (x is String && x.length > 0) {
    print(x.length)       // x is automatically cast to String
}
```

## Unsafe cast with as
```kotlin
val x = y as String  // if y is null, there will be error because x is not nullable
```

## Safe cast with as
```kotlin
val x: String? = y as? String
val x: String? = y as! String   // auto unwrap
```
