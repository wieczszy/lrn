Going trough https://docs.scala-lang.org/tour/basics.html

### expressions
computable statements
```scala
1 + 1 // 2
```

### values
Non-mutable results of expressions (cannot be re-assigned).
Declared using `val` keyword.
Referencing a value does not re-compute it.
```scala
val x = 1
println(x) // 1
x = 2 // compilation error
```
Types can be inferred (if not stated) or explicitly stated.
```scala
val x: Int = 1
```
the notation is:
```scala
val valueName = assignedValue
// or
val valueName: Type = assignedValue
```

### variables
Mutable results of expressions.
Declared using `var` keyword.
Type can be inferred or stated.
```scala
var x = 1
var x: Int = 1
```

### blocks
Used to combine expressions with `{}`.
The result of the last expression in the block is the result of the whole block.

```scala
println(
    {
    val x: Int = 1
    x + 1
    }
) // 3
```

### functions
Expressions that have parameters and take arguments.
Can be defined as anonymous or be named.
Functions can have one, multiple parameters or no parameters at all.
```scala
// syntax, [] are optional
[val] [functionName] = (parameter: Type) => expression

// anonymous function with a single parameter
(x: Int) => x + 1

// named function with one parameter
val addOne = (x: Int) => x + 1

// named function with two parameters
val addNumbers = (x: Int, y:Int) => x + y

//named function with no parameters
val foo = () => 42

```

### methods
Methods are defined with `def` keyword.
``scala
// method with one parameter list
def methodName(parameter: Type): ReturnedType = expression

// method with multiple parameter lists
def methodName(parameter1: Type, parameter2: Type)(parameter3: Type): ReturnedType = expression

// method without parameters
def methodName: ReturnedType = expression
``
Methods can be declared as multi-line expressions:
```scala
def squareString(x: Int): String =
    val squared = x * x
    squared.toString
```
The `return` keyword is optional.

### classes
Classes are defined with `class` keyword.
Instances of classes are compared by reference.
```scala
class MyClass(name: String):
    def hello(): Unit =
        println("Hello, " + name)

val foo = MyClass("Joe)
foo.hello() // "Hello, Joe"
```
`Unit` is used to signigy that noting meaningful is returned by the method (similar to `void` in Java).

### case classe
Instances of case classes are immutable and are compared by value.
Case classes are defined with `calse class` keywords.
```scala
// class, compared by reference
class Point(x: Int, y: Int)

val pointA = Point(1, 2)
val pointB = Point(1, 3)
val pointC = Point(1, 2)

println(pointA == pointB) // false
println(pointA == pointC) // false


// case class, compared by value
case class CasePoint(x: Int, y: Int)

val cpointA = CasePoint(1, 2)
val cpointB = CasePoint(1, 3)
val cpointC = CasePoint(1, 2)

println(cpointA == cpointB) // false
println(cpointA == cpointC) // true
```

### objects
Objects are single instances of their own definitions (class singletons).
Objects are defined with `object`.
```scala
object MyObject:
    private var counter = 0
    def create(): Int =
        counter += 1
        counter

val x: Int = MyObject.create()
println(x) // 1

val y: Int = MyObject.create()
println(y) //2
```

### traits
Traits are abstract data types containing fields and methods.
In Scala, a class can only extend one other class but it can extend multiple traits.
Traits are defined with `trait` keyword.
```scala
trait MyTrait:
	def hello(name: String): Unit =
		println("hello, " + name)

class MyClass extends MyTrait

val foo = MyClass()
foo.hello("Joe")
```

### entry point
JVM requires a main method named `main` so the entrypoint for a Scala program is the main method.
In Scala 3 the main method is generated from a method annotated with `@main`.
```scala
@main def main() =
    println("foo")
```
