<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->
# Table of Contents
- [Types](#types)

<!-- TOC end -->

<!-- TOC --><a name="types"></a>
## Types
Functions can also be generic and work on any type.

```scala
// Square brackets is used to mention generic types.
trait Cache[K, V] {
  def get(key: K): V
  def put(key: K, value: V)
  def delete(key: K)
}

def remove[K](key: K)
```

[Prev Page](./4_traits.md) 

End of section! To continue to extended basics, follow below.

[Next Page](../basics_extended/6_extended_basics.md)