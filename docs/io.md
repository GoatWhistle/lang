# IO blocks

IO computations are isolated inside `io { … }` blocks.

| Form | Meaning |
|---|---|
| `do! expr` | Run an IO action, discard the result |
| `let! x = expr` | Run an IO action, bind the result to `x` |
| `let x = expr` | A pure binding (no IO) |
| `return expr` | Return a pure value from the IO block |

```goat
fun main _ =
  io {
    do! println "What is your name?"
    let! name = input
    let msg = "Hello, " ++ name ++ "!"
    do! println msg
    do! writeFile "log.txt" msg
  }
```

## Entry point

A program defines a `main` function that takes one argument (usually `_`) and returns an IO block:

```goat
fun main _ =
  io {
    do! println "Hello, Goat!"
  }
```

---

Previous: [Lazy evaluation](lazy.md) · Next: [Option & Result](stdlib/types.md)
