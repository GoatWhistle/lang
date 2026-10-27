# Lists, tuples & ADTs

Goat's built-in compound data: lists, tuples, and your own algebraic types.

## Lists and ranges

### List literals

```goat
let empty  = []
let nums   = [1, 2, 3, 4, 5]
let mixed  = ["a", "b", "c"]
```

### The cons operator `::`

```goat
let xs = 1 :: 2 :: 3 :: []  -- [1, 2, 3]
let ys = 0 :: xs             -- [0, 1, 2, 3]
```

### Ranges

```goat
let r1 = [1..5]       -- [1, 2, 3, 4, 5]
let r3 = [1..100]     -- everything from 1 to 100
```

### List concatenation

```goat
let combined = [1, 2] ++ [3, 4]  -- [1, 2, 3, 4]
```

## Tuples

Fixed-size tuples can hold values of different types:

```goat
let pair   = (1, "hello")
let triple = (1, true, 3.14)

fun swap pair =
  match pair with
  | (a, b) => (b, a)
```

## Algebraic data types

Declared as `type TypeName = | Ctor1 | Ctor2 of field1 field2 | …`. Constructors that carry fields are applied like functions.

```goat
type Shape =
  | Circle    of radius
  | Rectangle of width height
  | Triangle  of a b c

let c  = Circle 5.0
let r  = Rectangle 4.0 6.0

fun area shape =
  match shape with
  | Circle r        => pi * r * r
  | Rectangle w h   => w * h
  | Triangle a b c  =>
      let s = (a + b + c) / 2.0 in
      sqrt (s * (s - a) * (s - b) * (s - c))
```

---

Previous: [Control flow](control-flow.md) · Next: [Pattern matching](patterns.md)
