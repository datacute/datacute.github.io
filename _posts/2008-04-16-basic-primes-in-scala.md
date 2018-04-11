---
layout: post
title: Basic Primes in Scala
date: 2008-04-16 00:17
author: spdenne
comments: true
---

I've started learning [Scala](http://www.scala-lang.org/).
One way I learn is by reading and experimenting,
so I looked for a simple program I could write in the right problem space
to make use of language features expressed more succinctly in Scala than in Java.

<!--more-->
 
### Desired Application
 
I chose to implement a weird idea that I had a couple of years ago:
Instead of representing natural numbers in base 10, or any other fixed base,
record the prime factorisation.
Instead of recording how many 1s, 10s, 100s, 1000s, etc. to sum, 
you can record how many 2s, 3s, 5s, 7s, 11s, 13s, etc. to multiply. 
(With a special code for 1.)
Each prime number is indexed, and referred to by its index, such that, 
for example the number 288 (base 10) = 3^2 x 2^5, 
which is 3 (the second prime) to the power of 2 (the first prime), 
multiplied by 2 (the first prime) to the power of 5 (the third prime). 
The powers are also converted into their representation within this same system.
 
Using `[x]` to refer to the x'th prime, we get 288 (base 10)

```
= [2] ^ [1] x [1] ^ [3]
= [[1]] ^ [1] x [1] ^ [[2]]
= [[1]] ^ [1] x [1] ^ [[[1]]]
```

Everything reduces to `[1]`, which I then replace with `[]`.
Multiplication signs can be removed,
and power signs can be replaced with parenthesis to give a cryptic representation: 288 = `[[]]([])[]([[[]]])`

A cleaner representation may be to replace 1, with `()`, 
meaning "to the power of zero", but that is not what I did for this silly example.

That covers the basic idea for the program: 
conversion from simple base 10 numbers into these cryptic character sequences representing the prime factorisation.

### Generating A Sequence Of Primes

