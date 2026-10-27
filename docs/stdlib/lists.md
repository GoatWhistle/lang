# Lists

Working with finite and lazy lists.

## Basics

| Function | Type | Description |
|---|---|---|
| `head xs` / `tail xs` | [a] → a / [a] → [a] | First element / everything after it |
| `last xs` / `init xs` | [a] → a / [a] → [a] | Last element / everything before it |
| `length xs` | [a] → Int | List length |
| `null xs` | [a] → Bool | Whether the list is empty |
| `nth n xs` | Int → [a] → a | Element at index (0-based) |
| `reverse xs` / `sort xs` | [a] → [a] | Reverse / sort |
| `append xs ys` / `concat xss` | — | Concatenate / flatten |

## Higher-order

**`map : (a -> b) -> [a] -> [b]`**

Applies a function to every element.

```goat
map (\x -> x * 2) [1, 2, 3]  -- [2, 4, 6]
```

**`filter : (a -> Bool) -> [a] -> [a]`**

Keeps only the elements that satisfy the predicate.

**`fold : (acc -> a -> acc) -> acc -> [a] -> acc`**

Left fold (foldl).

```goat
fold (\acc x -> acc + x) 0 [1..5]   -- 15
```

**`foldr : (a -> acc -> acc) -> acc -> [a] -> acc`**

Right fold (foldr).

**`concatMap / zipWith / scan`**

Flat-map, pairwise combine two lists, and fold that keeps every intermediate accumulator.

## Search

| Function | Description |
|---|---|
| `any pred xs` | Whether any element satisfies the predicate |
| `all pred xs` | Whether every element satisfies the predicate |
| `elem x xs` | Whether the element is in the list |

## Transform

| Function | Description |
|---|---|
| `take n xs` / `drop n xs` | First n elements / everything after them |
| `takeWhile pred xs` / `dropWhile pred xs` | Leading run while the predicate holds |
| `zip xs ys` / `unzip pairs` | Pair up / split apart |
| `replicate n x` / `range lo hi` | n copies / inclusive integer range |

## Lazy lists

**`lazyFilter : (a -> Bool) -> [a] -> [a]`**

A filter for lazy (possibly infinite) lists. The tail is forced on demand.

**`iterate : (a -> a) -> a -> [a]`**

An infinite list: `x, f(x), f(f(x)), …`

**`repeat : a -> [a]    natsFrom : Int -> [Int]`**

An infinite repeat, and an infinite stream of naturals (`nats` starts at 0).

---

Previous: [Math](math.md) · Next: [Combinators & utilities](utils.md)
