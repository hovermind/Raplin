## Kotlin class
```kotlin
class ClassName {
    // property
    // member function
    ... .. ...
}
```

When class is defined, only the specification for the object is defined; no memory or storage is allocated.
To access members defined within the class, you need to create objects
```kotlin
class Lamp {

    // property (data member)
    private var isOn: Boolean = false

    // member function
    fun turnOn() {
        isOn = true
    }

    // member function
    fun turnOff() {
        isOn = false
    }
}
```

**Creating object (class instance)**
```kotlin
val lamp = Lamp()
lamp.turnOn()
```

(Class Members) Classes can contain:
* Constructors and initializer blocks
* Functions
* Properties
* Nested and Inner Classes
* Object Declarations


## Constructor
Kotlin has two types of constructor:
* primary constructor
* secondary constructor

#### Primary constructor
```kotlin
class Book constructor(title: String, isbn: Long) {

    var title: String
    var isbn: Long
 
	// init block will be called when class instance is created
    init {
       this.title = title
       this.isbn = isbn
    }
}
```    

**syntactic sugar - the properties can be declared in the primary constructor**
```
class Book constructor(var title: String, var isbn: Long)

class Book constructor(var title: String, var isbn: Long = 2128300558) # default value for isbn
```

The properties declared in the primary constructor can be mutable (`var`) or read-only (`val`). If no access modifier / annotation used, the we can ommit constructor keyword for primary constructor
```kotlin
class Book(var title: String, var isbn: Long)

class Book(var title: String, var isbn: Long = 2128300558) # default value for isbn
```

**Notes:**
* if a non-abstract class does not declare any constructors (primary or secondary), it will have a generated primary constructor with no arguments. The visibility of the constructor will be public.
* if you do not want your class to have a public constructor, you need to declare an empty primary constructor with non-default visibility
```kotlin
class DontCreateMe private constructor () { ... }
```
* if all of the parameters of the primary constructor have default values, the compiler will generate an additional parameterless constructor which will use the default values. This makes it easier to use Kotlin with libraries such as Jackson or JPA that create class instances through parameterless constructors. 

#### Secondary constructor
Secondary constructors are prefixed with `constructor` keyword:
```kotlin
class Car(val name: String, val plateNo: String) {

    var new: Boolean? = null
    var colour: String = ""
 
    constructor(name: String, plateNo: String, new: Boolean) : this(name, plateNo) {
        this.new = new
    }
 
    constructor(name: String, plateNo: String, new: Boolean, colour: String ) : this(name, plateNo, new) {
        this.colour = colour
    }
}
```

**Notes:** 
* If the class has a primary constructor, each secondary constructor needs to delegate to the primary constructor, either directly or indirectly through another secondary constructor
* `this()`: reusing constructor or delegating to primary constructor


## Init
* primary constructor cannot contain any code. Initialization code can be placed in initializer blocks, which are prefixed with the `init` keyword. `init` code block is executed immediately when the class instance is created
* code in initializer blocks effectively becomes part of the primary constructor and  the code in all initializer blocks is executed before the secondary constructor
* if the class has no primary constructor, the delegation still happens implicitly, and the initializer blocks are still executed:
* parameters of the primary constructor can be used in the initializer blocks
* there can be more than one `init` block. The initializer blocks are executed in the same order as they appear in the class body
```kotlin
class InitOrderDemo(name: String) {

    val firstProperty = "First property: $name".also(::println)
    
    init {
        println("First initializer block")
    }
    
    val secondProperty = "Second property: ${name.length}".also(::println)
    
    init {
        println("Second initializer block")
    }
}
```

## Access modifiers
* `private` - visible (can be accessed) from inside the class only.
* `public` - visible everywhere.
* `protected` - visible to the class and its subclass.
* `internal` - any client inside the module can access them.

## Properties
In Kotlin, there is no concept of a field; instead, it uses the concept of "properties". 
An amazing thing is that the getters and setters for these properties are auto-generated for us under the hood by the Kotlin compiler. 
Properties are public by default

**Creating custom properties**
```kotlin
class Book (val isbn: Long) {

    var title = "default value"
    set(value) {
        if (!value.isNotEmpty()) {
            throw IllegalArgumentException("Title must not be empty")
        }
        field = value
    }
    get() {
        return field.toUpperCase()
    }
}
```

## Inheritance
* all classes implicitly inherits from `Any`
* `Any` is not `java.lang.Object` in particular, it does not have any members other than `equals()`, `hashCode()` and `toString()`
* if the derived class has a primary constructor, the base class can (and must) be initialized right there, using the parameters of the primary constructor
```kotlin
open class Base(p: Int)

class Derived(p: Int) : Base(p)
```
* If the class has no primary constructor, then each secondary constructor has to initialize the base type using the super keyword, or to delegate to another constructor which does that
```kotlin
class MyView : View {
    constructor(ctx: Context) : super(ctx)

    constructor(ctx: Context, attrs: AttributeSet) : super(ctx, attrs)
}
```
* [Overriding Methods](https://kotlinlang.org/docs/reference/classes.html#overriding-methods)
* [Overriding Properties](https://kotlinlang.org/docs/reference/classes.html#overriding-properties)
* [Calling the superclass implementation](https://kotlinlang.org/docs/reference/classes.html#calling-the-superclass-implementation)
* [Overriding Rules](https://kotlinlang.org/docs/reference/classes.html#overriding-rules)

## More
* [Abstract Classes](https://kotlinlang.org/docs/reference/classes.html#abstract-classes)
* [Companion Objects](https://kotlinlang.org/docs/reference/object-declarations.html#companion-objects)


