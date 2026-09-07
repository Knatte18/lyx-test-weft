# Decision record — r4-crash-hub

## Goal

`services/api/main.go` exposes `ComposeGreeting(name string) string`, which inlines its own
empty-name check. Add a symmetric farewell path: factor the empty-name default into an
unexported helper, add `ComposeFarewell`, cover it with a table-driven test, and print both
lines from `main()`. Delivered as three independently-committable steps, each compiling and
passing the test suite on its own.

## Scope

In scope — exactly two files change:

- `services/api/main.go`
  - new unexported `defaultName(name string) string`
  - `ComposeGreeting` rewritten to call it
  - new exported `ComposeFarewell(name string) string`
  - `main()` prints greeting and farewell
- `services/api/main_test.go`
  - new table-driven `TestComposeFarewell`

Out of scope:

- Adding `go.mod` or any other new file, anywhere in the repo.
- New packages, new directories, moving code out of `package main`.
- Touching `README.md`, `.gitignore`, `_lyx/`, or `.lyx/`.
- Renaming, resignaturing, or behaviourally changing `ComposeGreeting`.
- Refactoring `TestComposeGreeting`, or sharing a table between the two tests.
- Trimming, casing, validating, or length-capping names; error returns; i18n; a
  caller-supplied default; a template or format parameter.

## Decisions

**D1 — Three commits, one per brief step, in brief order.**
Rationale: the brief specifies the split, and each step is independently green. Follows the
existing commit-message convention on this branch (`1: format-greeting-helper`,
`2: main-greeting-wiring`): `<step-number>: <kebab-slug>`.

**D2 — `defaultName` stays unexported, in `services/api/main.go`, above `ComposeGreeting`.**
Rationale: a package-internal detail with no caller outside `package main`. Same file keeps
the "no new files" rule intact.

**D3 — `defaultName` handles the empty string only.**
`return "world"` when `name == ""`, `name` otherwise. Whitespace-only names pass through
unchanged, matching today's `ComposeGreeting` behaviour exactly.
Rationale: preserves current behaviour bit-for-bit; trimming would be an unrequested
behaviour change smuggled in under a refactor.

**D4 — Both composers call the helper inline inside `fmt.Sprintf`.**
`return fmt.Sprintf("Hello, %s!", defaultName(name))` and
`return fmt.Sprintf("Goodbye, %s!", defaultName(name))`.
Rationale: drops the parameter mutation `ComposeGreeting` does today and makes the two
functions structurally identical, so a reader sees at a glance that they share one default.

**D5 — `ComposeFarewell` mirrors `ComposeGreeting`'s shape.**
Exported, single `string` argument, single `string` return, no error, `fmt.Sprintf` with the
literal `"Goodbye, %s!"`, godoc comment opening with the identifier
(`// ComposeFarewell returns a farewell for name, defaulting to "world" when name is empty.`).
Rationale: the file's established idiom; a divergent shape would be the only surprise here.

**D6 — `TestComposeFarewell` mirrors `TestComposeGreeting` structurally, with its own literal table.**
Same anonymous-struct fields (`name`, `want`), same three inputs (`"lyx"`, `""`,
`"Ada Lovelace"`), same single-loop body, same `t.Errorf` format string with the function name
swapped.
Rationale: duplication of a six-line table is cheaper to read than a shared fixture, and it
keeps step 3's diff purely additive apart from the `main()` change.

**D7 — No direct test for `defaultName`.**
Rationale: unexported, three lines, fully exercised through both composers' empty-name rows.

**D8 — `main()` prints two lines via two `fmt.Println` calls**, greeting first, farewell
second, both with the existing `"lyx"` argument. The `// Dummy subpath fixture …` comment on
`main` stays.
Rationale: matches how the greeting line was wired in `ed1263a`; two statements keep each
line independently greppable.

**D9 — Verify with `GO111MODULE=off go test ./...` run from `services/api`.**
Also run `gofmt -l services/api` and expect empty output.
Rationale: see C2 — the repo has no `go.mod`, so the brief's literal `go test ./...` cannot
run in module mode. GOPATH mode compiles and tests the package as-is and exits 0 today,
verified before this record was written.

## Constraints

