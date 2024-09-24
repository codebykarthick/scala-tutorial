<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->
# Table of Contents
- [Classes](#classes)
- [Constructor](#constructor)
- [Method vs Function](#method-vs-function)
- [Inheritance](#inheritance)
- [Overloading methods](#overloading-methods)
- [Abstract Classes](#abstract-classes)

<!-- TOC end -->

<!-- TOC --><a name="classes"></a>
## Classes
Classes are a self-contained blueprint with its own members and functions.

```scala
class Calculator {
    val brand: String = "HP"
    def add(m: Int, n: Int) = m + n
}

// Initialise an object of the class
val calc = new Calculator

println(calc.add(1,2)) // 3
println(calc.brand) // HP
```

<!-- TOC --><a name="constructor"></a>
## Constructor
Used to assign values during instance creation.

```scala
class Calculator(brand: String) {
  /**
   * A constructor.
   */
  val color: String = if (brand == "TI") {
    "blue"
  } else if (brand == "HP") {
    "black"
  } else {
    "white"
  }

  // An instance method.
  def add(m: Int, n: Int): Int = m + n
}
```

<!-- TOC --><a name="method-vs-function"></a>
## Method vs Function
Although both are used interchangably, both bear different meanings.

* Method: Member of a class, trait or object, defined using the `def` keyword. It is associated with that class.

* Function: Complete object that is assigned to a variable, passed around or returned from other functions.

<!-- TOC --><a name="inheritance"></a>
## Inheritance
A new class can inherit an existing class and therefore gets the properties of the base class.

```scala
class ScientificCalculator(brand: String) extends Calculator(brand) {
  def log(m: Double, base: Double) = math.log(m) / math.log(base)
}
```

<!-- TOC --><a name="overloading-methods"></a>
## Overloading methods
You can have multiple methods with the same but with different signature.

```scala
class EvenMoreScientificCalculator(brand: String) extends ScientificCalculator(brand) {
  def log(m: Int): Double = log(m, math.exp(1))
}
```

<!-- TOC --><a name="abstract-classes"></a>
## Abstract Classes
Classes that define some methods but do not implement them, instead subclasses that extend these abstract classes implement them.

```scala
abstract class Shape {
    def area(): Int
}

// Subclass
class Circle(r: Int) extends Shape {
    def area(): Int = r * r * 3
}
```

[Prev Page](./2_var_functions.md) 

[Next Page](./4_traits.md)