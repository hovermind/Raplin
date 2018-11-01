# TOC
* [iterates through anything that provides an iterator](/looping.md#iterates-through-anything-that-provides-an-iterator)
* [iterating over a range](/looping.md#iterating-over-a-range)
* [iterating over a range with step](/looping.md#iterating-over-a-range-with-step)
* [iteraring over array](/looping.md#iteraring-over-array)
* [while and do while](/looping.md#while-loop)

## For loop
```
for (item: Int in fooList) {
    // ...
}
```
#### iterates through anything that provides an iterator
Same as`foreach` in C#
```
for (item in collection) {
    print(item)
}
```
#### iterating over a range
```
for (i in 1..3) {
    println(i)
}
```
#### iterating over a range with step
```
for (i in 6 downTo 0 step 2) {
    println(i)
}
```
See: [Range Expression](https://kotlinlang.org/docs/reference/ranges.html)

#### iteraring over array
```
for (i in array.indices) {
    println(array[i])
}

for ((index, value) in array.withIndex()) {
    println("the element at $index is $value")
}
```

## While loop
```
while (testExpression) {
    // ...
}


do {
    // ...
} while (testExpression);
```
