A regular variable (even string) can not hold `null` (in other languages i.e. C#, Java => string can hold `null`)

```
var name = "Hassan"
name = null               // compilation error
```
If you call a method or access a property on `name`, it's guaranteed not to cause an `NullPointerException`
```
val len = name.length
```
`type?` (i.e. `String?`) allows a variable to hold `null` value
```
var name = "Hassan"
name = null               // OK
```
Now if you want to access the same `length` property, the compiler reports an error
```
val len = name.length    // error: variable 'name' can be null
```
