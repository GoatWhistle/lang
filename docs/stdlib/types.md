# Option & Result

The two core error-handling types, defined in the standard library.

> The whole standard library is available without imports: it loads automatically when the interpreter starts.

## The Option type

Represents an optional value:

```goat
type Option =
  | None
  | Some of x
```

```goat
match present with
| None   => "nothing"
| Some x => "got: " ++ show x
```

## The Result type

Represents either success or failure:

```goat
type Result =
  | Ok  of x
  | Err of e
```

```goat
fun divide x y =
  if y == 0 then Err "division by zero"
  else Ok (x / y)
```

## Option combinators

| Function | Type | Description |
|---|---|---|
| `mapOption f opt` | (a→b)→Option a→Option b | Apply a function to the contents if `Some` |
| `bindOption opt f` | Option a→(a→Option b)→Option b | Monadic chaining |
| `fromMaybe def opt` | a→Option a→a | The value, or a default on `None` |
| `isNone opt` | Option a→Bool | Whether it is `None` |
| `isSome opt` | Option a→Bool | Whether it is `Some` |

## Result combinators

| Function | Type | Description |
|---|---|---|
| `mapOk f r` | (a→b)→Result a e→Result b e | Apply a function to `Ok`, leave `Err` untouched |
| `bindOk r f` | Result a e→(a→Result b e)→Result b e | Monadic chaining along the success path |

---

Previous: [IO blocks](io.md) · Next: [IO functions](io.md)
