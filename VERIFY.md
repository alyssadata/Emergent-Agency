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

## Verification Contract (stable)

This repo’s verification depends on a small, stable contract.

### Artifact naming
Each workflow run produces exactly one artifact with the pattern:

outputs/continuity-<timestamp>.md

Where `<timestamp>` is an ISO-style timestamp included in both the filename and the receipt line.

### Receipt log location
Each workflow run appends exactly one receipt line to the monthly log:

logs/returns-YYYY-MM.md

### Receipt line requirements
A valid receipt line must contain:
- an ISO timestamp
- an `outputs/` artifact path
- `SHA-256:` followed by **64 lowercase hex characters** (0-9, a-f)

### Hash algorithm
Integrity is verified using **SHA-256** computed over the full artifact file contents.

### Pass / fail conditions
Verification **passes** if the SHA-256 computed locally for the referenced artifact exactly matches the hash recorded after `SHA-256:` in the receipt line.

Verification **fails** if:
- the artifact file was edited after the receipt was logged
- the receipt line format is malformed
- the referenced artifact path is missing
- the computed hash does not match the recorded hash
