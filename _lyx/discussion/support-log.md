# Support log — glyph-demo-greet

## Interview

No operator was present; `discussion_interactive` is `false` in `_lyx/config/loom.yaml`
and the session ran autonomously. The exchange below is the reasoning that would have
been the interview, batch by batch, with every answer self-picked.

**Batch 0 — read before asking.** `services/api/main.go` is a four-line stub: package
clause, a comment marking it a weft relpath-mirroring fixture, and an empty `main()`.
`README.md` explains that the whole repo is a fixture host for the weft sandbox and that
`services/api/` exists to exercise path mirroring. There is no `CONSTRAINTS.md`. Git
history for the file is a single seeding commit. Two questions the codebase answered
outright and that therefore never became interview questions: which module boundary the
work falls under (there is only one — `services/api`, `package main`), and whether the
design conflicts with an existing pattern (there is no existing pattern; the package has
no functions but `main`).

**Batch 1 — scope, and whether this is the right thing to build.** The task is a demo
exercise on a fixture repo, so "is this worth building" resolves differently than it
would on production code: the deliverable is the exercise. Challenged instead whether
the *rename* is real work or theatre. Concluded it is real if and only if the first name
is one a developer would plausibly write and the second is a genuine improvement —
hence `Greet` to `FormatGreeting`, not a token swap. Scope fixed at two files, both
inside `services/api/`.

**Batch 2 — the toolchain constraint, which turned out to dominate.** Probed whether Go
commands even run here. They do not in module mode: there is no `go.mod` at any level,
so `go build`, `go vet`, and `go test` all fail with `go.mod file not found`. Probed
GOPATH mode instead — `GO111MODULE=off` makes vet, build, and test all succeed against
this package on go1.26.0. This resolved the testing question in one shot: a bundled test
file is not dead weight, because it actually runs. Also learned the hard way that a bare
`GO111MODULE=off go build ./services/api/` writes an `api` binary into the repo root;
the stray artifact was removed and the worktree returned to clean before continuing.
That byproduct became acceptance criterion 9. One standing caveat with no action attached,
and so kept here rather than in the decision record: GOPATH mode is a legacy path. It works
on go1.26.0 today, but if a future toolchain drops `GO111MODULE=off` every verification
command in the record stops working and the repo would need a `go.mod` — a decision outside
this task.

**Batch 3 — signature, behaviour, edge cases.** Settled on
`FormatGreeting(name string) string`: one parameter, one return, no `error`, because
string formatting cannot fail and an error return would be an unreachable branch
everywhere. Empty input is the only edge case a caller hits by accident, and
`"Hello, !"` is visibly wrong output, so it defaults to `"world"`. Stopped there:
whitespace-only names, casing, and length caps are hypotheticals, and adding them would
have been designing for requirements nobody stated. `main()` greets `"lyx"` rather than
`"world"` so the binary's normal path and the test's default path are distinguishable.

**Batch 4 — security.** Nothing to decide. There is no trust boundary: the only input is
a compile-time literal in `main()`, the output goes to stdout, and nothing is parsed,
stored, or forwarded. No validation is warranted and none was added.

**Batch 5 — testing and card shape.** Three table-driven cases: an ordinary name, the
empty-name default, and a name containing a space to confirm verbatim pass-through.
Card shape was the last open question and the one with the weakest evidence — resolved
in favour of two ordered cards, since the task states the rename as a follow-on step and
each state builds and passes on its own.

## Rejected alternatives

**No test file at all.** Rejected once GOPATH mode was confirmed working. The only
argument for skipping tests was that they could not be executed; that argument
evaporated, and the task explicitly permits a bundled test file.

**Add a `go.mod` so module-mode commands work.** Rejected. It puts a new file at the
repo root, which the task's "no new files beyond what main.go already has" excludes, and
it changes the shape of a fixture repo that `lyx-test-weft` mirrors. The cost of the
alternative is one environment-variable prefix on three commands.

**Keep the helper dumb — no empty-name branch.** Genuinely close, since "keep the change
minimal" argues for zero branches. Rejected because it leaves the test file asserting
nothing but `fmt.Sprintf`'s behaviour, and because `"Hello, !"` is the one output a
caller can produce by accident. One `if` is a small price for a test worth running.

