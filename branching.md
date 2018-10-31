## IF
* in Kotlin, if is an expression (it returns a value). Therefore there is no ternary operator (`condition ? ... : ...`), because ordinary if works fine in this role.
* if branches can be blocks, and the last expression is the value of a block
* when used as an expression rather than a statement, an else branch is required
```
var max: Int = 0
if (a > b) {
    max = a
} else {
    max = b
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
**Note: Kotlin does not have `else...if`, use `when` instead**

## When
* when replaces the `switch` (and `else...if`) operator of C-like languages
* when can be used either as an expression or as a statement
* if when is used as an expression, the else branch is mandatory
* else branch is evaluated if none of the other branch conditions are satisfied (default)
```
when (x) {
    1 -> print("x == 1")
    2 -> print("x == 2")
    else -> {
        print("x is neither 1 nor 2")
    }
}
```
`when(x)` cases:
* multiple cases: `1, 2, 3 ->`
* arbitrary expressions: `parseInt(strIntVal) ->`
* in range & not in range: `in 1...10 ->`, `!in 1...10 ->`
* type check: `is String ->`, `!is String ->`

when can also be used as a replacement for an if-else if chain. If no argument is supplied, the branch conditions are simply boolean expressions, and a branch is executed when its condition is true:
```
when {
    x.isOdd() -> print("x is odd")
    x.isEven() -> print("x is even")
    else -> print("x is funny")
}
```
