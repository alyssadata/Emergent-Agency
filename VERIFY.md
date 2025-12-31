# VERIFY

## What this repo produces
Each run writes:
- an artifact in `outputs/continuity-<timestamp>.md`
- a receipt line in `logs/returns-YYYY-MM.md` with the artifact path + SHA-256

## Verify one receipt (30 seconds)
1) Open `logs/` and pick a line from `returns-YYYY-MM.md`.
2) Open the referenced artifact file in `outputs/`.
3) Copy the SHA-256 from the log line.
4) On your machine, run:

```bash
shasum -a 256 outputs/<artifact-file>
