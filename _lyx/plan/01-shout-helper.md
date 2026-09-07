# Card 1 — shout-helper

**Create:**
- `services/api#shout`

**Intent:** Add a new unexported helper `shout` to `services/api/main.go`, placed directly below
`orDefault`, returning its argument with a single `"!"` appended.

No import is added, no existing function changes, and no other file is touched.
`go test ./...` must pass unchanged afterwards.

**Commit:** `1: shout-helper`
