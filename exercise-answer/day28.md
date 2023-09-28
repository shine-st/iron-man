**Exercise D28-1 answer**

```scala
  extension[A] (fa: F[A])
    def product[B](fb: F[B]): F[(A, B)] =
      fa.map2(fb)((_, _))

  def replicateM[A](n: Int, fa: F[A]): F[List[A]] =
    sequence(List.fill(n)(fa))
```