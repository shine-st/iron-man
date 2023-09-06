**Exercise D7-1 answer**

```scala
  def getOrElse[B >: A](default: => B): B = this match
    case None => default
    case Some(x) => x

  def flatMap[B](f: A => Option[B]): Option[B] = this match
    case None => None
    case Some(x) => f(x)

  //  使用既有的 pattern match 實現
  def flatMapV2[B](f: A => Option[B]): Option[B] =
    map(f).getOrElse(None)

  def orElse[B >: A](ob: => Option[B]): Option[B] = this match
    case None => ob
    case _ => this

  //  使用既有的 pattern match 實現
  def orElseV2[B >: A](ob: => Option[B]): Option[B] =
    map(Some(_)).getOrElse(ob)

  def filter(f: A => Boolean): Option[A] = this match
    case Some(x) if f(x) => this
    case _ => None
```

**Exercise D7-2 answer**

```scala
  def flatMap[EE >: E, B](f: A => Either[EE, B]): Either[EE, B] = this match
    case Left(e) => Left(e)
    case Right(a) => f(a)

  def orElse[EE >: E, B >: A](b: => Either[EE, B]): Either[EE, B] = this match
    case Left(_) => b
    case Right(a) => Right(a)
```