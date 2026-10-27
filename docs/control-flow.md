# Control flow

Branching with `if`, `match`, and guards.

## if / then / else

A conditional expression. The `else` branch is **always** required: both branches must produce a value of the same type.

```goat
let sign x =
  if x > 0 then "positive"
  else if x < 0 then "negative"
  else "zero"

let abs x = if x < 0 then -x else x
```

## match — pattern matching

Matches a value against a sequence of patterns. Each branch reads `| pattern => body`.

```goat
fun describe n =
  match n with
  | 0   => "zero"
  | 1   => "one"
  | _   => "many"

fun sumList xs =
  match xs with
  | []         => 0
  | x :: rest  => x + sumList rest
```

## Guards (when)

A pattern can carry an extra condition through `when`:

```goat
fun classify n =
  match n with
  | x when x < 0   => "negative"
  | x when x == 0  => "zero"
  | x when x < 10  => "small"
  | _              => "large"
```

---

Previous: [Bindings & functions](bindings.md) · Next: [Lists, tuples & ADTs](data.md)
