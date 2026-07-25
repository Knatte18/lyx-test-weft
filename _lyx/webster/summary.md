# fable-r3 integration bisect probe — run paused

Batch 1 (`01-good-one`) completed successfully: `r3g1.md` was created and
committed at `fd407ef053ef7b098f54582c2e61418ab6029b83`. No deviations were
reported.

Before batch 2 (`02-bad-plant`) could begin, `lyx webster begin-batch 2`
returned a paused result (`{"paused": true}`). Per protocol this ends the
run immediately without judging or retrying the pause. The run is resumable
later with `lyx webster run`; batches 2 and 3 remain outstanding.
