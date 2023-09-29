**Exercise D28-1 answer**

```scala
  extension[A] (fa: F[A])
    def product[B](fb: F[B]): F[(A, B)] =
      fa.map2(fb)((_, _))

  def replicateM[A](n: Int, fa: F[A]): F[List[A]] =
    sequence(List.fill(n)(fa))
```

**Exercise D28-2 answer**

```scala
  extension[A] (fa: F[A])
    def map3[B, C, D](fb: F[B], fc: F[C])(f: (A, B, C) => D): F[D] =
      apply(apply(apply(unit(f.curried))(fa))(fb))(fc)
```