# Card 1 — rename-default-helper

**Edit:**
- `services/api#orDefault`

**Intent:** The unexported helper is currently spelled `defaultName`, which reads as a noun,
while every call site spends it as an operator inside `fmt.Sprintf`. Retarget the identifier
to `orDefault` in `services/api/main.go`: change the declaration and both call sites
(`ComposeGreeting` and `ComposeFarewell`) and nothing else.

This is a plain identifier retargeting, in place, in the file the helper already lives in.
Do not move the function, do not change its signature, its body, or its behaviour, and do not
touch any other file. `go test ./...` must pass unchanged afterwards.

**ImpactSummary:** Retargets one unexported identifier and its two in-file call sites; no exported surface and no behaviour changes.

**Commit:** `1: rename-default-helper`
