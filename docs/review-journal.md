# Review Journal

The review surface for `apex-mesh-gossip-gate` is deliberately narrow: one fixture, one scoring rule, and one local check.

The local checks classify each case as `ship`, `watch`, or `hold`. That gives the project a small review vocabulary that matches its distributed systems focus without claiming live deployment or external usage.

## Cases

- `baseline`: `quorum health`, score 144, lane `ship`
- `stress`: `lease drift`, score 130, lane `watch`
- `edge`: `replica lag`, score 190, lane `ship`
- `recovery`: `membership churn`, score 197, lane `ship`
- `stale`: `quorum health`, score 256, lane `ship`

## Note

This file is intentionally plain so the fixture remains the source of truth.
