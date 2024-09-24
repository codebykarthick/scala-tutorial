# Funcitonal Combinators
These are usually methods that can be applied on an array or list or other data types to perform some operations.

## map
Evaluates a function over each item in a list, returning another list with the same number of elements.

```scala
val numbers = List(1, 2, 3, 4, 5)

numbers.map(i => i*2) // Returns a list of (2, 4, 6, 8, 10)
```

## foreach
Goes through each element but returns nothing, intended for side-effects in place only.

```scala
numbers.foreach(i => i*2)
```

## filter
Removes any elements in the list and returns the resulting list, where the function you pass evaluates to false (predicate functions).

```scala
numbers.filter(i => i%2 == 0) // returns list with (2, 4) and removes (1, 3, 5)
```

## zip
Aggregates two lists into a single list of pairs

```scala
List(1,2,3).zip(List("a", "b", "c")) // returns List((1, "a"), (2, "b"), (3, "c"))
```

## partition
Splits a list based on a predicate function

```scala
val numbers = List(1,2,3,4,5,6,7,8,9,10)
numbers.partition(_ % 2 == 0) // returns a tuple of two lists even numbers and odd numbers
```

## find
Returns the first element of a list that matches a predicate function

```scala
numbers.find(i => i > 5) // returns an option of 6
```

## drop
Drops the first i elements

```scala
numbers.drop(5) // Returns a list of (6, 7, 8, 9, 10)
```

## dropWhile
Drops elements until predicate function is evaluated to false

```scala
numbers.dropWhile(_ < 3) // Returns a list with (3, 4, 5, 6, 7, 8, 9, 10)
```

## foldLeft
Accumulator function that starts from the first, with an initial value.

```scala
numbers.foldLeft(0) {(m: Int, n: Int) => m + n}
```

## foldRight
Similar to foldLeft above but starts from the last element.

## flatten
Collapses one level of nested structure

```scala
List(List(1,2), List(3, 4)).collapse() // returns List(1, 2, 3, 4)
```

## flatMap
Combinator that maps and flattens simultaneously.

```scala
val nestedNumbers = List(List(1,2), List(3,4))
nestedNumbers.flatMap(x => x.map(_ * 2)) // Returns List of (2, 4, 6, 8)
```

## Generalized combinators
Every functional combinator shown above can be written on top of fold.

```scala
def ourMap(numbers: List[Int], fn: Int => Int): List[Int] = {
  numbers.foldRight(List[Int]()) { (x: Int, xs: List[Int]) =>
    fn(x) :: xs
  }
}
```

## Extra
All of the combinators work on maps too, with a slight modification to handle both key and value.

```scala
val extensions = Map("steve" -> 100, "bob" -> 101, "joe" -> 201)

// Either name a single tuple to reference
extensions.filter((namePhone: (String, Int)) => namePhone._2 < 200)

// Or use a pattern match
extensions.filter({case (name, extension) => extension < 200})
```