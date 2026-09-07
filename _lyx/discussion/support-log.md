# Support log — glyph-rename-format

## Interview

No operator was available: the session ran autonomously, so the interview below
is a self-conducted pass. Each batch records the question posed, the recommended
answer, and the pick that was taken.

**Batch 0 — is this the right thing to build?**
Challenged the task itself before designing it. `FormatGreeting` does two things
a reader would not predict from the name: it substitutes a default for an empty
name and it builds the whole sentence. "Compose" covers both; "format" implies
the sentence already exists and is merely being rendered. The rename is
justified, cheap, and total — there are no external consumers to break. Proceed.

**Batch 1 — scope boundaries.**
Asked what counts as "every reference". Four shapes exist in the two Go files:
declaration, doc comment, call expressions, and the identifier as text inside
the test's failure-message format strings. Recommended treating all four as in
scope, and the test function's own name with them. Also asked whether the
absent `go.mod` should be added so the suite runs in place — recommended no,
because the repository is a weft fixture whose file inventory is itself
load-bearing for other tests.

**Batch 2 — constraints.**
Established that the work sits inside one module boundary, the `services/api`
package, and conflicts with no existing pattern: there is no rename ledger, no
deprecation convention, and no other caller anywhere in the tree. `go1.26.0` is
present. No `CONSTRAINTS.md` exists at the repo root. Behaviour must be
bit-for-bit preserved.

**Batch 3 — architecture, at the coarse level allowed here.**
Confirmed the change is confined to one package with no cross-package call
graph. Deliberately did not pin signatures, line numbers, or an exhaustive
reference list — that class of fact is recomputed at Plan time.

**Batch 4 — edge cases.**
Walked failure modes. Partial rename that still compiles: possible only if a
reference lived outside the two Go files, closed by a grep census. Case-variant
or unexported twin (`formatGreeting`): none exists. Collateral damage from a
repo-wide substitution: avoided by editing per occurrence. Concurrency, empty
state, and invalid input do not apply — the function is pure and its table
already covers the empty-name default. Nothing about the rename changes any of
those paths.

**Batch 5 — security.**
No trust boundary, no input validation, no untrusted data. Recorded as not
applicable rather than padded with a section.

**Batch 6 — verification.**
Asked how the change can be proved correct given the missing module.
Recommended and probed a scratchpad copy plus a throwaway `go.mod`; the probe
ran green during discussion, and the direct in-worktree run failed with the
expected setup error. Paired that with in-worktree `gofmt` and a grep census, so
the checks that run against the real files still say something.

## Rejected alternatives

- **Keep `FormatGreeting` as a deprecated alias forwarding to
  `ComposeGreeting`.** Rejected: the board brief forbids new symbols, and with
  every caller inside this repository an alias buys nothing but a second name
  for one behaviour.
- **Add `go.mod` to the repository so `go test` runs in place.** Rejected: the
  repository is a weft path-mirroring fixture whose file inventory other tests
  depend on. Adding a build file to make verification more convenient changes
  the thing being tested by other tooling.
- **Repo-wide `sed -i` (or `gofmt -r`) substitution of the identifier.**
  Rejected on two grounds: the operator's standing instruction bans `sed`, and a
  blanket rewrite risks touching fixture files that must stay byte-identical.
  Per-occurrence edits keep the diff exactly as wide as the rename.
- **A rename tool (`gopls rename` / `gorename`).** Rejected: both want a module
  to resolve packages, which this tree does not have, so the tool would need the
  same scaffolding that was already rejected above.
- **Broaden the rename into a small cleanup — rewording the doc comment, adding
  a test case.** Rejected under YAGNI and the brief's "pure rename" framing.
  Nobody asked, and it would blur the diff.
- **Leave the test function named `TestFormatGreeting`.** Rejected: it would
  leave the old name in the very file the brief says to update, pointing at a
  symbol that no longer exists.

## Review rounds

_No rounds yet._

## Question ledger

All entries below are auto-picks: the session ran autonomously with no operator
to answer, per Step 4.

| # | Question | Pick | Status |
|---|----------|------|--------|
| Q1 | Is the rename worth doing at all? | Yes — the old name under-describes both the defaulting and the sentence construction. | Resolved (auto-pick) |
| Q2 | Does "every reference in the test" include the test function's own name? | Yes — Go pairs `TestXxx` with `Xxx`, and a stale test name misleads. | Resolved (auto-pick) |
| Q3 | Does it include the identifier inside the failure-message format strings? | Yes — those strings are read by a human debugging a failure. | Resolved (auto-pick) |
| Q4 | Keep a compatibility alias under the old name? | No — the brief forbids new symbols and there are no external consumers. | Resolved (auto-pick) |
| Q5 | Update the doc comment? | Leading word only; the description after it stays verbatim. | Resolved (auto-pick) |
| Q6 | Add `go.mod` so the suite runs in the worktree? | No — verify on a scratchpad copy with a throwaway module instead. | Resolved (auto-pick) |
| Q7 | How is the rename applied? | Per-occurrence editing-tool edits, never a repo-wide substitution. | Resolved (auto-pick) |
| Q8 | Any changes to the test table? | None — behaviour is unchanged, so the three existing cases stand. | Resolved (auto-pick) |
| Q9 | Is a security section warranted? | No — pure function, no trust boundary, no input validation. | Resolved (auto-pick, N/A) |
| Q10 | Who commits the result? | The loop owner. The deliverable is the worktree state. | Resolved (auto-pick) |

No environment faults were encountered. `lyx board get` returned a live task,
and the absent `go.mod` is a property of this fixture repository, not a broken
tool — it is recorded as a constraint, not repaired.
