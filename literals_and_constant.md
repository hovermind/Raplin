## Constants
* No keyword for constant
* `val` is used for both constant and read-only variables
```kotlin
val PI = 3.1416;
```

## Literals
* `Int` is default for integer variables
* `Double` is default for floating point variables
* `String` can not be `null`

##### Type suffix
| Type | suffix |example|
|------|--------|-------|
|  `Int` | no suffix (default) | val x = 10
| `Long` | L | val x = 10L |
| `Float`| F | val x = 10.0F |
| `Double` | no suffix (default) | val x = 10.0 |

##### Type prefix
| number system | prefix | example |
|---------------|--------|---------|
| Hexadecimal |  0x... | val hexBytes = 0xFFECDE5E |
| Binary | 0b... | val bytes = 0b11010010 |

## Underscores in numeric literals
```kotlin
val oneMillion = 1_000_000
val creditCardNumber = 1234_5678_9012_3456L
val socialSecurityNumber = 999_99_9999L
val hexBytes = 0xFF_EC_DE_5E
val bytes = 0b11010010_01101001_10010100_10010010
```
