---
format: 5
approved: true
language: go
---

# Plan: add a shout helper and wire it into main

`services/api/main.go` prints its greeting and farewell verbatim.
This plan adds an unexported `shout` helper and has `main` route the greeting through it, so the
package carries one small emphasis helper both lines can reuse later.

## Card Index

1 — shout-helper — add the unexported `shout` helper
2 — shout-wiring — route main's greeting through the helper

## verify:

```
(cd services/api && GO111MODULE=off go test ./...)
```
