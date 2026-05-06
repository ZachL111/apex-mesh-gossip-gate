# Field Notes

I would read this project from the data inward: cases first, implementation second.

The domain cases cover `quorum health`, `lease drift`, `replica lag`, and `membership churn`. They sit beside the smaller starter fixture so the project has both a compact scoring check and a domain-flavored review check.

`stale` tells me the happy path still works. `stress` tells me whether the guardrail still has teeth.

The point is not to make the repository bigger. The point is to make the important judgment testable.
