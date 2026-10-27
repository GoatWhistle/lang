# IO functions

Output, input, file operations, and process control.

## Output

**`println : String -> IO ()`**

Prints a string followed by a newline.

**`print : String -> IO ()`**

Prints a string without a trailing newline.

**`show : a -> String`**

Converts any value to its string representation.

```goat
show 42         -- "42"
show [1, 2, 3]  -- "[1, 2, 3]"
```

## Input

**`input : IO String`**

Reads one line from stdin.

**`getArgs : IO [String]`**

Returns the command-line arguments.

## Files

**`readFile : String -> IO String`**

Reads the entire contents of a file. Fails if the file is missing.

**`writeFile : String -> String -> IO ()`**

Writes a string to a file, overwriting its contents.

**`appendFile : String -> String -> IO ()`**

Appends a string to the end of a file.

**`fileExists : String -> IO Bool`**

Checks whether a file exists.

## System

**`exit : Int -> IO ()`**

Terminates the process with the given exit code.

**`error : String -> a`**

Aborts execution with the given error message.

---

Previous: [Option & Result](types.md) · Next: [Strings](strings.md)
