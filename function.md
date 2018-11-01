# TOC
* [Single expression function](/function.md#single-expression-function)
* [Unit return type](https://github.com/hovermind/Raplin/blob/master/function.md#unit-return-type)
* [Named arguments](/function.md#named-arguments)
* [Default parameter](/function.md#default-parameter)
* [Variable number of arguments](/function.md#variable-number-of-arguments)
* [Generic function](/function.md#generic-function)
* [Local function](/function.md#local-function)
* [Infix notation](/function.md#infix-notation)
* [Higher order function](/function.md#higher-order-function)
* [Passing lambda](/function.md#passing-lambda)


## Function
Use `fun` keyword to define function.
```kotlin
fun sum(a: Int, b: Int): Int {
    return a + b
}
```
## Single expression function
Function with an expression body
```kotlin
fun double(x: Int): Int = x * 2

// return type is optional when return type can be inferred from righ side expression
fun double(x: Int) = x * 2
```

## Unit return type
`Unit` in Kotlin corresponds to the `void` type in other languages. `Unit` is a singleton object. It has only one value: `Unit`
```kotlin
fun printSum(a: Int, b: Int): Unit {
    println("sum of $a and $b is ${a + b}")
}

// Unit return type can be omitted:
fun printSum(a: Int, b: Int) {
    println("sum of $a and $b is ${a + b}")
}
```

## Named arguments
Named argument is optional in Kotlin. Parameter names can be used for clarity during function call.
```kotlin
fun sum(a: Int, b: Int): Int {
    return a + b
}

// function call
val result = sum(a = 10, b = 20)
```
**Note:** When a function is called with both positional & named arguments, all the positional arguments should be placed before the first named one i.e. `f(1, y = 2)` is allowed, but `f(x = 1, 2)` is not.

## Default parameter
Default values are defined using the `=` after `type` along with the value
```kotlin
fun sum(a: Int, b: Int = 10): Int {
    return a + b
}

// function call
val result = sum(5)    // a = 5, b == defualt == 10
```
Overriding methods always use the same default parameter values as the base method & therefore the default parameter values must be omitted from the signature in sub class
```kotlin
open class A {
    open fun foo(i: Int = 10) { ... }
}

class B : A() {
    override fun foo(i: Int) { ... }  // no default value allowed because default value of i is 10 (from super class A)
}
```

## Variable number of arguments
- only one parameter may be marked as `vararg`
- inside a function a `vararg` parameter of type `T` is visible as an `array` of `T`
```kotlin
fun <T> asList(vararg ts: T): List<T> {
    val result = ArrayList<T>()
    
    // ts is type of Array<out T>
    // precess here
    
    return result
}
```
**Note:** Normally the last one is marked with `vararg` modifier. If `vararg` is not last parameter (i.e. lambda is last parameter), then use parameter name for `vararg` during function call

Use the spread operator (prefix the array name with \*) to pass its contents to the function as variable arguments.
```kotlin
val list = asList(-1, 0, *a, 4)
```

## Generic function
```kotlin
fun <T> singletonList(item: T): List<T> {
    // type T is determined during function call depending on arguments
}
```

## Local function
Kotlin supports local functions, i.e. a function inside another function. Local functions are closures means local function has access to the outer function variables & parameter (even the outer function has returned)
```kotlin
fun foo(radius: Int): Double {
    val PI = 3.1416
    
    // loacl fucntion has access to both PI & radius parameter
    fun area(): Double{
        return  PI * radius * radius;
    }
    
    return area()
}
```

## Top level function
In Kotlin functions can be declared at top level in a file, meaning you do not need to create a class to hold a function

## Infix notation
Functions can also be called using infix notations when:
 - They are member functions or extension functions
 - They have a single parameter
 - They are marked with the infix keyword
```kotlin
// Define extension to Int
infix fun Int.shl(x: Int): Int {
    ...
}

// call extension function using infix notation
val result = 1 shl 2    // same as 1.shl(2)
```

## Higher order function
A higher-order function is a function that takes functions as parameters, or returns a function. The parameter of a higher order function is delegate / function type & the argument is lambda.
```kotlin
fun foo(bar: Int, mathFunction: (Int) -> Int) {
    println("Math Function Result: ${mathFunction(bar)}")
}

// function call
val result = foo(10) { x ->
    x * x  // implicit return from lambda: last statement is return statement
}
```

## Passing lambda
Lambda can be passed to a function call outside the parentheses (as like Groovy)
```kotlin
fun foo(bar: Int, mathFunction: (Int) -> Int) {
    println("Math Function Result: ${mathFunction(bar)}")
}

// function call
val result = foo(bar: 10) { x ->
    x * x  // implicit return from lambda: last statement is return statement
}
```
