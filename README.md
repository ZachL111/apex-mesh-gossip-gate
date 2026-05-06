# apex-mesh-gossip-gate

`apex-mesh-gossip-gate` keeps a focused SQL implementation around distributed systems. The project goal is to implement an SQL distributed systems project for gossip stream reduction, using windowed input fixtures and late-data behavior checks.

## Reason For The Project

The point is to make a small domain rule concrete enough that a reader can change it and immediately see what broke.

## Apex Mesh Gossip Gate Review Notes

The first comparison I would make is `quorum health` against `lease drift` because it shows where the rule is most opinionated.

## What It Does

- `fixtures/domain_review.csv` adds cases for quorum health and lease drift.
- `metadata/domain-review.json` records the same cases in structured form.
- `config/review-profile.json` captures the read order and the two review questions.
- `examples/apex-mesh-gossip-walkthrough.md` walks through the case spread.
- The SQL code includes a review path for `quorum health` and `lease drift`.
- `docs/field-notes.md` explains the strongest and weakest cases.

## How It Is Put Together

The fixture data drives the tests. The code stays thin, while `metadata/domain-review.json` and `config/review-profile.json` explain what each case is meant to protect.

The SQL checks add a separate view over the domain review fixture.

## Run It

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

## Check It

The verifier is intentionally local. It should fail if the fixture score math, lane assignment, or language-specific test drifts.

## Boundaries

This remains a local project with deterministic fixtures. It does not depend on credentials, hosted services, or live data. Future work should add richer malformed inputs before widening the public API.
