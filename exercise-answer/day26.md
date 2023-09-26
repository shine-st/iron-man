**Exercise D26-1 answer**

```scala
  given listMonad: Monad[List] with
    def unit[A](a: => A) = List(a)

    extension[A] (fa: List[A])
      def flatMap[B](f: A => List[B]) =
        fa.flatMap(f)

  given optionMonad: Monad[Option] with
    def unit[A](a: => A) = Some(a)

    extension[A] (fa: Option[A])
      def flatMap[B](f: A => Option[B]) =
        fa.flatMap(f)
```

**Exercise D26-2 answer**

```scala
  def sequence[A](fas: List[F[A]]): F[List[A]] =
    fas.foldRight(unit(List[A]()))((fa, acc) => fa.map2(acc)(_ :: _))
```

**Exercise D26-3 answer**

```scala
  def replicateM[A](n: Int, fa: F[A]): F[List[A]] =
    sequence(List.fill(n)(fa))
```
