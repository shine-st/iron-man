**Exercise D20-1 answer**

```scala
  def map2[A, B, C](p: Parser[A], p2: Parser[B])(f: (A, B) => C): Parser[C] =
    product(p, p2).map((a, b) => f(a, b))
```
