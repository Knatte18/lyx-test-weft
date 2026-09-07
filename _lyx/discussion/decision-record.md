# Decision record — glyph-rename-format

## Goal

Rename the exported greeting helper in `services/api` from `FormatGreeting` to
`ComposeGreeting`, so the name describes what the function actually does: it
composes the whole greeting sentence rather than formatting a pre-existing one.
Nothing else about the program changes.

## Scope

In scope:

- The function declaration and its doc comment in `services/api/main.go`.
- The call site inside `main()`.
- Every reference in the existing table-driven test in
  `services/api/main_test.go`: the test function's own name, the call under
  test, and the function name embedded in the failure-message format strings.

Out of scope:

- Any change to the signature, parameter name, return type, or behaviour.
- Any new symbol beyond the renamed one; no alias, no deprecated shim, no
  wrapper kept under the old name.
- Adding `go.mod` or any other build scaffolding to the repository.
- `services/api/s2-note.txt`, `README.md`, `_lyx/`, and every other file in the
  worktree.
- Test-table changes: no new cases, no altered expectations.

## Decisions

**D1 — Rename in place; no compatibility alias.**
The old name is deleted outright rather than retained as a thin forwarder.
Rationale: the helper has a small, fully enumerable set of in-repo callers and
no external consumers; a retained alias would defeat the point of the rename and
add a symbol the task explicitly forbids.

**D2 — The test function is renamed too: `TestFormatGreeting` → `TestComposeGreeting`.**
Rationale: Go's convention pairs `TestXxx` with the `Xxx` under test, and the
board brief puts every reference in the test inside scope. A test whose name
still points at a symbol that no longer exists is a stale signpost.

**D3 — The function name inside the test's failure-message format strings is
updated as well.**
Rationale: those strings are user-facing output on failure. A failure message
naming a function that no longer exists sends a future reader hunting for the
wrong symbol.

**D4 — The doc comment's leading word is retargeted; the rest of the sentence is
left verbatim.**
Rationale: Go requires a doc comment to begin with the declared name, so the
first word must change. The description after it is still accurate, and
rewriting it would turn a pure rename into an editorial pass.

**D5 — Surgical per-occurrence identifier retargeting, using the editing tools
rather than a repo-wide substitution.**
Rationale: the task calls for preserving git history. Touching only the lines
that carry the identifier keeps the diff minimal and blame legible, and it rules
out collateral hits (the fixture files under `services/api/` and `_lyx/` must
stay byte-identical).

**D6 — Compile-and-test verification runs on a throwaway copy outside the
worktree.**
Rationale: the repository has no `go.mod`, so `go test` and `go vet` refuse to
run in place. Copying the two Go files into the session scratchpad alongside a
temporary module file makes the test suite runnable without adding build
scaffolding to a fixture repo whose file inventory is itself under test by
other tooling. Confirmed working during discussion.

**D7 — In-worktree checks are `gofmt` cleanliness plus a grep census.**
Rationale: these are the two checks that can run against the real files. `gofmt`
catches a syntactically broken edit; the grep census proves the rename is total
(zero occurrences of the old identifier) rather than partial.

## Constraints

- The repository is a fixture host repo for the weft sandbox, not a product
  codebase. Its file inventory and subpath layout are load-bearing for other
  tests: do not add, move, or delete files.
- No Go module is defined anywhere in the tree, and none may be introduced.
- No `CONSTRAINTS.md` exists at the repo root.
- The Go toolchain available in this environment is go1.26.0.
- The change is confined to one module boundary: the `services/api` package.
  It touches no other package, and there is no cross-package call graph to
  reason about.
- Behaviour is bit-for-bit preserved: the same greeting strings, the same
  empty-name default of `"world"`.

## Auto-mode assumptions

This session ran with no operator available, so every decision above is a
self-pick. The assumptions behind them:

- **A1** — "Every reference in its existing test" is read to include the test
  function's own name and the identifier inside its format strings, not merely
  the call expression. A narrower reading would leave the old name visible in
  the file the brief singles out.
- **A2** — "No new symbols beyond the renamed one" forbids a compatibility
  alias, rather than merely discouraging one.
- **A3** — The doc comment is treated as part of the identifier's surface, so
  updating its leading word is inside a "pure rename", not a behaviour change.
- **A4** — Nobody outside this repository imports the symbol. The package is
  `package main` in a fixture repo with no module path, so it is not importable
  by anything.
- **A5** — Committing the change is the loop owner's job. The deliverable is the
  worktree state.

## Open risks

- **R1 (low)** — Automated verification is indirect: the suite runs on a
  scratchpad copy, not on the worktree files themselves. A divergence between
  copy and original would hide a defect. Mitigated by copying immediately before
  the run and by the in-worktree `gofmt` and grep checks.
- **R2 (low)** — If any tooling outside this repository greps for the literal
  string `FormatGreeting` in this fixture, the rename breaks it. Nothing in this
  worktree does, and the board brief commissions the rename, so this is
  recorded rather than mitigated.
- **R3 (very low)** — A partial rename that still compiles is possible in
  principle only if some reference lived outside the two Go files. The grep
  census in the acceptance criteria closes this.

## Acceptance criteria

1. `grep -rn FormatGreeting` across the worktree, excluding `.git`, returns no
   matches — in code, comments, test names, and string literals alike.
2. Every reference that previously named the old helper now names
   `ComposeGreeting`, and the count of references is unchanged: nothing was
   dropped, nothing was duplicated.
3. `services/api/main.go` and `services/api/main_test.go` are the only files
   modified. `git status` shows no other change, and no file added or removed.
4. The function's signature, body, and the doc comment text following the
   leading identifier are byte-identical to before.
5. The doc comment begins with `ComposeGreeting`.
6. `gofmt -l services/api` prints nothing.
7. The test suite passes on a scratchpad copy of the two Go files with a
   throwaway `go.mod`, exercising the existing three-case table unchanged:
   a named greeting, the empty-name default to `"world"`, and a
   multi-word name.
8. The test function is named `TestComposeGreeting`, and its failure messages
   name `ComposeGreeting`.
9. No `go.mod` or other new file exists in the worktree when the work is done —
   including no leftover scratch artifacts inside the repository.

## Notes for the plan writer

Explore the tree yourself; this is a head start, not an inventory.

- The rename surface is small — a single-digit number of references, all inside
  `services/api/`. Recount them fresh rather than trusting that description.
- References fall into four shapes, and it is easy to fix the first and forget
  the rest: the declaration, the doc comment's leading word, call expressions,
  and the identifier as text inside the test's format strings.
- `go test` and `go vet` will fail in the worktree with a "does not contain main
  module" setup error. That is the absent `go.mod`, not a defect in the change;
  see D6 for the verification route.
- `_lyx/` holds live driver configuration and loom orchestration state. It is
  read-only to every phase of this task.
