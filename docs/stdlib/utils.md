# Combinators & utilities

Small functional building blocks.

| Function | Type | Description |
|---|---|---|
| `id x` | a→a | The identity function |
| `const x _` | a→b→a | Always returns the first argument |
| `flip f x y` | (a→b→c)→b→a→c | Swaps the argument order |
| `compose f g x` | (b→c)→(a→b)→a→c | Function composition: `f(g(x))` |
| `fix f` | ((a→b)→a→b)→a→b | Fixed point (the Y combinator) |

```goat
let double    = \x -> x * 2
let addOne    = \x -> x + 1
let doubleThenAdd = compose addOne double
let r = doubleThenAdd 5  -- 11

let always42 = const 42
let xs = map always42 [1..5]  -- [42, 42, 42, 42, 42]
```

---

Previous: [Lists](lists.md) · Next: [Example programs](../examples.md)
