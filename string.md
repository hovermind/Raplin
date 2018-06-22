* a sequence of characters
* all strings are objects of `String` class
* immutable
```
val myString: String
myString = "Howdy"

val myStr = "Hey there!"
```

## Iterating
```
val myString = "Hovermind!"

for (ch in myString) {
    println(ch)
}
```

## Raw string
`'''`/`"""` used for Raw string & multi-line string
```
fun main(args: Array<String>) {

    val myString = """
    for (character in "Hey!")
        println(character)
    """
    print(myString)
}

// output:
    for (character in "Hey!")
        println(character)
```

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
