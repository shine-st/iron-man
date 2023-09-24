**Exercise D24-1 answer**

```scala
  def productMonoid[A, B](ma: Monoid[A], mb: Monoid[B]): Monoid[(A, B)] = new:
    def combine(a1: (A, B), a2: (A, B)): (A, B) = (ma.combine(a1._1, a2._1), mb.combine(a1._2, a2._2))

    def empty: (A, B) = (ma.empty, mb.empty)
```
