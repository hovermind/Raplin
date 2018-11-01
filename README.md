**This is kinda Kotlin cheatsheet & intended for anyone who wants to learn Kotlin and is already good at (any) programming language i.e. C#, Java**

[AIA](https://drive.google.com/folderview?id=0B2KMjffVzeSAN3d1R0N1NV9HNU0l)
## <a name="#toc">TOC
* [data types and variables](https://github.com/hovermind/Raplin/blob/master/data_types_and_variables.md)
* [literals and constant](https://github.com/hovermind/Raplin/blob/master/literals_and_constant.md)
* [printing and comment](https://github.com/hovermind/Raplin/blob/master/printing_and_comment.md)
* [type related](https://github.com/hovermind/Raplin/blob/master/type_related.md)
* [optional type & null safety](https://github.com/hovermind/Raplin/blob/master/optional_type.md)
* [type casting](https://github.com/hovermind/Raplin/blob/master/type_casting.md)
* [operators](https://github.com/hovermind/Raplin/blob/master/operators.md)
* [branching](https://github.com/hovermind/Raplin/blob/master/branching.md)
* [looping](https://github.com/hovermind/Raplin/blob/master/looping.md)
* [string](https://github.com/hovermind/Raplin/blob/master/string.md)
* [function](https://github.com/hovermind/Raplin/blob/master/function.md)
* [exception](https://github.com/hovermind/Raplin/blob/master/exception.md)
* [data structure](#)
    * [array](#)
    * [list](#)
    * [map](#)
    * [see](#)
    * [stack](#)
    * [queue](#)
* [enum](#)
* [structure](#)
* [class](#)
* [interface](#)
* [deep dive](#)
    * [idioms](https://kotlinlang.org/docs/reference/idioms.html)
    * [data class](#)
    * [tuple](https://github.com/hovermind/Raplin/blob/master/tuple.md)
* [io](#)
* [extensions](#)
* [multithreading](#)
* [async](#)

# <a name="#function"></a>Function
Use ```fun``` keyword to define function.
```
fun sum(a: Int, b: Int): Int {
    return a + b
}
```
#### Single-Expression functions 
```
// Function with an expression body
fun double(x: Int): Int = x * 2
```
The return type is optional when this can be inferred by the compiler
```
fun double(x: Int) = x * 2       // return type is inferred from righ side expression
```
#### `Unit` return type
`Unit` in Kotlin corresponds to the `void` type in other languages. `Unit` is a singleton object. It has only one value: `Unit`
```
fun printSum(a: Int, b: Int): Unit {
    println("sum of $a and $b is ${a + b}")
}
```

`Unit` return type can be omitted:
```
fun printSum(a: Int, b: Int) {
    println("sum of $a and $b is ${a + b}")
}
```

#### Named Arguments
Named argument is optional in Kotlin. Parameter names can be used for clarity during function call.
```
fun sum(a: Int, b: Int): Int {
    return a + b
}

// function call
val result = sum(a = 10, b = 20)
```
When a function is called with both positional & named arguments, all the positional arguments should be placed before the first named one i.e. `f(1, y = 2)` is allowed, but `f(x = 1, 2)` is not.
```
fun sum(a: Int, b: Int, c: Int): Int {
    return a + b + c
}

// function call
val result = sum(5, 10, c = 20)   // a = 5, b = 10
```
#### Default Parameters
Default values are defined using the `=` after `type` along with the value.
```
fun sum(a: Int, b: Int = 10): Int {
    return a + b
}

// function call
val result = sum(5)    // a = 5, b == defualt == 10
```
Overriding methods always use the same default parameter values as the base method & therefore the default parameter values must be omitted from the signature in sub class
```
open class A {
    open fun foo(i: Int = 10) { ... }
}

class B : A() {
    override fun foo(i: Int) { ... }  // no default value allowed because default value of i is 10 (from super class A)
}
```
#### Passing Lambda
Lambda can be passed to a function call outside the parentheses (as like Groovy)
```
fun foo(bar: Int, mathFunction: (Int) -> Int) {
    println("Math Function Result: ${mathFunction(bar)}")
}

// function call
val result = foo(10) { x ->
    x * x  // implicit return from lambda: last statement is return statement
}

```
#### Variable number of arguments
- only one parameter may be marked as `vararg`
- inside a function a `vararg` parameter of type `T` is visible as an `array` of `T`
```
fun <T> asList(vararg ts: T): List<T> {
    val result = ArrayList<T>()
    
    // ts is type of Array<out T>
    // precess here
    
    return result
}
```
Normally the last one is marked with `vararg` modifier. If `vararg` is not last parameter (i.e. lambda is last parameter), then use parameter name for `vararg` during function call.

Use the spread operator (prefix the array name with \*) to pass its contents to the function as variable arguments.
```
val list = asList(-1, 0, *a, 4)
```
#### Top level function
In Kotlin functions can be declared at top level in a file, meaning you do not need to create a class to hold a function

#### Local Functions
Kotlin supports local functions, i.e. a function inside another function. Local functions are closures means local function has access to the outer function variables & parameter (even the outer function has returned)
```
fun foo(radius: Int): Double {
    val PI = 3.1416
    // loacl fucntion has access to both PI & bar parameter
    fun area(): Double{
        return  PI * radius * radius;
    }
    
    return area()
}
```

#### Infix notation
Functions can also be called using infix notations when:
 - They are member functions or extension functions
 - They have a single parameter
 - They are marked with the infix keyword
```
// Define extension to Int
infix fun Int.shl(x: Int): Int {
    ...
}

// call extension function using infix notation
val result = 1 shl 2    // same as 1.shl(2)
```
#### Generic Functions
```
fun <T> singletonList(item: T): List<T> {
    // type T is determined during function call depending on arguments
}
```
#### Higher-Order Functions
A higher-order function is a function that takes functions as parameters, or returns a function. The parameter of a higher order function is delegate / function type & the argument is lambda.
```
fun foo(bar: Int, mathFunction: (Int) -> Int) {
    println("Math Function Result: ${mathFunction(bar)}")
}

// function call
val result = foo(10) { x ->
    x * x  // implicit return from lambda: last statement is return statement
}
```

