<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->
# Table of Contents
- [Extended Basics](#extended-basics)
   * [Apply Methods](#apply-methods)
   * [Objects](#objects)
   * [Functions are Objects](#functions-are-objects)
   * [Packages](#packages)

<!-- TOC end -->

<!-- TOC --><a name="extended-basics"></a>
# Extended Basics
<!-- TOC --><a name="apply-methods"></a>
## Apply Methods
Apply method is a nice shorthand for classes that have one purpose

```scala
class Foo {}

object FooMaker {
    def apply() = new Foo
}

val newFoo = FooMaker() // calls the apply function implicitly

/*
Alternatively
*/

class Bar {
    def apply() = 0
}

val bar = new Bar
println(bar()) // Calling the object like a method invokes the apply
```

<!-- TOC --><a name="objects"></a>
## Objects
Objects are used to hold single instance of a class, instead of creating a class and then instantiating a single instance.

```scala
object Timer {
    var count = 0

    def currentCount(): Long = {
        count += 1
        count
    }
}

Timer.currentCount() // 1
```

<!-- TOC --><a name="functions-are-objects"></a>
## Functions are Objects
Function is a set of traits. A function that has one argument, is an instance of Function 1 trait with the apply function defined.

```scala
// Does what def addOne(m: Int): Int = m + 1
// Function1[firstParam type and return value]
object addOne extends Function1[Int, Int] {
    def apply(m: Int): Int = m + 1
}

println(addOne(1)) // 2
```

As mentioned earlier all methods in a class are methods, methods defined standalone are a function and therefore an object. Shorthand for `extends Function1[Int, Int]` is `extends (Int => Int)`. There are 23 Functions from 0 to 22.

<!-- TOC --><a name="packages"></a>
## Packages
Similar to java packages, this helps in organizing code in a folder.

```scala
package com.codebykarthick.example

object colorHolder {
    val BLUE = "blue"
    val RED = "red"
}

println(com.codebykarthick.example.colorHolder.BLUE) // blue
```

[Prev Page](../basics/5_types.md) 

[Next Page](./7_extended_basics_p2.md)