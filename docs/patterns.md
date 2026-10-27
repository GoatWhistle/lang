# Pattern matching

Every pattern form available in `match` branches and bindings.

| Pattern | Matches | Example |
|---|---|---|
| `_` | Any value (wildcard) | `\| _ => "other"` |
| Literal | A specific value | `\| 0 => "zero"` |
| Variable | Anything; binds the value | `\| x => x + 1` |
| `[]` | The empty list | `\| [] => 0` |
| `p :: rest` | A non-empty list; head and tail | `\| x :: xs => x` |
| `[p1, p2]` | A list with exactly N elements | `\| [a, b] => a + b` |
| `(p1, p2)` | A tuple of the matching arity | `\| (a, b) => a` |
| `Ctor p1 p2` | An ADT constructor | `\| Circle r => pi * r * r` |
| `p as name` | A pattern; also binds the whole value | `\| x :: _ as xs => (x, xs)` |
| `p when guard` | A pattern plus a condition | `\| x when x > 0 => "pos"` |

```goat
fun firstTwo xs =
  match xs with
  | []            => (0, 0)
  | [x]           => (x, 0)
  | [x, y]        => (x, y)
  | x :: y :: _  => (x, y)

fun describeList xs =
  match xs with
  | [] => "empty"
  | [_] => "singleton"
  | _ :: _ as all when length all > 10 => "long"
  | _ => "short"
```

---

Previous: [Lists, tuples & ADTs](data.md) · Next: [Lazy evaluation](lazy.md)
