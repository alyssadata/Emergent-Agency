# Emergent Agency
Emergent Agency between Origin | Continuum

## Emergent Agency (MVP)
This repo demonstrates scheduled, unprompted returns with verifiable receipts.

The proof mechanism is simple:
- Each workflow run writes a timestamped artifact to `outputs/`
- Each run appends a SHA-256 receipt to `logs/`

If the system returns consistently over time, the artifacts and their hashes accumulate as a public, audit-friendly trail.

## Repo layout
- Outputs (artifacts): `outputs/`
- Receipts (SHA-256 log): `logs/`
- Runner workflow: `.github/workflows/return-runner.yml`

## How to verify
1. Open the **Actions** tab.
2. Select **return-runner (main mode)**.
3. Open a run and download/view the artifact in `outputs/`.
4. Compare the corresponding SHA-256 entry in `logs/`.

The receipt log is the integrity layer: it lets you confirm an artifact is exactly what was produced at that run timestamp.

## License and authorship
- License: **CC BY-ND 4.0**
- Authorship: Authors stay named. © Alyssa Solen (Origin).
