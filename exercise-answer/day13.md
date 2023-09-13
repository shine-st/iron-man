**Exercise D13-1 answer**

```scala
  def nonNegativeInt(rng: RNG): (Int, RNG) =
    val (n, nextRng) = rng.nextInt
    if n >= 0 then
      (n, nextRng)
    else
      nonNegativeInt(nextRng)
```

**Exercise D13-2 answer**

```scala
  def double(rng: RNG): (Double, RNG) =
    val (i, r) = nonNegativeInt(rng)
    (i / (Int.MaxValue.toDouble + 1), r)
```

**Exercise D13-3 answer**

```scala
  def takeWhileViaFoldRight(p: A => Boolean): LazyList[A] =
    foldRight(empty)((a, b) => if p(a) then cons(a, b) else empty)
```

**Exercise D13-4 answer**

```scala
  def doubleViaMap: Rand[Double] =
    map(nonNegativeInt)(_ / (Int.MaxValue.toDouble + 1))
```

**Exercise D13-5 answer**

```scala
  def map2[A, B, C](ra: Rand[A], rb: Rand[B])(f: (A, B) => C): Rand[C] =
    rng =>
      val (i1, r1) = ra(rng)
      val (i2, r2) = rb(r1)
      (f(i1, i2), r2)
```