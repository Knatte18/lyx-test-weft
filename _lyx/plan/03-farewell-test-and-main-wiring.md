# Card 3 — Cover `ComposeFarewell` and print it from `main`

**Edit:**
- `services/api/main_test.go`
- `services/api#main`

**Uses:**
- `services/api#ComposeFarewell`

**Intent:** Close card 2's gap by giving `ComposeFarewell` both a test and a caller.

In `services/api/main_test.go`, add a table-driven `TestComposeFarewell` structurally
identical to `TestComposeGreeting`: its own literal `cases` slice of the same anonymous struct
(`name`, `want`), the same single loop, and the same `t.Errorf` format string with the
function name swapped. Do not refactor `TestComposeGreeting` or share a table between the two
— the duplicated six-line table is the cheaper read here. The three rows are `"lyx"` →
`"Goodbye, lyx!"`, `""` → `"Goodbye, world!"` (the default the helper exists for), and
`"Ada Lovelace"` → `"Goodbye, Ada Lovelace!"` (an embedded space passes through untouched).
The file keeps `testing` as its only import.

In `main()`, add a second `fmt.Println` so it prints `Hello, lyx!` and then `Goodbye, lyx!` on
separate lines, both from the existing `"lyx"` argument — two statements rather than one
combined call, so each line stays independently greppable. Leave the
`// Dummy subpath fixture …` comment above `main` in place.

**ImpactSummary:** `main` has no callers and no test asserts its stdout, and the new test function leaves `TestComposeGreeting` untouched, so both edits are additive and reach nothing outside `package main`.

**Commit:** `3: farewell-test-and-main-wiring`
