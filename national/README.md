# CM Civic Verification — National Registry

By CM (Charles Miller).

A source-linked civic verification system: public-meeting archives,
public-records mirroring, and contradiction checking against budgets,
transcripts, and official records.

## License

Paid commercial / source-available. See `LICENSE-COMMERCIAL.md`.
Copyright (c) 2026 CM (Charles Miller). All rights reserved.

- Non-commercial use (personal use, civic research, journalism,
  public-record verification) is allowed with attribution to CM.
- Commercial copying, redistribution for sale, or selling a
  hosted/service version requires a paid commercial license from CM.
- Certain core/designed modules are held back and offered separately
  under a paid commercial license only. Their absence is intentional.

## Status — verified / candidate / not started

- **Wyoming: candidate.** 126 instances are configured in the
  Wyoming registry (99 municipalities + 23 counties + 4 state bodies).
  0 of 126 are proven reporting as of 2026-11-23. The Casper pilot
  is the first proof target. Nothing here is claimed live until a
  source-linked record is public and a repeat run succeeds.
- **All other states, territories, and tribal nations in
  `national-registry.json`: not started.** Workbook entries only.
  Every per-jurisdiction config is disabled until live-verified.
  No totals in this repository are presented as verified coverage.

## Contents

- `national-registry.json` — 64 entries in similarity-rank order:
  50 states, District of Columbia, 5 territories, 8 tribal nations.
  Rank is by similarity / relationship to Wyoming, not a dated
  rollout plan.
- `states/*.json` — one disabled config stub per entry. All have
  `"enabled_for_crawling": false` and an empty jurisdictions list
  until live verification.
- `LICENSE-COMMERCIAL.md` — the paid commercial license.
- `BUILD-STATUS.md` — validation checklist and per-state status.

## Provenance

No private Drive content is in this repository. Workbook registries
were used as read-only reference only; public data must be
regenerated from public sources. Every claim in this repository
keeps its source; a candidate stays a candidate until checked.
