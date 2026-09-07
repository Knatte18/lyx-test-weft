# Card 1 — Rename the greeting helper to ComposeGreeting

**Rename:**
- `services/api#FormatGreeting` -> `plan:services/api#ComposeGreeting`
- `services/api#TestFormatGreeting` -> `plan:services/api#TestComposeGreeting`

**Edit:**
- `services/api#main`

**Intent:** Rename the exported helper so its name states what it does — it
composes the whole greeting sentence rather than formatting a pre-existing one.
The old name is deleted outright: no alias, no deprecated forwarder, no wrapper
kept under `FormatGreeting`. Nothing about the signature, the parameter name,
the return type, or the body changes, and the empty-name default to `"world"`
is preserved bit for bit.

The test function is renamed with it, in this same card. Go's convention pairs
`TestXxx` with the `Xxx` under test, so `TestFormatGreeting` becomes
`TestComposeGreeting`; a test whose name still points at a symbol that no longer
exists is a stale signpost. That function has no meaning or testability apart
from the helper it exercises, and two of its own lines already change here, so
splitting its declaration line into a follow-on card would split one unit rather
than separate two.

Six occurrences carry the old name, and they are easy to fix out of order. In
`services/api/main.go`: the declaration, which reads like the whole job; the doc
comment's leading word above it; and the call inside `main()`. In
`services/api/main_test.go`: the test function's own declaration line; the call
under test; and — on the line below that call — the helper's name sitting as
plain text inside the `t.Errorf` format string. That last one is the one most
easily left behind, because nothing about it breaks the build; a failure message
naming a function that no longer exists sends a future reader hunting for the
wrong symbol, so it is retargeted too.

The doc comment above the declaration has its leading word retargeted and
nothing else: Go requires the comment to begin with the declared name, and the
description after it is still accurate, so rewriting it would turn a pure rename
into an editorial pass.

The test's table of three cases — a named greeting, the empty-name default to
`"world"`, and a multi-word name — stays untouched: no new cases, no altered
expectations. Only the lines carrying the identifier change.

Retarget each occurrence surgically with the editing tools, one at a time. No
`sed`, and no repo-wide substitution of any kind — the operator's standing
instruction bans the former, and a blanket replace would risk collateral hits in
`services/api/s2-note.txt`, `README.md`, and the driver state under `_lyx/`,
every one of which must stay byte-identical.

**ImpactSummary:** Confined to the `services/api` package; six occurrences across `main.go` and `main_test.go` are the complete in-repo reference set, nothing outside the repository can import the symbol, and observable behaviour is unchanged.

**Commit:** 1: rename FormatGreeting to ComposeGreeting

**Verify:**
```sh
! grep -rn FormatGreeting services/api
```
