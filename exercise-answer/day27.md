**Exercise D27-1 answer**

```scala
  def join[A](ffa: F[F[A]]): F[A] =
    ffa.flatMap(fa => fa)
```