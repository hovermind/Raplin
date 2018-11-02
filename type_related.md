## Type inference
Same as C# (variables must be initialized to infer type)
```kotlin
var myInt = 10;
var myDouble = 3.1416
```

## Type alias
```kotlin
typealias NodeSet = Set<Network.Node>
typealias FileTable<K> = MutableMap<K, MutableList<File>>
typealias MyHandler = (Int, String, Any) -> Unit
```

For classes
```kotlin
class A {
    inner class Inner
}

class B {
    inner class Inner
}

typealias AInner = A.Inner
typealias BInner = B.Inner
```
