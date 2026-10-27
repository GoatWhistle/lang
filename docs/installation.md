# Installation & CLI

Build Goat from source and run programs through the CLI or the interactive REPL.

## Requirements

| Tool | Version |
|---|---|
| .NET SDK | 10.0.x |
| F# | 9+ |
| OS | Windows / Linux / macOS |

## Build from source

```bash
git clone https://github.com/GoatWhistle/lang.git
cd lang/compiler
dotnet restore Goat.slnx
dotnet build Goat.slnx
dotnet test Goat.slnx
```

## CLI commands

| Command | Action |
|---|---|
| `goat run file.goat` | Parse, evaluate, and run `main` |
| `goat check file.goat` | Parse and desugar without running |
| `goat repl` | Start the interactive REPL |
| `goat --help` | Show usage |
| `goat --version` | Show the interpreter version |

```bash
dotnet run --project src/Goat.Cli -- run examples/factorial.goat
dotnet run --project src/Goat.Repl
```

## Makefile targets

| Command | Action |
|---|---|
| `make build` | Compile |
| `make test` | 142 xUnit tests |
| `make repl` | Start the REPL |
| `make run FILE=…` | Run a file |
| `make examples` | Run every example |

---

Previous: [Overview](README.md) · Next: [Comments & literals](comments-literals.md)
