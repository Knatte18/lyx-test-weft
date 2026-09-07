# Card 1 — Extract the empty-name default into `defaultName`

**Create:**
- `plan:services/api#defaultName` -> `func defaultName(name string) string`

**Edit:**
- `services/api#ComposeGreeting`

**Intent:** `ComposeGreeting` inlines its own empty-name check, reassigning `name` to
`"world"` before formatting. Move that check into a new unexported `defaultName` placed
directly above `ComposeGreeting` in `services/api/main.go`: it returns `"world"` when
`name == ""` and `name` otherwise, handling the empty string only — a whitespace-only name
passes through untouched, exactly as today.

`ComposeGreeting` then drops both the `if` and the parameter reassignment and calls the
helper inline: `return fmt.Sprintf("Hello, %s!", defaultName(name))`. Its name, signature,
godoc comment, and output are all unchanged, so this is a behaviour-preserving refactor; the
existing `TestComposeGreeting` is the check on it and must pass unmodified. The helper stays
unexported and untested on its own — it is three lines with no caller outside `package main`,
fully exercised through the composers' empty-name rows.

No file is created, no import is added, and `main.go` keeps `fmt` as its only import.

**ImpactSummary:** `ComposeGreeting`'s body shrinks to a single `return`; its signature and output are unchanged, so no caller and no test needs updating.

**Commit:** `1: default-name-helper`
