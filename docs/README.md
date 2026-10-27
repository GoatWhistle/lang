# Documentation

Goat is a small functional language in F#. These pages cover the language, its standard library, and worked examples.

- [Language](comments-literals.md): Syntax from literals to IO blocks: bindings, functions, pattern matching, ADTs, and laziness.

- [Standard library](stdlib/types.md): Every built-in: Option/Result, IO, strings, math, lists, and combinators.

- [Examples](examples.md): Annotated programs: factorial, Fibonacci, quicksort, lazy streams, the Option monad, ADTs, and file IO.

- [Installation](installation.md): Requirements, building from source, and the CLI and REPL commands.

## A taste of Goat

```goat
fun rec factorial n =
  if n <= 1 then 1
  else n * factorial (n - 1)

fun main _ =
  io {
    do! println (show (factorial 10))
  }
```

---

Next: [Installation & CLI](installation.md)
