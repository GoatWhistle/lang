# Comments & literals

The smallest building blocks of a Goat program.

## Comments

Goat has two kinds of comments:

```goat
-- A line comment

{- A block comment,
   which may span lines
   {- and nest -} -}

fun add x y = x + y  -- inline comment
```

## Literals

The primitive types and their literal syntax:

| Type | Examples | Description |
|---|---|---|
| `Int` | `0`, `42`, `-7` | 64-bit signed integer |
| `Float` | `3.14`, `-0.5`, `1.0e10` | 64-bit floating point |
| `Bool` | `true`, `false` | Boolean |
| `String` | `"hello"`, `"line\n"` | UTF-8 string |
| `Unit` | `()` | The unit type, like void |

## String escape sequences

| Sequence | Meaning |
|---|---|
| `\n` | Newline |
| `\t` | Tab |
| `\r` | Carriage return |
| `\\` | Backslash |
| `\"` | Double quote |
| `\'` | Single quote |

---

Previous: [Installation & CLI](installation.md) · Next: [Operators](operators.md)
