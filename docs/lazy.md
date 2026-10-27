# Lazy evaluation

Goat uses *explicit* laziness: evaluation is deferred only where you ask for it.

## lazy / force

```goat
let expensive = lazy (factorial 100)  -- a thunk, not yet evaluated
let result     = force expensive       -- evaluated on force

let thunk = lazy (2 + 2)
let val   = force thunk               -- 4, memoized
```

## Infinite lists

Lazy tails let you build infinite data structures:

```goat
fun rec natsFrom n = n :: lazy (natsFrom (n + 1))
let nats = natsFrom 0

fun rec fibs a b = a :: lazy (fibs b (a + b))
let fibStream = fibs 0 1

-- Take the first N elements of an infinite stream
let first10 = take 10 nats       -- [0..9]
let fibs10  = take 10 fibStream   -- [0, 1, 1, 2, 3, 5, ...]
```

## The lazy pipe `~>`

Passes the right operand as a `lazy` value:

```goat
-- x ~> f  is equivalent to  f (lazy x)
let stream = fibs 0 1
let filtered = lazyFilter (\x -> x mod 2 == 0) stream
```

---

Previous: [Pattern matching](patterns.md) · Next: [IO blocks](io.md)
