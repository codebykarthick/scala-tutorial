<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->
# Table of Contents
- [Basic Data Structures](#basic-data-structures)
   * [Arrays](#arrays)
   * [Lists](#lists)
   * [Sets](#sets)
   * [Tuple](#tuple)
   * [Maps](#maps)
   * [Option](#option)

<!-- TOC end -->

<!-- TOC --><a name="basic-data-structures"></a>
# Basic Data Structures
Scala provides a lot of nice data structures.

<!-- TOC --><a name="arrays"></a>
## Arrays
Arrays are same datatype, preserve order, allows duplicates and are mutable.

```scala
val numbers = Array(1, 2, 3, 4, 5)
numbers(3) // Note the brackets for indexing.
```

<!-- TOC --><a name="lists"></a>
## Lists
Lists same as arrays in most properties except they are immutable.

```scala
val numbers = List(1, 2, 3, 4, 5)
numbers(3) = 10 // Not allowed
```

<!-- TOC --><a name="sets"></a>
## Sets
Do not preserve order and have no duplicates

```scala
val numbers = Set(1, 2, 3, 4, 5, 1, 2, 3, 4, 5) // Has only 1, 2, 3, 4, 5
```

<!-- TOC --><a name="tuple"></a>
## Tuple
Groups together simple logical items without needing a class

```scala
val hostPort = ("localhost", 8080)

hostPort._1 // "localhost", tuples are 1 indexed.
hostPort._2 // 8080
```

They also have good matchers

```scala
hostPort match {
    case ("localhost", port) => ...
    case (host, port) => ...
}
```

They have a nice shorthand to create for 2 value tuples

```scala
1 -> 2 // equivalent to (1, 2)
```

<!-- TOC --><a name="maps"></a>
## Maps
Holds data in key value pairs, can be seen as an array of 2 tuples

```scala
val immutableMap = Map("apple" -> 1, "banana" -> 3)

immutableMap.get("apple") // Returns an option type, defined below
```

<!-- TOC --><a name="option"></a>
## Option
Option is a container for any datatype that may or may not hold a value.

```scala
trait Option[T] {
  def isDefined: Boolean
  def get: T
  def getOrElse(t: T): T
}
```

It has two subclasses called Some[] and None. Some is returned if there is a value for that key and None is returned when there is no value.

```scala
val value = immutableMap.get("apple")

if(value.isDefined) {
    value.get * 2 // actually accesses the value.
}

// Can also use
value.getOrElse(0) // returns 0 is value is none.
```

Pattern matching naturally matches an Option

```scala
value match {
    case Some(n) => n * 2
    case None => 0
}
```

[Prev Page](../basics_extended/7_extended_basics_p2.md) 

[Next Page](./9_func_combinators.md)