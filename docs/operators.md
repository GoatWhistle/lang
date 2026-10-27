# Operators

Operators are listed from lowest to highest precedence.

| Precedence | Operator | Associativity | Description |
|---|---|---|---|
| 1 | `\|>` | left | Pipe: `x \|> f` becomes `f x` |
| 1 | `~>` | left | Lazy pipe: the argument is wrapped in `lazy` |
| 2 | `&&` | left | Logical AND |
| 2 | `\|\|` | left | Logical OR |
| 3 | `==` `!=` `/=` | none | Equality / inequality (`!=` and `/=` are synonyms) |
| 3 | `` `=` | none | Comparison |
| 4 | `++` | right | String and list concatenation |
| 5 | `::` | right | Cons: prepend an element to a list |
| 6 | `+` `-` | left | Addition / subtraction |
| 7 | `*` `/` `mod` | left | Multiplication / division / remainder |
| 8 | `**` | right | Exponentiation |
| 9 | `not` | prefix | Logical negation |
| 10 | `-` | prefix | Unary minus |
| 11 | application | left | `f x y`, function application |

```goat
-- Operator examples
let a = 2 ** 10              -- 1024
let b = 10 mod 3            -- 1
let s = "hello" ++ " world" -- "hello world"
let xs = 1 :: 2 :: 3 :: []  -- [1, 2, 3]
let r = xs |> reverse |> show  -- pipeline
```

## Pipe operators

Feed the value on the left into the function on the right:

```goat
-- |> is the ordinary pipe
let result = [1..10]
  |> filter (\x -> x mod 2 == 0)
  |> map (\x -> x * x)
  |> fold (\acc x -> acc + x) 0
  |> show
```

---

Previous: [Comments & literals](comments-literals.md) · Next: [Bindings & functions](bindings.md)
