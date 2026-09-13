## Goal

Give `services/api` a `FormatGreeting` helper that produces a friendly greeting string, falling back to a default name when the caller passes an empty name, and wire it into `main.go` so the package has a real consumer.

## Scope

In:
- A `FormatGreeting(name string) string` function in `services/api`.
- Empty-name fallback to the default name `"friend"`.
- A table-driven unit test covering the empty-name fallback and an ordinary name.
- A call from `main.go` so the function is exercised by the package's real entry point.
- A `go.mod` for the module, since none exists in the repo yet and `go build ./...` / `go test ./...` need one.

Out:
- Any I/O, CLI flag parsing, or printing beyond what's needed to call the helper from `main`.
- Localization, pluralization, or multiple greeting formats.
- Any other package or service beyond `services/api`.

## Decisions

- **Function name and signature: `func FormatGreeting(name string) string`.**
  Rationale: matches the task brief exactly ("FormatGreeting helper"), and a single string-in/string-out function is the smallest exported surface that satisfies "one exported function returning a greeting string."
- **Default name: the literal `"friend"`.**
  Rationale: specified verbatim in the task brief.
- **Empty-name detection: trim whitespace, then check for empty string.**
  Rationale: a name of all-whitespace is effectively "no name supplied," and trimming avoids a greeting like "Hello,   !". Untrimmed input is otherwise used as-is (no other normalization, e.g. no case-folding) to keep the surface minimal.
- **Greeting format: `"Hello, <name>!"`.**
  Rationale: simplest conventional greeting shape, easy to assert on in a table-driven test.
- **Module setup: add a minimal `go.mod` at the repo root (module `dummy-r2-greet`, matching Go version available in the environment).**
  Rationale: no `go.mod` currently exists anywhere in the repo, but the acceptance criteria require `go build ./...` and `go test ./...` to pass — one must be created for those commands to run at all.
- **Test file: `services/api/main_test.go`, table-driven, covering an empty-name case and an ordinary-name case.**
  Rationale: satisfies the acceptance criterion directly; co-locating with `main.go` matches the existing single-file package.
- **`main.go` consumer: call `FormatGreeting` with a hardcoded or empty-string argument and use the result (e.g. assign to `_` is not sufficient — print it) so the call isn't dead code.**
  Rationale: task requires "the helper is called from main.go so the package has a real consumer"; printing is the simplest way to make the call observably real without adding CLI parsing scope.

## Constraints

- Must build with `go build ./...` and pass `go test ./...` from the repo root (or module root) in the worktree.
- Keep the exported surface to exactly one function (`FormatGreeting`).
- No new dependencies — standard library only (`strings`, `fmt`).

## Auto-mode assumptions

- This session ran without an operator; all decisions above were made by best judgment per the task brief and are logged as auto-picks in the support log's Question ledger.
- No `CONSTRAINTS.md` exists in the repo, so no project-wide constraints apply beyond what's stated in the task brief.

## Open risks

- No `go.mod` currently exists in the repo — the plan writer needs to determine the correct module path and Go version to declare, since none was previously established as precedent.
- `s2-note.txt` already exists in `services/api` as an unrelated sandbox artifact from a prior task (`S2`); it should be left untouched.

## Acceptance criteria

- `go build ./...` succeeds in the worktree.
- `go test ./...` succeeds in the worktree.
- `FormatGreeting("")` (and whitespace-only input) returns a greeting containing the default name `"friend"`.
- `FormatGreeting("Alice")` (an ordinary non-empty name) returns a greeting containing `"Alice"`, not the default.
- `main.go` contains a real call to `FormatGreeting` whose result is used (not discarded).
- Exactly one exported function exists in the package (`FormatGreeting`).

## Notes for the plan writer

- See Open risks for the missing-`go.mod` risk; plan should include creating one before `go build`/`go test` will work.
- `services/api/main.go` is presently a one-line stub (`package main` + empty `func main() {}`); it needs both the new function and an updated `main` body.
