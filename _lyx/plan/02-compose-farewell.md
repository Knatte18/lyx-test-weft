# Card 2 — Add `ComposeFarewell`

**Create:**
- `plan:services/api#ComposeFarewell` -> `func ComposeFarewell(name string) string`

**Uses:**
- `services/api#defaultName`

**Intent:** Add an exported `ComposeFarewell` to `services/api/main.go`, mirroring
`ComposeGreeting`'s shape point for point: one `string` argument, one `string` return, no
error, and a single `return fmt.Sprintf("Goodbye, %s!", defaultName(name))`. It reuses card
1's helper rather than re-inlining the empty-name check, so both composers visibly share one
default.

Open it with a godoc comment that starts with the identifier, matching the file's idiom:
`// ComposeFarewell returns a farewell for name, defaulting to "world" when name is empty.`

The function lands here with neither a caller nor a test — card 3 adds both. That is
deliberate and transient: an exported, unreferenced function compiles cleanly in Go, so the
package still builds and `TestComposeGreeting` still passes at this commit.

**Commit:** `2: compose-farewell`
