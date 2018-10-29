## Exception
`try-catch` works pretty much the same way as it does in Java
```
try {
    // some code
}
catch (e: SomeException) {
    // handler
}
finally {
    // optional finally block
}
```

To throw an exception object, use the throw-expression:
```
throw Exception("Foo Exception")
```

## Try expression
In kotlin, try is an expression, i.e. it may have a return value:
```
val a: Int? = try { parseInt(input) } catch (e: NumberFormatException) { null }
```
The returned value of a try-expression is either the last expression in the try block or the last expression in the catch block (or blocks). Contents of the finally block do not affect the result of the expression.

## `fail(): Nothing`
`Nothing` is like Optional<T> in java
```
fun fail(message: String): Nothing {
    throw IllegalArgumentException(message)
}
    
val name: String = user.name ?: fail("No name found")
```

**Details: [Kotlin Exception](https://kotlinlang.org/docs/reference/exceptions.html)**

