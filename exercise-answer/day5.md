**Exercise D5-1 answer**

```scala
  @tailrec
  def foldLeft[A, B](as: List[A], z: B, f: (B, A) => B): B = as match
    case Nil => z
    case Cons(x, xs) => foldLeft(xs, f(z, x), f)
```

**Exercise D5-2 answer**

```scala
  def reverse[A](as: List[A]): List[A] = 
    foldLeft(as, Nil: List[A], (acc, h) => Cons(h, acc))
```

**Exercise D5-3 answer**

```scala
  def appendViaFoldRight[A](a1: List[A], a2: List[A]): List[A] =
    foldRight(a1, a2, Cons(_, _))
```

**Exercise D5-4 answer**

```scala
  def map[A, B](l: List[A], f: A => B): List[B] = 
    foldRight(l, Nil: List[B], (h, t) => Cons(f(h), t))
```

**Exercise D5-5 answer**

```scala
  def size[A](t: Tree[A]): Int = t match
    case Leaf(_) => 1
    case Branch(l, r) => 1 + size(l) + size(r)
```