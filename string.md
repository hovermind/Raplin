* a sequence of characters
* all strings are objects of `String` class
* immutable
```
val myString: String
myString = "Howdy"

val myStr = "Hey there!"
```

## Accessing characters
```
val myString = "Hey there!"

val y = myString[2]

myString[2] = 'Y' // // Error! String is immutable
```

## Iterating
```
val myString = "Hovermind!"

for (ch in myString) {
    println(ch)
}
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
