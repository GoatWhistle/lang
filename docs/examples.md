# Example programs

Complete programs from the `examples/` directory, explained in detail.

## Factorial — recursion and IO

The classic recursive function: `fun rec`, `if/then/else`, and an IO block.

[`factorial.goat`](../compiler/examples/factorial.goat)

```goat
fun rec factorial n =
  if n <= 1 then 1
  else n * factorial (n - 1)

fun main _ =
  io {
    do! println (show (factorial 10))   -- 3628800
  }
```

## Fibonacci — three approaches

Naive recursion, a tail-recursive version, and an infinite lazy stream.

[`fibonacci.goat`](../compiler/examples/fibonacci.goat)

```goat
fun rec fib n =
  match n with
  | 0 => 0
  | 1 => 1
  | n => fib (n - 1) + fib (n - 2)

fun rec fibs a b = a :: lazy (fibs b (a + b))
let fibStream = fibs 0 1   -- take 10 -> [0,1,1,2,3,5,8,13,21,34]
```

## List operations

Sorting, folding, mapping, filtering, and zip over plain lists.

[`list_ops.goat`](../compiler/examples/list_ops.goat)

```goat
fun rec quicksort xs =
  match xs with
  | []       => []
  | p :: rest =>
      let smaller = filter (\x -> x < p) rest in
      let greater = filter (\x -> x >= p) rest in
      append (quicksort smaller) (p :: quicksort greater)
```

## Sorting — comparison functions

A parameterized quicksort: the comparator is passed as an argument, so one implementation covers any ordering.

[`quicksort.goat`](../compiler/examples/quicksort.goat)

```goat
fun rec quicksort cmp xs =
  match xs with
  | []       => []
  | p :: rest =>
      let smaller = filter (\x -> cmp x p) rest in
      let greater = filter (\x -> not (cmp x p) && x /= p) rest in
      append (quicksort cmp smaller) (p :: quicksort cmp greater)
```

## Lazy streams — infinite sequences

The sieve of Eratosthenes and other infinite streams.

[`lazy_streams.goat`](../compiler/examples/lazy_streams.goat)

```goat
-- Sieve of Eratosthenes
fun rec sieve xs =
  match xs with
  | []       => []
  | p :: rest =>
      let ps = lazyFilter (\x -> x mod p /= 0) (force rest)
      in p :: lazy (sieve ps)

let primes = sieve (natsFrom 2)   -- take 10 -> [2,3,5,7,11,13,17,19,23,29]
```

## The Option monad — safe computation

Chaining fallible steps with `bindOption`; the first `None` short-circuits the rest.

[`option_monad.goat`](../compiler/examples/option_monad.goat)

```goat
fun safeDivide x y =
  if y == 0 then None
  else Some (x / y)

fun pipeline x =
  bindOption (safeDivide 100 x) (\q ->
  Some (show q))
```

## Algebraic data types — shapes

An ADT with multi-field constructors and exhaustive matching for area and perimeter.

[`shapes.goat`](../compiler/examples/shapes.goat)

```goat
type Shape =
  | Circle    of radius
  | Rectangle of width height

fun area shape =
  match shape with
  | Circle r      => pi * r * r
  | Rectangle w h => w * h
```

## File IO

Writing, reading, and processing file contents.

[`file_io.goat`](../compiler/examples/file_io.goat)

```goat
fun main _ =
  io {
    let path = "out.txt"
    do! writeFile path "Hello from Goat!\nLine 2\n"
    let! content = readFile path
    do! println ("Lines: " ++ show (length (lines content)))
  }
```

---

Previous: [Combinators & utilities](stdlib/utils.md)
