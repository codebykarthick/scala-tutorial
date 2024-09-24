<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->
# Table of Contents
- [Extended Basics Part 2](#extended-basics-part-2)
   * [Pattern Matching](#pattern-matching)
   * [Case Classes](#case-classes)
   * [Exceptions](#exceptions)

<!-- TOC end -->

<!-- TOC --><a name="extended-basics-part-2"></a>
# Extended Basics Part 2
<!-- TOC --><a name="pattern-matching"></a>
## Pattern Matching
Scala has one of the most flexible pattern matchers in all languages.

```scala
val times = 1

// Matching directly
times match {
    case 1 => "one"
    case 2 => "two"
    case _ => "some other number" // default case.
}

// Matching with a guard
times match {
    case i if i == 1 => "one"
    case i if i == 2 => "two"
    case _ => "Some other number"
}

// Matching different types
o match {
    case i: Int if i < 0 => i - 1
    case i: Int => i + 1
    case d: Double if d < 0.0 => d - 0.1
    case text: String => text + "s"
}

// You can also match on class members
// Assuming calc is an instance of Calculator with members brand and model
calc match {
    case _ if calc.brand == "HP" && calc.model == "20B" => "financial"
}
```

<!-- TOC --><a name="case-classes"></a>
## Case Classes
Scala has a nice shorthand for the last match above, with respect to classes, called Case Classes. They automatically get good equal comparison and toString methods. **`new` keyword is not needed to construct an instance of a case class.**

```scala
case class Calculator(brand: String, model: String)

val hp20b = Calculator("HP", "20b")
val anotherHp20b = Calculator("HP", "20b")
hp20b == anotherHp20b // true
```

Match becomes much easier as well.

```scala
hp20b match {
    case Calculator("HP", "20b") => "financial"
    case Calculator(_, _) => "Unknown"
}
```

<!-- TOC --><a name="exceptions"></a>
## Exceptions
Exceptions are available in Scala with pattern matching. `try`s are also expression oriented like methods and functions are.

```scala
val result = try {
    remoteCalculatorService.add(1, 2)
} catch {
    case e: ServerIsDownException => log.error(e, "The remote calculator is down")
    0 // returned to result
} finally {
    // Runs nonetheless if try or catch is executed.
    remoteCalculatorService.close()
}
```

[Prev Page](./6_extended_basics.md) 

The basics section is over, we will next cover the basic and advanced data structures next, follow next when you are ready!

[Next Page](../collections/8_basic_ds.md)