To start with I looked for a way to calculate primes in Scala. 
The docs on [scala.Stream](http://www.scala-lang.org/docu/files/api/scala/Stream.html) 
includes a simple definition of the [Sieve of Eratosthenes](http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes). 
I started with something similar, which I found on [Scala Kurz](http://www.scala-kurz.org/show/15):

```scala
def sieve(s: Stream[Int]): Stream[Int] = 
  Stream.cons(s.head, sieve(s.tail filter (_ % s.head != 0)))
val primes = sieve(Stream.from(2))
```

This simple algorithm is quite easy to understand, but unfortunately is pretty useless, 
as it is so resource intensive that without changing any JVM runtime parameters, 
it can only calculate up to the 1641st prime 
(or the 3715th prime if using the scala runtime, which starts the jvm with a larger heap) before overflowing the stack.

### Generating A Sequence Of Primes Efficiently

The [Literate Programs site](http://en.literateprograms.org/LiteratePrograms:Welcome) 
includes the same implementation in its 
[Sieve of Eratosthenes in Scala](http://en.literateprograms.org/Sieve_of_Eratosthenes_%28Scala%29) page, 
but the [Sieve of Eratosthenes in Haskell](http://en.literateprograms.org/Sieve_of_Eratosthenes_%28Haskell%29) 
includes a more efficient functional implementation that I thought I'd convert to Scala 
(I don't know Haskell, but the algorithm is explained well).

The most difficult part of the conversion was trying to decipher what foldr1 was supposed to do. 
I incorrectly assumed it was the same as Stream.foldRight, 
which I butchered till I arrived at something that seemed to work 
(The definition of foldr1 below is probably **not** equivalent to Haskell's.):

```scala
def merge(xs: Stream[Int] , ys: Stream[Int]): Stream[Int] = {
  if (xs.head < ys.head)
    return Stream.cons(xs.head, merge(xs.tail, ys))
  if (xs.head == ys.head) 
    return Stream.cons(xs.head, merge(xs.tail, ys.tail))
  return Stream.cons(ys.head, merge(xs, ys.tail))
}
def diff(xs: Stream[Int], ys: Stream[Int]): Stream[Int] = {
  if (xs.head < ys.head) 
    return Stream.cons(xs.head, diff(xs.tail, ys))
  if (xs.head == ys.head) return diff(xs.tail, ys.tail)
  return diff(xs, ys.tail)
}
def f(xs: Stream[Int], ys: => Stream[Int]) = 
  Stream.cons(xs.head, merge(xs.tail, ys))
def g(p: Int) = Stream.from(p*p,p*2)
def foldr1(f: (Stream[Int], => Stream[Int]) => Stream[Int])
  (s: Stream[Stream[Int]]): Stream[Int] =
  if (s.isEmpty) Stream.empty
  else f(s.head, foldr1(f)(s.tail))
val primes: Stream[Int] = 
  Stream.fromIterator((2::3::5::Nil).elements).append(
      diff(Stream.from(7,2), nonprimes))
val nonprimes = foldr1(f)(primes.tail map g)
```

Now I can calculate up to the 18707th prime, 
an order of magnitude more that the simple algorithm, 
in an order of magnitude more lines of code.

Comments in Jorge Ortiz post 
[Fun with Project Euler and Scala](http://scala-blogs.org/2007/12/project-euler-fun-in-scala.html) 
also mention the poor resource utilisation of the two-line sieve, 
and code is supplied for providing a stream of primes using java's BigInteger.nextProbablePrime(). 
I'll leave that for now though, and get back on track...

### Determining Prime Factorisation

Next I needed indexed prime factors:

```scala
// Prime Factor Tuple: Prime, Power, Index
type Factors = List[(Int, Int, Int)];
def primeFactorsRecurse(i: Int, factors: Factors, 
    morePrimes: Stream[Int], index: Int): Factors = {
  if (i == 1) return factors;
  if (i % morePrimes.head == 0) {
    if ((factors != Nil) && (morePrimes.head == factors.head._1)) {
      return primeFactorsRecurse(i / morePrimes.head, 
          (morePrimes.head, factors.head._2 + 1, index) :: 
          factors.tail, 
          morePrimes, index);
    } else {
      return primeFactorsRecurse(i / morePrimes.head, 
          (morePrimes.head, 1, index) :: factors, 
          morePrimes, index);
    }
  }
  return primeFactorsRecurse(
      i, factors, morePrimes drop 1, index + 1);
}

def primeFactors(i: Int): Factors = {
  if (i == 1) return (1,1,0) :: Nil;
  primeFactorsRecurse(i, Nil, primes, 1);
}
```

### Printing The Numbers

All that is needed now is the code to print the numbers using the unusual representation described above:

```scala
def printPrimeFactors(factors: Factors): Unit = {
  factors match{
    case (prime: Int, power: Int, index: Int) :: morefactors =>  {
      if (index > 0) printPrimeFactors("[", index, "]")
      if (power > 1) printPrimeFactors("(", power, ")")
      printPrimeFactors(morefactors)
    }
    case Nil => ();
  }
}

def printPrimeFactors(pre: String, i: Int, post: String): Unit = {
  print(pre)
  printPrimeFactors(primeFactors(i))
  print(post)
}

(1 to 300) foreach {i: Int => printPrimeFactors(i + ":",i,"\n")}
```

### Summary

I was able to create an application in Scala to do what I wanted, 
while making use of a number of Scala language features.

I'll welcome corrections, and comments regarding the Scala code, 
such as how I can create a infix Stream.cons operator to make my code less verbose, 
or ways to automatically switch to BigInts if the range of Int is surpassed.

I'd also be extremely interested in anyone can think of a use for this representation of natural numbers. 
The same ideas can be converted into graphical symbols, 
e.g. using differently sized concentric circles instead of `[[[]]]`, 
or tracing a path to give a particular "primal squiggle" that uniquely represents a number, (such as an IP address). 
The order of factors doesn't matter, 
so that provides scope to position graphical representations of them in artistically pleasing arrangements.
