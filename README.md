**This is kinda Kotlin cheatsheet & intended for anyone who wants to learn Kotlin and is already good at (any) programming language i.e. C#, Java**

# <a name="#toc">TOC
- [Data Types & Variables](#data-types)
- [Constant](#constant)
- [Type Inference](#type-inference)
- [Tuple](#tuple)
- [String](#string)
- [Type Alias](#type-alias)
- [Operators](#operators)
- [Optional Type](#optional-type)
- [Optional Binding](#optional-binding)
- [Guard (Early Exit)](#guard)
- [Type Casting](#type-casting)
- [Looping](#looping)
- [Branching](#branching)
- [Array](#array)
- [Dictionary](#dictionary)
- [Set](#set)
- [Function](#function)
- [Clouser](#clouser)
- [Function Type](#function-type)
- [Nested Function](#nested-function)
- [Enum](#enum)
- [Structure](#structure)
- [Class](#class)
- [Initializer](#initializer)
- [Properties](#properties)
- [Static vs Class Type](#static-vs-class-type)
- [Access Modifier](#access-modifier)
- [Protocol](#protocol)
- [Inheritance](#inheritance)
- [Subscript](#subscript)
- [Extension](#extension)
- [Generic](#generic)
- [Exception](#exception)
- [Advanced Operator](#advanced-operator)
- [Misc](#misc)

# <a name="#function"></a>Function
Use ```fun``` keyword to define function.
```
fun sum(a: Int, b: Int): Int {
    return a + b
}
```
Function with an expression body
```
fun sum(a: Int, b: Int) = a + b       // return type is inferred from righ side expression
```

```Unit``` in Kotlin corresponds to the ```void``` type in other languages. ```Unit``` is a singleton object. It has only one value: ```Unit```
```
fun printSum(a: Int, b: Int): Unit {
    println("sum of $a and $b is ${a + b}")
}
```

```Unit``` return type can be omitted:
```
fun printSum(a: Int, b: Int) {
    println("sum of $a and $b is ${a + b}")
}
```

## Named Arguments
Named argument is optional in Kotlin. Parameter names can be used for clarity during function call.
```
fun sum(a: Int, b: Int): Int {
    return a + b
}

// function call
val result = sum(a = 10, b = 20)
```
When a function is called with both positional & named arguments, all the positional arguments should be placed before the first named one i.e. ```f(1, y = 2)``` is allowed, but ```f(x = 1, 2)``` is not.
```
fun sum(a: Int, b: Int, c: Int = 20): Int {
    return a + b
}

// function call
val result = sum(5, 10)   // a = 5, b = 10, c = defualt (20)
```
## Default Parameters
Default values are defined using the ```=``` after type along with the value.
```
fun sum(a: Int, b: Int = 10): Int {
    return a + b
}

// function call
val result = sum(5)
```






