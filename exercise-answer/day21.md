**Exercise D21-1 answer**

```scala
  def product[A, B](p: Parser[A], p2: => Parser[B]): Parser[(A, B)] =
    flatMap(p)(a => p2.map(b => (a, b)))
```

**Exercise D21-2 answer**

```scala
  def map[A, B](p: Parser[A])(f: A => B): Parser[B] =
    flatMap(p)(a => succeed(f(a)))
```
