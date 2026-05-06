# keystone-tool-index-stack

`keystone-tool-index-stack` is a focused Python codebase around package a Python local lab for index analysis with safe and unsafe fixtures, remediation hints, and documented operating limits. It is meant to be easy to inspect, run, and extend without a hosted service.

## Keystone Tool Index Stack Walkthrough

I would read the project from the outside in: command, fixture, model, then roadmap. That keeps the cli tools idea grounded in files that can be checked locally.

## Reason For The Project

This project keeps the domain idea close to the tests. That makes it useful as a reference implementation, a small experiment, or a starting point for a more specialized tool.

## How It Is Put Together

The core is a scoring model over demand, capacity, latency, risk, and weight. That keeps terminal output, argument shape, and file input in one explicit decision path. The threshold is 166, with risk penalty 6, latency penalty 3, and weight bonus 5. The Python code favors standard library tools and direct tests over framework weight.

## Data Notes

`examples/extended_cases.csv` adds six named cases. I kept the names plain so failures are easy to read in a terminal: baseline, pressure, surge, degraded, recovery, and boundary.

## Capabilities

- Uses fixture data to keep argument shape changes visible in code review.
- Includes extended examples for file input, including `recovery` and `degraded`.
- Documents repeatable reports tradeoffs in `docs/operations.md`.
- Runs locally with a single verification command and no external credentials.
- Stores project constants and verification metadata in `metadata/project.json`.

## Getting It Running

Install Python and run the commands from the repository root. The project does not need credentials or a hosted service.

## Check The Work

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/audit.ps1
```

The audit command checks repository structure and README constraints before it delegates to the verifier.

## Where Things Live

- `src`: primary implementation
- `tests`: verification harness
- `fixtures`: compact golden scenarios
- `examples`: expanded scenario set
- `metadata`: project constants and verification metadata
- `docs`: operations and extension notes
- `scripts`: local verification and audit commands
- `pyproject.toml`: Python project metadata

## Tradeoffs

This code is local-first. It makes no claim about deployed usage and avoids credentials, hosted state, and environment-specific setup.

## Possible Extensions

- Add malformed input fixtures so the failure path is as visible as the happy path.
- Split the scoring constants into a typed configuration object and validate it before use.
- Add a comparison mode that shows how decisions change when one signal is adjusted.
- Add one more cli tools fixture that focuses on a malformed or borderline input.

## Command Examples

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

This runs the language-level build or test path against the compact fixture set.
