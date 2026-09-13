# Card 2 — add FormatGreeting and wire it into main

**Edit:**
- `services/api/main.go`

**Create:**
- `services/api/main_test.go`

**Intent:** Add an exported `func FormatGreeting(name string) string` to `services/api/main.go`. It trims leading/trailing whitespace from `name`; if the trimmed result is empty, it uses the default name `"friend"` in place of the trimmed input. It then returns `"Hello, <name>!"` using whichever name was selected. Update `main()` to call `FormatGreeting` and print the result with `fmt.Println` (using an empty-string or hardcoded argument), so the call is a real, non-discarded consumer rather than dead code. Add `services/api/main_test.go` with a table-driven test covering an empty/whitespace-only name (expecting the greeting to contain `"friend"`) and an ordinary name such as `"Alice"` (expecting the greeting to contain `"Alice"` and not `"friend"`). Only the standard library (`strings`, `fmt`, `testing`) is needed — no new dependencies. Leave `services/api/s2-note.txt` untouched.

**ImpactSummary:** `services/api/main.go` gains one exported function and its `main()` body changes from an empty stub to a single print call; no other file in the package is affected, and the file remains the package's only non-test source file.

**Commit:** 2: add FormatGreeting with default-name fallback and wire into main
