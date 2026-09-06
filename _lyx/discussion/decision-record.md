# Decision record — glyph-demo-greet

## Goal

Give `services/api` a real, exercised greeting helper: add an exported function that
builds a short greeting string, call it from `main()`, then rename it to a name that
describes what it actually does. The package stops being an empty fixture stub and
becomes a small package that builds, runs, and has tests — without changing why it
exists (weft path-mirroring fixture).

## Scope

In scope:

- `services/api/main.go` — add the helper, wire it into `main()`, then rename it.
- `services/api/main_test.go` — a new bundled test file for the helper.

Out of scope:

- Adding a `go.mod` anywhere in the repo.
- New packages, new directories, or any restructuring of `services/api`.
- Any file outside `services/api/`.
- CI wiring, lint config, or a build script for the new verification commands.
- Changing `README.md` or the existing `services/api/s2-note.txt`.

## Decisions

**Final helper is `func FormatGreeting(name string) string`.**
Rationale: verb-led and honest about the return — it formats and returns a string
rather than performing a greeting. `Greet` reads as an action with a side effect,
which is exactly the vagueness the rename is meant to fix.

**Intermediate name is `Greet`; the rename lands `FormatGreeting`.**
Rationale: the task sequences add-then-rename as two ordered steps, and each state is
independently buildable and testable.

**The helper is exported.**
Rationale: the task asks for an exported helper, and the test file exercises it by name,
so the export cannot quietly become unexported without breaking the tests.

**Signature takes one `string`, returns one `string`, no `error`.**
Rationale: string formatting has no failure mode. An `error` return would be an
unreachable branch in every caller and in every test.

**Body is `fmt.Sprintf("Hello, %s!", name)`.**

**Empty `name` falls back to `"world"`, so `FormatGreeting("")` is `"Hello, world!"`.**
Rationale: `"Hello, !"` is visibly broken output for the one input a caller can pass by
accident. One `if` gives the helper the single behaviour actually worth asserting in a
test; without it the test file is a tautology over `Sprintf`.

**No trimming, no other normalisation.**
Rationale: only the empty string is a real accident. Whitespace-only names, casing, and
length limits are hypotheticals nobody asked for.

**`main()` calls `fmt.Println(FormatGreeting("lyx"))`.**
Rationale: a non-empty literal exercises the normal path in the binary and leaves the
empty-name default to the test, so the two paths are covered in different places rather
than both landing on `"world"`.

**The existing fixture comment on `main()` stays.**
Rationale: it records why `services/api` exists at all.

## Constraints

- No `go.mod` in this repo or any parent; every `go` verb must be prefixed with
  `GO111MODULE=off` or it fails before reaching the code.
- `go build` on a `main` package writes the executable into the working directory —
  a bare `GO111MODULE=off go build ./services/api/` drops an `api` binary at the repo
  root and dirties the worktree. Use `-o /dev/null` for a compile check, `-o` into a
  directory outside the repo when the binary has to be run, or prefer `go vet`.
- This repo is the host fixture for the Loomyard **weft** sandbox and is paired with
  `lyx-test-weft`; `services/api/` exists to exercise weft path mirroring. Its path
  layout must not move.
- `lyx` resolves against the current directory's own `_lyx/`, so all commands run from
  the repo root, never from `services/api/`.
- Code must be `gofmt`-clean.
- Everything outside the two files named in Scope is read-only for this task, including
  `_lyx/config/`, `_lyx/loom/`, and git history.

## Auto-mode assumptions

The session ran autonomously with no operator, so every decision above was self-answered.

Four of them are auto-picks with no operator preference behind them, and are the ones to
revisit first if the plan writer has better information: the greeting text
`"Hello, %s!"`, the greeted name `"lyx"`, the intermediate name `Greet`, and the
two-card split (add-and-wire, then rename) — the last being the weakest-evidence call in
this record.

## Open risks

- **Weft fixture assertions are not visible from this worktree.** If any test in
  `lyx-test-weft` asserts an exact file inventory for the mirrored `services/api/`
  subpath, the new `main_test.go` would trip it. Not checkable from here; commit
  `2fe7af9` already added `services/api/s2-note.txt` to this same directory without
  incident, which is evidence but not proof.

## Acceptance criteria

Final state of the tree:

1. `services/api/main.go` declares exactly one exported helper,
   `func FormatGreeting(name string) string`, carrying a doc comment that begins with
   `FormatGreeting`.
2. `main()` calls that helper and prints the result; running the built binary prints
   `Hello, lyx!` and exits 0.
3. No standalone `Greet` identifier survives anywhere:
   `grep -rnE '\bGreet\b' services/api` returns no matches (`FormatGreeting` does not
   match, since `Greeting` is not a word-boundary hit for `Greet`).
4. The fixture comment explaining why `services/api` exists is still present.
5. No file was added, moved, or deleted outside `services/api/main.go` and
   `services/api/main_test.go`.

Commands, all run from the repo root, all exiting 0:

6. `GO111MODULE=off go vet ./services/api/`
7. `GO111MODULE=off go test ./services/api/`
8. `gofmt -l services/api` prints nothing.
9. `git status --porcelain` shows only the two intended files — in particular no stray
   `api` binary at the repo root.
10. `OUT="$(mktemp -d)/api"; GO111MODULE=off go build -o "$OUT" ./services/api/ && "$OUT"`
    prints `Hello, lyx!` — this is what checks criterion 2. Building outside the repo is
    what keeps criterion 9 true; a bare `go build` would drop the binary at the root.

Must-cover test scenarios in `services/api/main_test.go`, table-driven:

11. Ordinary name: `FormatGreeting("lyx")` is `"Hello, lyx!"`.
12. Empty name defaults: `FormatGreeting("")` is `"Hello, world!"`.
13. Name passes through verbatim, spaces and all: `FormatGreeting("Ada Lovelace")` is
    `"Hello, Ada Lovelace!"`.

Intermediate state, if the rename lands as its own card:

14. At the end of the add-and-wire card, the helper is named `Greet`, `main()` and the
    test file both call it by that name, and criteria 6–10 already hold.

## Notes for the plan writer

Non-exhaustive; explore the tree yourself.

- `services/api/main.go` is four lines today: `package main`, a comment reading
  `// Dummy subpath fixture for weft relpath-mirroring tests.`, and an empty
  `func main() {}`. There is no import block yet — adding `fmt` means adding one.
- `services/api/` also holds `s2-note.txt`, an unrelated sandbox artifact. Leave it.
- The verification commands are hand-invoked; nothing in the repo needs updating to make
  them run.
- Card ordering: the rename card depends on the add-and-wire card. The rename touches
  three sites — the function declaration, its doc comment, and the call in `main()` —
  plus every reference in `main_test.go`.
