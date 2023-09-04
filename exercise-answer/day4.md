**Exercise D4-1 answer**

```scala
  def setHead[A](l: SinglyLinkedList[A], head: A): SinglyLinkedList[A] = l match
    case Cons(_, tail) => Cons(head, tail)
    case Nil => throw new NoSuchElementException("list is empty")
```

**Exercise D4-2 answer**

```scala
  def drop[A](l: SinglyLinkedList[A], n: Int): SinglyLinkedList[A] =
    if n <= 0 then
      l
    else
      l match
        case Cons(_, tail) => drop(tail, n - 1)
        case Nil => Nil
```

**Exercise D4-3 answer**

```scala
  def length[A](l: SinglyLinkedList[A]): Int = 
    foldRight(l, 0, (_, x) => x + 1)
```
