<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->
# Table of Contents
- [Values](#values)
- [Variables](#variables)
- [Functions](#functions)
- [Anonymous Functions](#anonymous-functions)
- [Partial Application](#partial-application)
- [Curried Functions](#curried-functions)
- [Variable length arguments](#variable-length-arguments)

<!-- TOC end -->

<!-- TOC --><a name="values"></a>
## Values
Values are constants that cannot be mutated once assigned. Most commonly used in Scala.

```scala
val two = 1+1
```

<!-- TOC --><a name="variables"></a>
## Variables
Variables are values that can be mutated throughout its lifetime, although not recommended to be used.

```scala
var fruit = "apple"
```

<!-- TOC --><a name="functions"></a>
## Functions
Any functions can be created with the keyword `def`

```scala
def addTwoNums(a: Int, b: Int): Int = {
  val sum = a + b
  sum
}

println(addTwoNums(3, 4))
```

The last value is assumed to be the return value. A function can have no arguments as well.

<!-- TOC --><a name="anonymous-functions"></a>
## Anonymous Functions
You can have anonymous functions (Functions with no name) in Scala as well.

```scala
(x: Int) => x + 1
```

You can pass anonymous functions as arguments or save them as values as well.

```scala
val addOne = (x: Int) => x + 1

println(addOne(2))
```

<!-- TOC --><a name="partial-application"></a>
## Partial Application
You can partially apply a function with a underscore, which returns another function. Basically returning a placeholder that can be filled later. For example

```scala
def adder(m: Int, n: Int) = m + n
val add2 = adder(2, _:Int) // Create a partial

println(add2(3)) // 5, supplying the placeholder.
```

<!-- TOC --><a name="curried-functions"></a>
## Curried Functions
Similar to partial application as above, curried functions allow to apply operands to the functions at different stages in the application.

```scala
def multiply(m: Int)(n: Int): Int = m * n
val timesTwo = multiply(2)_ // One half
println(timesTwo(3)) // 6, apply the other half.
```

You can also curry an already existing function.

```scala
// Taking the above adder
val curriedAdd = (adder _).curried
val addTwo = curriedAdd(2)

println(addTwo(2)) // 4
```

<!-- TOC --><a name="variable-length-arguments"></a>
## Variable length arguments
There is a special syntax for methods that can take parameters of a repeated type.

```scala
def capitalizeAll(args: String*) = {
    args.map { arg =>
        arg.capitalize
    }
}
```

[Prev Page](./1_what_is_scala.md) 

[Next Page](./3_classes)