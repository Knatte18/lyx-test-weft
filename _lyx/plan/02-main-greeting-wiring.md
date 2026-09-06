# Card 2 — main-greeting-wiring

**Edit:**
- `services/api#main`

**Uses:**
- `plan:services/api#FormatGreeting`

**Intent:** Make the binary do something. `main()`'s body becomes
`fmt.Println(FormatGreeting("lyx"))`, so building and running `services/api` prints
`Hello, lyx!` and exits 0.

The literal is non-empty on purpose: it exercises the helper's normal path in the binary
and leaves the empty-name default to card 1's test, so the two branches are covered in
different places rather than both landing on `"world"`. The fixture comment above
`main()` stays exactly where it is.

`main()`'s printed output is not reachable from a unit test without restructuring
`services/api`, which is out of scope for this task, so this card's check is to build the
binary and run it. Build with `-o` into a directory outside the repo: a bare
`GO111MODULE=off go build ./services/api/` drops an `api` executable at the repo root and
dirties the worktree, which would break the requirement that only the two intended files
show up in `git status --porcelain`.

**ImpactSummary:** One line inside `main()`; the package has no other caller and the helper's signature is untouched.

**Verify:** OUT="$(mktemp -d)/api"; GO111MODULE=off go build -o "$OUT" ./services/api/ && test "$("$OUT")" = "Hello, lyx!"
