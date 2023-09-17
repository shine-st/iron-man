**Exercise D17-1 answer**

```scala
  def asyncF[A, B](f: A => B): A => Par[B] =
    a => lazyUnit(f(a))
```

**Exercise D17-2 answer**

```scala
  def parFilter[A](l: List[A])(f: A => Boolean): Par[List[A]] = fork:
    val pas: List[Par[List[A]]] = l.map(asyncF(a =>
      if f(a) then
        List(a)
      else
        List()
    ))

    sequence(pas).map(_.flatten)
```