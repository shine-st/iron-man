**Exercise D11-1 answer**

```scala
  def takeWhileViaFoldRight(p: A => Boolean): LazyList[A] =
    foldRight(empty)((a, b) => if p(a) then cons(a, b) else empty)

  def filter(f: A => Boolean): LazyList[A] =
    foldRight(empty[A])((a, acc) => if f(a) then cons(a, acc) else acc)
```

**Exercise D11-2 answer**

```scala
  def map[B](f: A => B): LazyList[B] =
    foldRight(empty[B])((a, acc) => cons(f(a), acc))

  def flatMap[B](f: A => LazyList[B]): LazyList[B] =
    foldRight(empty[B])((a, acc) => f(a).append(acc))
```

