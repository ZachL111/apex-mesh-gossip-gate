# Apex Mesh Gossip Gate Walkthrough

This walk-through keeps the domain vocabulary close to the data instead of burying it in prose.

| Case | Focus | Score | Lane |
| --- | --- | ---: | --- |
| baseline | quorum health | 144 | ship |
| stress | lease drift | 130 | watch |
| edge | replica lag | 190 | ship |
| recovery | membership churn | 197 | ship |
| stale | quorum health | 256 | ship |

Start with `stale` and `stress`. They create the widest contrast in this repository's fixture set, which makes them better review anchors than the middle cases.

`stale` is the optimistic case; use it to make sure the scoring path still rewards strong signal.