**Trim whitespace before the empty check**, so `" "` also defaults. Rejected as YAGNI —
nobody asked, and it adds a normalisation rule that then has to be documented and tested.

**Unexported helper (`formatGreeting`).** Better Go style for a `package main` symbol
that nothing outside the package can reach, but the task explicitly asks for an exported
helper. Followed the task. Standing caveat, carried here rather than in the decision
record because it needs no action from the plan writer: a later reviewer applying
ordinary Go style may read the export as pointless and "fix" it, which breaks the test
file that calls the helper by name.

**Final name `GreetingMessage` or `BuildGreeting`.** Both describe the return, but
`FormatGreeting` is verb-led and matches the `fmt`-family vocabulary already in the file.
Marginal call; any of the three would have satisfied the task.

**Concatenation instead of `fmt.Sprintf`.** Faster, and avoids a dependency — except
`fmt` is imported anyway for `main()`'s print, so there is no dependency to avoid and
the speed difference is irrelevant at one call per process.

**Delete or reword the fixture comment above `main()`.** Rejected: it is the only in-repo
note explaining why `services/api` exists, and this task has no business removing it.

**One card containing both the add and the rename.** The argument for it is real — two
cards commit a name that the next commit deletes, which is churn in the history. Rejected
because the task body sequences the rename explicitly ("Once that is in place, rename
..."), and taking that literally is the safer reading of an operator's intent than
optimising their history for them.

## Review rounds

_No rounds yet._

## Question ledger

All entries are auto-picks: the session ran autonomously under
`discussion_interactive: false`, so no question was put to an operator.

| # | Question | Resolution | Basis |
|---|---|---|---|
| 1 | What is the final, descriptive helper name? | `FormatGreeting` | Auto-pick. Verb-led, states that it returns a string rather than performing an action. |
| 2 | What is the intermediate name the rename replaces? | `Greet` | Auto-pick. A plausible first-draft name, so the rename is a real improvement. |
| 3 | Exported or unexported? | Exported | Task text is explicit; no judgment needed. |
| 4 | Does the helper return an `error`? | No | Auto-pick. No failure mode exists. |
| 5 | What is the greeting text? | `"Hello, %s!"` | Auto-pick. Task says only "a short greeting message". |
| 6 | Behaviour on empty `name`? | Default to `"world"` | Auto-pick. The one accidental input; `"Hello, !"` is visibly broken. |
| 7 | Trim or otherwise normalise `name`? | No | Auto-pick, YAGNI. |
| 8 | What name does `main()` greet? | `"lyx"` | Auto-pick. Non-empty, so it does not collide with the empty-name default. |
| 9 | Include a bundled test file? | Yes | Resolved by probe: GOPATH mode runs the tests, so they are not dead weight. |
| 10 | How do verification commands run without a `go.mod`? | `GO111MODULE=off` prefix | Resolved by probe on go1.26.0: vet, build, and test all exit 0. |
| 11 | Add a `go.mod` instead? | No | Auto-pick. Out of the task's stated file scope and changes a shared fixture's shape. |
| 12 | One card or two? | Two, ordered | Auto-pick, and the weakest-evidence call in this record. The task sequences the rename explicitly; each state builds and passes alone. |
| 13 | Keep the existing fixture comment on `main()`? | Yes | Auto-pick. Only in-repo record of the package's purpose. |
| 14 | Any security work needed? | No | No trust boundary — input is a compile-time literal, output is stdout. |

Open, and not resolvable from this worktree:

| # | Question | Why it is open |
|---|---|---|
| 15 | Does any `lyx-test-weft` fixture test assert an exact file inventory for the mirrored `services/api/` subpath? | The assertions live in the paired repo, outside this worktree. If one exists, adding `main_test.go` would trip it. Commit `2fe7af9` already added `s2-note.txt` to the same directory without incident, which is evidence but not proof. Carried into the decision record's open risks. |

No tool or environment fault was encountered. `lyx board get` returned a well-formed
task, and the one worktree change this session made outside its two output files — an
`api` binary left by a probe build — was its own byproduct and was removed immediately,
leaving `git status --porcelain` clean.
