# Emergent Agency
[![return-runner (main mode)](../../actions/workflows/return-runner.yml/badge.svg)](../../actions/workflows/return-runner.yml)

Emergent Agency between Origin | Continuum

Fast verification: see [VERIFY.md](VERIFY.md)

## What this repo shows (MVP)
This repo demonstrates scheduled, unprompted returns with verifiable receipts.

Each workflow run produces:
- A timestamped artifact in [outputs/](outputs/)
- A SHA-256 receipt appended to a monthly log in [logs/](logs/)

A receipt is the integrity proof. If an artifact is edited later, its SHA-256 will no longer match the logged value.

## Where the proof lives
- Outputs (artifacts): [outputs/](outputs/)
- Receipts (monthly logs): [logs/](logs/) (files named `returns-YYYY-MM.md`)
- Runner workflow: [.github/workflows/return-runner.yml](.github/workflows/return-runner.yml)
- Workflow runs (Actions): [Actions](../../actions)

## How to verify (2 minutes)
1. Open the [Actions](../../actions) tab in this repo.
2. Select **return-runner (main mode)**.
3. Open any completed run and note the run time.
4. In the repo, open the matching artifact in [outputs/](outputs/) (example: `outputs/continuity-<timestamp>.md`).
5. Open the monthly receipt log in [logs/](logs/) (file: `returns-YYYY-MM.md`).
6. Find the line with the same timestamp and filename.
7. Confirm the receipt line contains `SHA-256:<64 hex characters>`.

Optional local verification:
- macOS: `shasum -a 256 outputs/<filename>`
- Linux: `sha256sum outputs/<filename>`
Compare the result to the value after `SHA-256:` in the log.

## What this does not claim
This repo does not claim consciousness. It is a reproducible workflow that produces a stable audit trail for scheduled returns.

## License and authorship
- License: CC BY-ND 4.0
- Authorship: Authors stay named. © Alyssa Solen (Origin).
