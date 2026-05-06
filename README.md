# apex-mesh-gossip-gate

`apex-mesh-gossip-gate` packages a practical distributed systems exercise in SQL. The emphasis is on deterministic behavior, a small public API, and examples that explain the tradeoffs.

## How I Read Apex Mesh Gossip Gate

The useful thing to inspect here is how the same score rule is represented in code, metadata, and examples. If those three pieces disagree, the audit script should make the drift visible.

## Internal Model

The core is a scoring model over demand, capacity, latency, risk, and weight. That keeps node state, quorum behavior, and lease timing in one explicit decision path. The threshold is 152, with risk penalty 4, latency penalty 2, and weight bonus 5. The SQL project uses sqlite fixtures, views, and assertions to keep query behavior inspectable.

## Problem Shape

I use this kind of project to make a rule visible before adding more machinery around it. The important part here is not the size of the codebase. It is that the input signals, scoring rule, fixture data, and expected output can all be checked in one sitting.

## Main Behaviors

- Uses fixture data to keep quorum behavior changes visible in code review.
- Includes extended examples for lease timing, including `surge` and `degraded`.
- Documents message ordering tradeoffs in `docs/operations.md`.
- Runs locally with a single verification command and no external credentials.
- Stores project constants and verification metadata in `metadata/project.json`.

## Scenario Walkthrough

The extended cases are not random smoke tests. `degraded` keeps pressure on the review path, while `surge` shows the model when capacity and weight are strong enough to clear the threshold.

## Repository Map

- `tests`: verification harness
- `fixtures`: compact golden scenarios
- `examples`: expanded scenario set
- `metadata`: project constants and verification metadata
- `docs`: operations and extension notes
- `scripts`: local verification and audit commands
- `schema.sql`: sqlite schema and view definitions

## Run It Locally

Clone the repository, enter the directory, and run the verifier. No database server, cloud account, or token is required.

## How To Run It

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

This runs the language-level build or test path against the compact fixture set.

## Validation

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/audit.ps1
```

The audit command checks repository structure and README constraints before it delegates to the verifier.

## Known Edges

This code is local-first. It makes no claim about deployed usage and avoids credentials, hosted state, and environment-specific setup.

## Follow-Up Work

- Add malformed input fixtures so the failure path is as visible as the happy path.
- Split the scoring constants into a typed configuration object and validate it before use.
- Add a comparison mode that shows how decisions change when one signal is adjusted.
- Add one more distributed systems fixture that focuses on a malformed or borderline input.
