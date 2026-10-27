# Strings

Inspecting, splitting, transforming, and parsing strings.

## Info

**`strLength : String -> Int`**

The length of a string in characters.

**`contains : String -> String -> Bool`**

Checks whether a string contains a substring.

## Splitting

**`chars : String -> [String]`**

Splits a string into a list of characters.

**`words : String -> [String]`**

Splits a string into words on spaces and tabs.

**`lines : String -> [String]`**

Splits a string into lines on `\n` and `\r`.

## Transform

**`trim : String -> String`**

Removes whitespace from both ends of a string.

**`toUpper / toLower : String -> String`**

Convert a string to upper- or lowercase.

**`replace : String -> String -> String -> String`**

Replaces every occurrence of a substring. `replace string old new`.

**`unwords / unlines : [String] -> String`**

Join a list of words with spaces, or lines with `\n`.

## Parsing

**`parseInt : String -> Option Int`**

Parses a string as an integer. Returns `Some n` or `None`.

**`parseFloat : String -> Option Float`**

Parses a string as a floating-point number.

---

Previous: [IO functions](io.md) · Next: [Math](math.md)
