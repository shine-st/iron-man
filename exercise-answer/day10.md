**Exercise D10-1 answer**

```scala
  def toList: List[A] = this match
    case Empty => Nil
    case Cons(h, t) => h() :: t().toList
```

**Exercise D10-2 answer**

```scala
  def take(n: Int): LazyList[A] = this match
    case Cons(h, t) if n > 0 => cons(h(), t().take(n - 1))
    case _ => empty

  def drop(n: Int): LazyList[A] = this match
    case Cons(_, t) if n > 0 => t().drop(n - 1)
    case _ => this
```

**Exercise D10-3 answer**

```scala
  def takeWhile(f: A => Boolean): LazyList[A] = this match
    case Cons(h, t) if f(h()) => cons(h(), t().takeWhile(f))
    case _ => empty
```