# Card 1 — format-greeting-helper

**Create:**
- `plan:services/api#FormatGreeting` -> `func FormatGreeting(name string) string`
- `services/api/main_test.go`

**Intent:** Give `services/api` its one piece of real behaviour. Add an exported helper
`FormatGreeting(name string) string` to `services/api/main.go`, returning
`fmt.Sprintf("Hello, %s!", name)`, guarded by a single `if` that substitutes `"world"`
for an empty `name` — so `FormatGreeting("")` is `"Hello, world!"` rather than the
visibly broken `"Hello, !"`. That guard is the only behaviour worth asserting; without
it the test file is a tautology over `Sprintf`. No trimming, no casing rules, no length
limit — only the empty string is a real accident.

The name is verb-led and honest about the return: the function formats and returns a
string rather than performing a greeting. The signature takes one `string` and returns
one `string` with no `error`, because string formatting has no failure mode and an
`error` return would be an unreachable branch in every caller and every test. The helper
is exported because the test file exercises it by name.

Two mechanical details in `main.go`: the file has no import block yet, so `fmt` needs
one; and the doc comment on the helper must begin with `FormatGreeting`. Leave
`func main() {}` empty — card 2 wires the call — and leave the existing
`// Dummy subpath fixture for weft relpath-mirroring tests.` comment alone, since it
records why this directory exists at all. An exported function with no caller in its own
package compiles cleanly, so this card builds and tests on its own.

`services/api/main_test.go` is new, `package main`, and table-driven over exactly three
rows: `FormatGreeting("lyx")` is `"Hello, lyx!"`, `FormatGreeting("")` is
`"Hello, world!"`, and `FormatGreeting("Ada Lovelace")` is `"Hello, Ada Lovelace!"` — the
name passes through verbatim, spaces and all.
