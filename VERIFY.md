# VERIFY

## What this repo produces
Each run writes:
- an artifact in [outputs/](outputs/) (file: `continuity-<timestamp>.md`)
- a receipt line in [logs/](logs/) (file: `returns-YYYY-MM.md`) with the artifact path + `SHA-256:<hash>`

## Verify one receipt (30 seconds)
1. Open [logs/](logs/) and open the latest `returns-YYYY-MM.md`.
2. Pick one receipt line and copy:
   - the artifact path (example: `outputs/continuity-<timestamp>.md`)
   - the value after `SHA-256:`
3. Open the referenced artifact in [outputs/](outputs/).
4. On your machine, compute the SHA-256 of that file:
   - macOS: `shasum -a 256 outputs/<artifact-file>`
   - Linux: `sha256sum outputs/<artifact-file>`
5. Confirm the computed hash matches the value after `SHA-256:` in the log line.

## What a valid receipt looks like
A valid receipt line contains:
- an ISO timestamp
- an `outputs/` path
- `SHA-256:` followed by 64 hex characters