**C1 — No new files.** The brief forbids them. This rules out `go.mod`, a separate
`farewell.go`, and a separate `farewell_test.go`.

**C2 — The repo has no `go.mod`.** From the repo root, `go test ./...` fails with
`directory prefix . does not contain main module or its selected dependencies` — a
pre-existing property of the fixture, not something this task introduces or may fix (C1).
Every "must pass `go test ./...`" obligation in the brief is satisfied via D9's GOPATH-mode
invocation.

**C3 — Each of the three commits must compile and pass tests standalone.** Step 1 is a
behaviour-preserving refactor; step 2 adds an unreferenced-but-exported function (legal in
Go, no unused-symbol error); step 3 adds its test and the `main()` wiring together.

**C4 — Package stays `package main` with `fmt` as its only import.** No new imports.

**C5 — Existing public behaviour is frozen.** `ComposeGreeting("")` returns `"Hello, world!"`
and `TestComposeGreeting` passes unmodified after every step.

## Auto-mode assumptions

This session ran autonomously; no operator answered. Every decision above is a self-pick.
The assumptions behind them:

- A1 — The brief's three-step split is prescriptive, not a suggestion; it is reproduced
  verbatim as the commit plan rather than collapsed into one commit.
- A2 — "the same three cases the existing `TestComposeGreeting` covers" means the same three
  *inputs*, with the expected strings adjusted from `Hello` to `Goodbye`.
- A3 — `main()` printing "both the greeting and the farewell" means two separate output
  lines, not one concatenated line.
- A4 — The literal `go test ./...` in the brief means "the package's tests pass", not "the
  fixture must be converted to a Go module".
- A5 — `world` is the default for the farewell too; the brief's "uses the same `defaultName`
  helper" leaves no room for a different default.

## Open risks

- R1 — A reviewer reading the brief literally may flag that `go test ./...` from the repo
  root still fails. It fails identically before and after this task; fixing it needs a
  `go.mod`, which C1 forbids. Flagged, not fixed.
- R2 — D4 changes `ComposeGreeting`'s body beyond the minimum (it removes the `name = …`
  reassignment as well as the `if`). Behaviour is unchanged and C5 guards it, but the step-1
  diff is two lines larger than a strictly minimal edit.
- R3 — Step 2 lands `ComposeFarewell` with no test and no caller. Intentional per the brief's
  ordering; it is transient, closed by step 3.

## Acceptance criteria

After step 1:

- `defaultName` exists in `services/api/main.go`, unexported, `func(string) string`.
- `ComposeGreeting` contains no `if name == ""`; it delegates to `defaultName`.
- `TestComposeGreeting` passes unmodified.

After step 2:

- `ComposeFarewell("x")` returns `"Goodbye, x!"`; the function calls `defaultName`, and the
  empty-check is not re-inlined.
- The package still builds; `TestComposeGreeting` still passes.

After step 3 — `TestComposeFarewell` is table-driven and must cover:

- `"lyx"` → `"Goodbye, lyx!"` (ordinary name)
- `""` → `"Goodbye, world!"` (empty-name default, the helper's whole purpose)
- `"Ada Lovelace"` → `"Goodbye, Ada Lovelace!"` (embedded space passes through untouched)

and:

- `main()` prints `Hello, lyx!` then `Goodbye, lyx!`, in that order, on separate lines.
- `GO111MODULE=off go test ./...` from `services/api` exits 0 at **each** of the three
  commits, not only the last.
- `gofmt -l services/api` prints nothing at each of the three commits.
- `git show --stat` for each commit touches only `services/api/main.go` and
  `services/api/main_test.go`; no other path appears in any of the three.

## Notes for the plan writer

Not exhaustive — explore the files yourself.

- `services/api/main.go` is ~15 lines: `package main`, `import "fmt"`, `main()`,
  `ComposeGreeting`. `services/api/main_test.go` holds the single table-driven
  `TestComposeGreeting` to copy the shape from.
- Branch `r4-crash-hub`; its three most recent commits are the sibling greeting task and
  model the `<n>: <slug>` message convention.
- Run test/gofmt commands from `services/api`, with `GO111MODULE=off` (D9). Plain
  `go test ./...` at the repo root will fail for reasons unrelated to this change.
