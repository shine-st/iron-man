**Exercise D22-1 answer**

```scala
  val intAddition: Monoid[Int] = new:
    def combine(a1: Int, a2: Int) = a1 + a2
    val empty = 0

  val intMultiplication: Monoid[Int] = new:
    def combine(a1: Int, a2: Int) = a1 * a2
    val empty = 1

  val booleanAnd: Monoid[Boolean] = new:
    def combine(a1: Boolean, a2: Boolean) = a1 && a2
    val empty = true

  val booleanOr: Monoid[Boolean] = new:
    def combine(a1: Boolean, a2: Boolean) = a1 || a2
    val empty = false
```

**Exercise D22-2 answer**

```scala
  def optionMonoid[A]: Monoid[Option[A]] = new:
    def combine(x: Option[A], y: Option[A]) = x orElse y
    val empty = None
```
