# Bindings & functions

Naming values, defining functions, and recursion.

## let — value binding

Binds a name to a value. It can be global (a top-level declaration) or local (inside an expression via `in`).

### Global binding

```goat
let pi = 3.14159
let greeting = "Hello, world!"
let doubled = map (\x -> x * 2) [1..5]
```

### Local binding (let … in)

```goat
let result =
  let x = 10 in
  let y = x * 2 in
  x + y       -- 30
```

> **Note:** inside an IO block, `let` without `in` is a sequential binding, while `let!` is a monadic bind of an IO action.

## fun — function definition

Declares a named function. Parameters follow the name, separated by spaces, and the body comes after `=`.

```goat
fun greet name =
  "Hello, " ++ name ++ "!"

fun add x y = x + y

fun clamp lo hi x =
  if x < lo then lo
  else if x > hi then hi
  else x
```

### Currying and partial application

Every function is curried. `fun add x y = x + y` is equivalent to `fun add x = \y -> x + y`. Applying fewer arguments returns a new function:

```goat
let add5 = add 5       -- a function Int -> Int
let r    = add5 3     -- 8
```

## Lambda expressions

Anonymous functions are written as `\params -> body`:

```goat
let square = \x -> x * x
let add     = \x y -> x + y
let evens   = filter (\x -> x mod 2 == 0) [1..10]
```

## Recursion

Recursive functions are declared with the `rec` keyword:

```goat
fun rec factorial n =
  if n <= 1 then 1
  else n * factorial (n - 1)

fun rec fibFast a b n =
  if n == 0 then a
  else fibFast b (a + b) (n - 1)
```

> Without `rec`, the function name is not in scope inside its own body. Mutual recursion is not supported yet.

---

Previous: [Operators](operators.md) · Next: [Control flow](control-flow.md)
