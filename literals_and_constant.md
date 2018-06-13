## Constants
No keyword for constant, `val` is used for both constant and read-only variables
```
val PI = 3.1416; // type inferred & Double by default
```

## Literals
**default:** `Int` & `Double` (no suffix needed)   

**Type suffix:**   
* `Long` => L 
* `Float` => F
```
var myLong = 100000000005L
var myFloat = 3.1416238458152F
```
**Type prefix**
* Hexadecimal => 0x_ (starts with 0x)
* Binary => 0b_ (starts with 0b)

**Underscores in numeric literals**
```
val oneMillion = 1_000_000
val creditCardNumber = 1234_5678_9012_3456L
val socialSecurityNumber = 999_99_9999L
val hexBytes = 0xFF_EC_DE_5E
val bytes = 0b11010010_01101001_10010100_10010010
```
