# keystone-tool-index-stack

`keystone-tool-index-stack` keeps a focused Python implementation around cli tools. The project goal is to package a Python local lab for index analysis with safe and unsafe fixtures, remediation hints, and documented operating limits.

## Use Case

This is intentionally local and self-contained so it can be inspected without credentials, services, or seeded history.

## Keystone Tool Index Stack Review Notes

The first comparison I would make is `terminal width` against `argument risk` because it shows where the rule is most opinionated.

## Highlights

- `fixtures/domain_review.csv` adds cases for file span and terminal width.
- `metadata/domain-review.json` records the same cases in structured form.
- `config/review-profile.json` captures the read order and the two review questions.
- `examples/keystone-tool-index-walkthrough.md` walks through the case spread.
- The Python code includes a review path for `terminal width` and `argument risk`.
- `docs/field-notes.md` explains the strongest and weakest cases.

## Code Layout

The core code exposes a scoring path and the added review layer uses `signal`, `slack`, `drag`, and `confidence`. The domain terms are `file span`, `terminal width`, `argument risk`, and `report density`.

The added Python path is deliberately direct, with fixtures doing most of the explaining.

## Run The Check

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

## Regression Path

That command is also the regression path. It verifies the domain cases and catches mismatches between the CSV, metadata, and code.

## Future Work

This remains a local project with deterministic fixtures. It does not depend on credentials, hosted services, or live data. Future work should add richer malformed inputs before widening the public API.
