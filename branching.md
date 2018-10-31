# TOC
* [If](/branching.md#if)
* [When](/branching.md#when)
* [When as expression](/branching.md#when-as-expression)
* [When cases](/branching.md#when-cases)
* [Whe Expression with a case that throws an exception](/branching.md#whe-expression-with-a-case-that-throws-an-exception)
* [When as else-if](/branching.md#when-as-else-if)

## IF
* if is an expression (returns a value). Therefore there is no ternary operator
* when used as an expression rather than a statement, an else branch is required
* if branches can be blocks, and the last expression is the value of a block
```
if () {
} else if {
} else {
}
 
// As expression 
val max = if (a > b) a else b

// block
val max = if (a > b) {
    print("Max is a")
    a
} else {
    print("Max is b")
    b
}
```

## When
* when replaces the `switch` operator of C-like languages
* no break statements are needed in the end of each case block
* else branch is evaluated if none of the other branch conditions are satisfied (default)
* when can be used either as an expression or as a statement
* if when is used as an expression, the else branch is mandatory
```
when (x) {
    1 -> print("x == 1")
    2 -> print("x == 2")
    else -> {
        print("x is neither 1 nor 2")
    }
}
```

## When as expression
```
val objectType = when {
    fileType === UnixFileType.L -> "l"
    fileType === UnixFileType.HYPHEN_MINUS -> "-"
    fileType === UnixFileType.D -> "d"
    else -> "unknown file type"
}
```

## When cases
* **multiple cases:** `1, 2, 3 ->`
* **arbitrary expressions:** `parseInt(strIntVal) ->`
* **in range & not in range:** `in 1...10 ->`, `!in 1...10 ->`
* **type check:** `is String ->`, `!is String ->`

## Whe Expression with a case that throws an exception
```
val result: Boolean = when (fileType) {
    UnixFileType.HYPHEN_MINUS -> true
    else -> throw IllegalArgumentException("Wrong type of file")
}
```

## When as else-if
when can also be used as a replacement for an `if-else if` chain. If no argument is supplied, the branch conditions are simply boolean expressions, and a branch is executed when its condition is true:
```
when {
    x.isOdd() -> print("x is odd")
    x.isEven() -> print("x is even")
    else -> print("x is funny")
}
```
