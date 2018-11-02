# TOC
* [Exception](/exception.md#exception)
* [Try expression](/exception.md#try-expression)
* [fail(): Nothing](/exception.md#fail-nothing)

## Exception
* `try-catch` works pretty much the same way as it does in Java
* to throw an exception object, use the throw-expression
```kotlin
try {
    // some code
}
catch (e: SomeException) {
    // handler
}
finally {
    // optional finally block
}


throw Exception("Foo Exception")
```

## Try expression
* in kotlin, try is an expression, i.e. it may have a return value
* the returned value of a try-expression is either the last expression in the try block or the last expression in the catch block
* contents of the finally block do not affect the result of the expression
```kotlin
val a: Int? = try { parseInt(input) } catch (e: NumberFormatException) { null }
```

## [`fail(): Nothing`](https://medium.com/@aramaki/how-kotlin-can-help-us-with-error-handling-4c2265c9b50)
* In Kotlin, throw returns a value of type Nothing
* `Nothing` is the type that inherits from all user-defined and built-in types (`Nothing` is like Optional\<T\> in java)
```kotlin
fun fail(message: String): Nothing {
    throw IllegalArgumentException(message)
}
    
val name: String = user.name ?: fail("No name found")
```

**Details: [Kotlin Exception](https://kotlinlang.org/docs/reference/exceptions.html)**

