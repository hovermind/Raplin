## String
* a sequence of characters
* all strings are objects of `String` class
* immutable

`CharSequence`(interface) is a readable sequence of char values. This interface provides uniform, read-only access to many different kinds of char sequences. Mutability is not enforced by this interface. String class implements the `CharSequence`, therefore, Strings are CharSequences.

```kotlin
var foo: String
foo = "Foo"

val foo: String = "Foo"
val foo = "Foo"  // type inference

var emptyString = String() // empty String
```

#### Chars in String
```kotlin
// iterating chars
for (ch in myString) {
    println(ch)
}

// accessing chars
val foo = "Foo"
val f = foo[0]
val f = foo.get(0)

// immutable
foo[0] = 'f'  // ERROR
```

## Raw string
`"""` used for raw string & multi-line string
```kotlin
fun main(args: Array<String>) {
    val myString = """
        println() function
    """
    print(myString)
}
// output: println() function
```
**Nate:** `trimMargin()` can be used to remove spaces

## Interpolation
* Variable: `print("Total score for $name is $score")`
* Class propery: `"${person.name}"`
* Expression:  `"${1 * 2}"`

**Note:** raw string can also be interpolated

## Concatenation
* Interpolation : `val z = "$x $y"`
* `+` / `plus()`: `val z = x + y` or `val z = x.plus(y)`
* [StringBuilder](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/-string-builder/) :
```kotlin
val h = "Hello"
val w = "World"

val sb = StringBuilder()
sb.append(h)
sb.append(w)

val hw = sb.toString()
print(hw)              // HelloWorld
```
## Split
**See:** [split()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/split.html)

## Join
**See:** [joinToString()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/join-to-string.html)

## Excape sequence
Here is a list of escape characters supported in Kotlin:
* `\t` - Inserts tab
* `\b` - Inserts backspace
* `\n` - Inserts newline
* `\r` - Inserts carriage return
* `\'` - Inserts single quote character
* `\"` - Inserts double quote character
* `\\` - Inserts backslash
* `\$` - Inserts dollar character

## String Properties and Functions
* `length` - returns the length of character sequence of an string.
* `compareTo()` - compares this String (object) with the specified object. Returns 0 if the object is equal to the specfied object.
* `get()` - returns character at the specified index.You can use index access operator instead of get function as index access operator internally calls get function.
* `plus()` - returns a new string which is obtained by the concatenation of this string and the string passed to this function. You can use + operator instead of plus function as + operator calls plus function under the hood.
* `subSequence()` - returns a new character sequence starting at the specified start and end index.

**See:** [Kotlin String Class](http://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/)

## String Equality
There are two types of equality checkers:
* Referential Equality: Checks if the pointers for two objects are the same. `===` operator is used
* Structural Equality : Checks if the contents of both the objects are equal. `==` is used
