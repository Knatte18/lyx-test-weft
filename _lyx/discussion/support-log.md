# Support log — r4-crash-hub

## Interview

No operator was present; the session ran autonomously. What follows is the interview as it
was conducted against the codebase and the board brief, batch by batch, with each question's
recommendation and the resolution taken.

**Batch 0 — reading the ground.** Board entry read via `lyx board get`. Repo explored
read-only: `README.md` (fixture host repo for the Loomyard weft sandbox), `services/api/`
(two Go files, ~40 lines total), `git log` (the previous greeting task landed as
`1: format-greeting-helper` / `2: main-greeting-wiring` / `1: rename FormatGreeting to
ComposeGreeting`). No `CONSTRAINTS.md` at the repo root. Two facts surfaced that the brief
does not mention: there is **no `go.mod` anywhere in the repo**, and `go test ./...` from the
repo root therefore fails outright with `directory prefix . does not contain main module`.
`GO111MODULE=off go test ./...` from `services/api` was tried and exits 0.

**Batch 1 — is this the right thing to build?** Challenged the task itself: a farewell
function nobody calls is speculative surface. Resolution — it is not speculative here: step 3
wires it into `main()`, so the feature ships with its caller inside the same task. The brief
is a fixture exercise with a concrete, complete end state. Build it as specified. Separately
challenged the three-step split (why not one commit?) — kept, because the brief prescribes it
and each step is genuinely green on its own; collapsing would be the agent overriding an
explicit instruction for convenience.

**Batch 2 — scope boundaries.** Confirmed the "no other files" rule bites in exactly one
place worth naming: it forbids adding `go.mod`, which is the natural instinct on seeing C2's
failure. Held the line; recorded the verification workaround as D9, with the root-level
failure and its "not ours to fix" disposition carried by C2.
Also fenced out the near-miss temptations: no `farewell.go`, no shared test table, no
touching `ComposeGreeting`'s signature.

**Batch 3 — architecture, coarse.** One module boundary: `package main` under
`services/api/`. Nothing here crosses a package line, and the design conflicts with no
existing pattern — it copies the file's only pattern. Question asked: should `defaultName` be
exported, so the sibling `lyx-test-weft` fixture could reuse it? Recommendation and
resolution: no. Nothing outside this package calls it, and exporting it would enlarge the
fixture's public surface for a hypothetical consumer (YAGNI).

**Batch 4 — the helper's contract.** Should `defaultName` trim whitespace, so `"   "` also
defaults to `world`? Recommended no, and took it: today's `ComposeGreeting` does not trim,
and step 1 is meant to be behaviour-preserving. A refactor that quietly changes behaviour is
the worst kind. Recorded as D3 and pinned by C5.

**Batch 5 — call shape.** Two viable shapes for the composers: keep the reassignment
(`name = defaultName(name)`, minimal diff) or fold the call into `fmt.Sprintf` (one line, no
mutation, both functions structurally identical). Took the second (D4), accepting the
slightly larger step-1 diff as R2.

**Batch 6 — edge cases.** Empty string is the only interesting input, and it is the helper's
entire reason to exist — covered in both composers' tables. Whitespace-only and
space-containing names pass through by design (D3). Unicode needs no special handling: `%s`
on a `string` is byte-transparent. No concurrency surface — both composers are pure functions
over an immutable argument, no package-level state is introduced. No invalid input exists:
every `string` is valid.

**Batch 7 — security.** Assessed and dismissed in one pass. No trust boundary is crossed:
the name is a compile-time literal from `main()`, nothing is parsed, no I/O beyond
`fmt.Println` to stdout, no new imports, no format-string injection (the format string is a
literal; the name is an argument, never the format). Nothing to validate. Recorded here
rather than in the decision record so the record stays actionable.

**Batch 8 — testing.** Confirmed table-driven, mirroring the existing test's exact shape
(D6), three cases matching the greeting's three inputs. Asked whether `defaultName`
deserves its own test — no (D7): three lines, unexported, fully covered through both
composers' empty-name rows. Asked what proves the "independently committable" requirement,
since a passing suite at HEAD proves nothing about intermediate commits — answer folded into
the acceptance criteria as a per-commit obligation, not a final-state one.

## Rejected alternatives

- **Add a `go.mod` so `go test ./...` works literally as the brief writes it.** Rejected:
  the brief's "no new files" rule is explicit, and a module file would change how every other
  fixture exercise in this repo behaves. The gap is recorded in C2, not patched.
- **Export `DefaultName`.** Rejected: no caller outside the package; speculative surface.
- **Put `ComposeFarewell` in a new `services/api/farewell.go`.** Rejected: new file, forbidden.
- **Trim whitespace inside `defaultName`.** Rejected: silent behaviour change inside a
  refactor step.
- **Keep `name = defaultName(name)` in both composers** (minimal-diff variant of D4).
  Rejected, narrowly: the inline form makes the shared default visually obvious and both
  functions one-liners. Reasonable either way; the cost of the choice is logged as R2.
- **Share one table between `TestComposeGreeting` and `TestComposeFarewell`**, parameterised
  by a `func(string) string` and a prefix. Rejected: makes step 3 rewrite step 0's test for
  no gain, and a six-line duplicated table is more readable than an indirection.
- **A dedicated `TestDefaultName`.** Rejected (D7): redundant with the empty-name rows.
- **Collapse the three steps into one commit.** Rejected: the brief prescribes the split.
- **Print greeting and farewell with a single `fmt.Println` and string concatenation.**
  Rejected: "both" reads as two lines (D8), and two statements keep each line greppable.
- **Give `ComposeFarewell` a format or locale parameter.** Rejected: YAGNI, nobody asked.

## Review rounds

_No rounds yet._

## Question ledger

All entries are auto-picks: the session ran autonomously under Step 4, so no question was put
to an operator. Every one is resolved; none are left open.

The Rationale column points at the decision or constraint that governs each row rather than
restating it — the reasoning lives in the Interview above and in `decision-record.md`. Q1 and
Q13 produced no Decision of their own, so for those two the cell below is the only copy.

| # | Question | Auto-pick | Rationale |
|---|---|---|---|
| Q1 | Is a farewell function worth building at all? | Yes, build as briefed | Step 3 ships its caller; not speculative. |
| Q2 | Three commits or one? | Three, per the brief | D1 |
| Q3 | `go test ./...` fails at the repo root — add `go.mod`? | No; verify with `GO111MODULE=off go test ./...` from `services/api` | C1, C2, D9 |
| Q4 | Export `defaultName`? | No, unexported | D2 |
| Q5 | New file for the farewell? | No, same `main.go` | C1 |
| Q6 | Should `defaultName` trim whitespace? | No | D3, C5 |
| Q7 | `name = defaultName(name)` or inline in `Sprintf`? | Inline | D4; cost logged as R2 |
| Q8 | Farewell text and default? | `"Goodbye, %s!"`, default `world` | D5; default per D3 |
| Q9 | Shared test table across both tests? | No, separate literal tables | D6 |
| Q10 | Test `defaultName` directly? | No | D7 |
| Q11 | Which farewell test cases? | The greeting's three inputs, `Hello` → `Goodbye` | D6, and the step-3 acceptance criteria |
| Q12 | One `Println` or two in `main()`? | Two, greeting first | D8 |
| Q13 | Security review needed? | No trust boundary; nothing to validate | Literal input, literal format string, stdout only. |
| Q14 | How is "independently committable" proven? | Per-commit test + gofmt + `git show --stat` checks | C3, and the acceptance criteria |
