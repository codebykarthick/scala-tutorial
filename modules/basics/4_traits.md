<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->
# Table of Contents
- [Traits](#traits)
- [Traits vs Abstract Class](#traits-vs-abstract-class)

<!-- TOC end -->

<!-- TOC --><a name="traits"></a>
## Traits
traits are collections of fields and behaviours that you can extend or mixin with your classes.

```scala
trait Car {
    val brand: String
}

trait Shiny {
    val shineRefraction: Int
}

// Multiple inheritance with "with" keyword
class BMW extends Car with Shiny {
    val brand = "BMW"
    val shineRefraction = 12
}
```

<!-- TOC --><a name="traits-vs-abstract-class"></a>
## Traits vs Abstract Class
When to use traits and when to use abstract class?

* Favor traits: Class can extend several traits but can only extend one class.
* If a constructor parameter is needed, use an abstract class.

[Prev Page](./3_classes.md) 

[Next Page](./5_types.md)