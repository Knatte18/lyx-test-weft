---
format: 5
approved: false
language: go
---

# Plan: give `services/api` a real greeting helper

`services/api` is a four-line stub — a package declaration, a comment recording that the
directory exists to exercise weft path mirroring, and an empty `main()`. Give it an
exported helper that builds a short greeting string, bundle a table-driven test in the
same commit, then wire the call into `main()` so the binary prints something.

Nothing outside `services/api/main.go` and `services/api/main_test.go` changes. No
`go.mod` is added, no directory moves — the path layout is the fixture, and
`lyx-test-weft` mirrors it.

## Card Index

1 — format-greeting-helper — add the exported FormatGreeting helper and its bundled test
2 — main-greeting-wiring — call the helper from main() so the binary prints Hello, lyx!

## Shared Decisions

### Decision: final-name-lands-directly

- **Decision:** the helper is created as `FormatGreeting` in card 1. There is no
  intermediate `Greet` and no rename card, and the two cards split on
  helper-versus-caller instead.
- **Rationale:** the decision record sequences add-then-rename, but this plan format
  cannot express it: a `Rename` pair's `Old` side must resolve against the current
  worktree (`rename-old-unresolved`), so a symbol the same plan creates can never be a
  later card's rename source. The record names the two-card split as its
  weakest-evidence auto-pick and invites revision, and its acceptance criteria are
  unaffected — the final state still declares exactly one exported
  `FormatGreeting`, and "no standalone `Greet` survives" holds trivially because no
  `Greet` is ever written. The helper/caller split keeps what the original split was
  for: two states that each build, test, and commit on their own.
- **Applies to:** all cards

### Decision: gomodule-off-and-no-stray-binary

- **Decision:** every `go` verb is prefixed `GO111MODULE=off`, every command runs from
  the repo root, and a `go build` of this `main` package always targets `-o /dev/null`
  or a path outside the repo — never a bare `go build ./services/api/`.
- **Rationale:** there is no `go.mod` in this repo or any parent, so an unprefixed `go`
  verb fails before it reaches the code; and a bare `go build` writes an `api`
  executable into the working directory, dirtying the worktree with an untracked binary
  at the repo root. `lyx` also resolves against the current directory's own `_lyx/`, so
  it only works from the root.
- **Applies to:** all cards

### Decision: empty-name-defaults-to-world

- **Decision:** the helper's body is `fmt.Sprintf("Hello, %s!", name)` guarded by one
  `if` that substitutes `"world"` for an empty `name`. No trimming, no casing rules, no
  length limit.
- **Rationale:** `"Hello, !"` is visibly broken output for the one input a caller can
  pass by accident, and that single branch is the only behaviour worth asserting —
  without it the test file is a tautology over `Sprintf`. Whitespace-only names and
  casing are hypotheticals nobody asked for.
- **Applies to:** all cards

## verify:

GO111MODULE=off go vet ./services/api/
GO111MODULE=off go test ./services/api/
test -z "$(gofmt -l services/api)"
OUT="$(mktemp -d)/api"; GO111MODULE=off go build -o "$OUT" ./services/api/ && test "$("$OUT")" = "Hello, lyx!"
