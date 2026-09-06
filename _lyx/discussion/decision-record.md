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
Rationale: the task specifies add-then-rename as two ordered steps. `Greet` is a
plausible first-draft name a developer would actually write, so the rename is a real
improvement rather than a staged token swap.

**The helper is exported.**
Rationale: the task asks for an exported helper. Exporting from `package main` buys
nothing at link time, but it is what was specified, it is what the test file exercises
by name, and `go vet` does not object.

**Signature takes one `string`, returns one `string`, no `error`.**
Rationale: string formatting has no failure mode. An `error` return would be an
unreachable branch in every caller and in every test.

**Body is `fmt.Sprintf("Hello, %s!", name)`.**
Rationale: `fmt` is imported regardless because `main()` prints the result, so
`Sprintf` costs no new dependency and reads more clearly than concatenation at this
size.

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
Rationale: it records why `services/api` exists at all. Deleting it loses the only
in-repo explanation of the package's purpose to a task that has nothing to do with it.

**Verification runs under `GO111MODULE=off`.**
Rationale: the repo has no `go.mod` at any level, so module-mode `go build`, `go vet`,
and `go test` all fail with `go.mod file not found`. In GOPATH mode all three succeed
against this package today (verified on go1.26.0 in this worktree). Adding a `go.mod` to
make module mode work would put a new file at a path the task excludes and would change
the shape of a fixture repo other tests depend on.

**A bundled `main_test.go` is included.**
Rationale: it is permitted by the task and, given GOPATH mode works, the tests actually
run rather than sitting unrunnable in the tree.

## Constraints

- No `go.mod` in this repo or any parent; every `go` verb must be prefixed with
  `GO111MODULE=off` or it fails before reaching the code.
- `go build` on a `main` package writes the executable into the working directory —
  a bare `GO111MODULE=off go build ./services/api/` drops an `api` binary at the repo
  root and dirties the worktree. Use `-o /dev/null`, or prefer `go vet`.
- This repo is the host fixture for the Loomyard **weft** sandbox and is paired with
  `lyx-test-weft`; `services/api/` exists to exercise weft path mirroring. Its path
  layout must not move.
- `lyx` resolves against the current directory's own `_lyx/`, so all commands run from
  the repo root, never from `services/api/`.
- Code must be `gofmt`-clean.
- Everything outside the two files named in Scope is read-only for this task, including
  `_lyx/config/`, `_lyx/loom/`, and git history.

## Auto-mode assumptions

The session ran autonomously with no operator; every question below was self-answered.

- The rename is a genuine second step, not a cosmetic one: the tree passes at the
  `Greet` state and again at the `FormatGreeting` state.
- The work splits into two ordered cards (add-and-wire, then rename) rather than one
  card containing both edits, because the task states the rename as a follow-on
  ("Once that is in place") and each state is independently buildable and testable.
- `"Hello, %s!"` is the greeting text. No operator preference was available; anything
  short and conventional satisfies "a short greeting message".
- `"lyx"` is the name `main()` greets. Arbitrary; only requirement is that it is not
  empty, so the printed output does not coincide with the empty-name default.
- Adding `main_test.go` to `services/api/` does not disturb the weft fixture. Supporting
  evidence: commit `2fe7af9` already added `services/api/s2-note.txt` to this directory
  as a sandbox change without incident.

## Open risks

- **GOPATH mode is deprecated.** `GO111MODULE=off` works on go1.26.0 here, but it is a
  legacy path. If a future toolchain drops it, every verification command in this record
  stops working and the repo would need a `go.mod` — a decision outside this task.
- **Weft fixture assertions are not visible from this worktree.** If any test in
  `lyx-test-weft` asserts an exact file inventory for the mirrored `services/api/`
  subpath, the new `main_test.go` would trip it. Not checkable from here; the
  `s2-note.txt` precedent is evidence but not proof.
- **`services/api` is `package main` with an exported symbol.** Correct per the task,
  but a future reviewer applying ordinary Go style may flag the export as pointless and
  "fix" it, breaking the test file that calls it by name.

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

Must-cover test scenarios in `services/api/main_test.go`, table-driven:

10. Ordinary name: `FormatGreeting("lyx")` is `"Hello, lyx!"`.
11. Empty name defaults: `FormatGreeting("")` is `"Hello, world!"`.
12. Name passes through verbatim, spaces and all: `FormatGreeting("Ada Lovelace")` is
    `"Hello, Ada Lovelace!"`.

Intermediate state, if the rename lands as its own card:

13. At the end of the add-and-wire card, the helper is named `Greet`, `main()` and the
    test file both call it by that name, and criteria 6–9 already hold.

## Notes for the plan writer

Non-exhaustive; explore the tree yourself.

- `services/api/main.go` is four lines today: `package main`, a comment reading
  `// Dummy subpath fixture for weft relpath-mirroring tests.`, and an empty
  `func main() {}`. There is no import block yet — adding `fmt` means adding one.
- `services/api/` also holds `s2-note.txt`, an unrelated sandbox artifact. Leave it.
- There is no `go.mod`, no CI config, no lint config, and no build script in this repo.
  Nothing needs updating to make the new verification commands run; they are
  hand-invoked.
- Card ordering: the rename card depends on the add-and-wire card. The rename touches
  three sites — the function declaration, its doc comment, and the call in `main()` —
  plus every reference in `main_test.go`.
