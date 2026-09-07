# Card 1 — Rename the greeting helper to ComposeGreeting

**Rename:**
- `services/api#FormatGreeting` -> `plan:services/api#ComposeGreeting`

**Edit:**
- `services/api#main`
- `services/api#TestFormatGreeting`

**Intent:** Rename the exported helper so its name states what it does — it
composes the whole greeting sentence rather than formatting a pre-existing one.
The old name is deleted outright: no alias, no deprecated forwarder, no wrapper
kept under `FormatGreeting`. Nothing about the signature, the parameter name,
the return type, or the body changes, and the empty-name default to `"world"`
is preserved bit for bit.

Three references move with the declaration, and they are easy to fix out of
order. The declaration in `services/api/main.go` reads like the whole job. The
call inside `main()` follows it. The call under test inside
`services/api/main_test.go` follows that. The fourth — the helper's name sitting
as plain text inside the `t.Errorf` format string on the line below that call —
is the one most easily left behind, because nothing about it breaks the build; a
failure message naming a function that no longer exists sends a future reader
hunting for the wrong symbol, so it is retargeted too.

The doc comment above the declaration has its leading word retargeted and
nothing else: Go requires the comment to begin with the declared name, and the
description after it is still accurate, so rewriting it would turn a pure rename
into an editorial pass.

Retarget each occurrence surgically with the editing tools, one at a time. No
`sed`, and no repo-wide substitution of any kind — the operator's standing
instruction bans the former, and a blanket replace would risk collateral hits in
`services/api/s2-note.txt`, `README.md`, and the driver state under `_lyx/`,
every one of which must stay byte-identical.

This card leaves the test function still named `TestFormatGreeting`. That is a
stale signpost, not a broken build: the package compiles and the existing
three-case table passes unchanged. Card 2 retires the name.

**ImpactSummary:** Confined to the `services/api` package; the two call sites and one failure-message literal are the complete in-repo reference set, and observable behaviour is unchanged.

**Commit:** 1: rename FormatGreeting to ComposeGreeting

**Verify:**
```sh
! grep -n FormatGreeting services/api/main.go
test "$(grep -c FormatGreeting services/api/main_test.go)" = 1
```
