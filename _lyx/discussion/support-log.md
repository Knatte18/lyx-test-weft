## Interview

This session ran autonomously (no operator present). No interactive interview took place; all design points that would normally be asked were instead resolved as self-picks, recorded below in the Question ledger. Exploration of the codebase (Step 2) found:

- `services/api/main.go` is a one-line stub package (`package main`, empty `func main()`), with a comment noting it's a dummy subpath fixture for weft relpath-mirroring tests. No `FormatGreeting` helper exists yet, despite the task brief phrasing this as "extend."
- `services/api/s2-note.txt` is an unrelated leftover from a prior task (`S2: add services/api/s2-note.txt sandbox change`, per recent commit log) and is out of scope here.
- No `go.mod` exists anywhere in the repo — this is a bare fixture repo, not a working Go module.
- No `CONSTRAINTS.md` at the repo root.
- README.md was checked; it documents weft path-mirroring semantics, unrelated to this task's design.

## Rejected alternatives

- **Returning an error/second value from `FormatGreeting` (e.g. `(string, error)`) to signal empty-name fallback.** Rejected: the task brief explicitly wants a single exported function returning a greeting string; introducing an error return complicates the surface for no benefit since empty name is not an error condition.
- **Treating empty name as a panic/invalid-input case instead of a graceful fallback.** Rejected: the task brief is explicit that empty name should "still get a friendly greeting," i.e., graceful fallback, not rejection.
- **Skipping whitespace trimming (treating only the exact empty string `""` as missing).** Considered simpler, but rejected in favor of trimming since a whitespace-only name is a realistic near-miss for "no name supplied" and trimming is a one-line addition (`strings.TrimSpace`) that avoids a visibly broken greeting.
- **Wiring the module at `services/api/go.mod` (nested module) instead of a repo-root `go.mod`.** Rejected: the repo has no existing Go module structure to match, and `go build ./...`/`go test ./...` are phrased as running "in the worktree" (repo root), which is simplest with a single root-level module.

## Review rounds

_No rounds yet._

## Question ledger

- **Q: What should `FormatGreeting`'s exact signature and name be?**
  A (auto-pick): `func FormatGreeting(name string) string`. Directly matches the task brief's naming and "returning a greeting string" requirement.
- **Q: What is the default fallback name?**
  A (auto-pick): `"friend"`, as stated verbatim in the task brief.
- **Q: Should whitespace-only names also fall back to the default?**
  A (auto-pick): Yes, via `strings.TrimSpace` before the empty check. Judged in scope as a natural reading of "empty name," not an over-design.
- **Q: What greeting format/string should be produced?**
  A (auto-pick): `"Hello, <name>!"`. Simple, conventional, easy to assert on.
- **Q: How does `main.go` become a "real consumer"?**
  A (auto-pick): Call `FormatGreeting` and print the result via `fmt.Println`, rather than discarding the return value.
- **Q: Does a `go.mod` need to be created, and where?**
  A (auto-pick): Yes, at the repo root, since none exists and the acceptance criteria require `go build ./...` / `go test ./...` to succeed. Module name/Go version left as a note for the plan writer to confirm against the toolchain actually present.
