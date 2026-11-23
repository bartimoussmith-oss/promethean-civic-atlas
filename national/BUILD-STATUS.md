# CM Civic Verification — Build Status / Validation Checklist
Date: 2026-11-23
By CM (Charles Miller)

## What this batch did

- Backup branches `backup/cm-audit-20261123` created on 6 repos
  (see "Backup branches" below). 28 further backup requests were
  declined by Charles and were NOT retried.
- One national repo created in a single batch run:
  `bartimoussmith-oss/cm-civic-verification` (private), containing
  this registry, 64 disabled state/territory/tribal stubs, README,
  and the paid commercial license.
- Wyoming template pushed in the same batch run:
  - `therealwindycity/transcript-sync`: Wayback fetcher
    `scripts/fetch_transcripts_wayback.py` + workflow
    `.github/workflows/sync.yml` (no YouTube cookies, no yt-dlp).
  - `bartimoussmith-oss/casper-record-mirror`: `wayback_source.py`
    + patched `collect.py` (`--source wayback`, default `live`).

## Backup branches — backup/cm-audit-20261123

Created (6):
- therealwindycity/transcript-sync @ 10e6bda5
- bartimoussmith-oss/cheyenne-laramie-analysis-001 @ 31d40fb
- bartimoussmith-oss/Face-Booked @ a74e3c2
- bartimoussmith-oss/laramie-scanner-private @ 2aae48c
- bartimoussmith-oss/casper-record-mirror @ 9197a8e
- bartimoussmith-oss/therealwindycity @ 30cb025

Declined by Charles, NOT retried (28): all other fleet repos.
Note: earlier backup branches created by the first build attempt
still exist on some repos under the old naming. They cannot be
deleted through the available GitHub connector (no branch-delete
tool); delete them from the GitHub website if Charles wants them gone.
The CM-named branches above are the replacements.

## Wyoming template — verification checklist

- [ ] Casper pilot: `collect.py --source wayback --dry-run`
      enumerates 155 documents (verified locally 2026-11-23).
- [ ] Casper pilot: `--source wayback --max-new 5` in Actions,
      manifest verified, before any full run.
- [ ] Transcript sync: one successful Wayback run from
      archive.org `cochwy` captions (31,449 words verified locally
      for 2026-11-09 council, YouTube id LspPbRmg9xg).
- [ ] Only after a successful sync run: retire YOUTUBE_COOKIES
      and close Issue #2 in The-Real-Windy-City-.
- [ ] BOPU / lead-pipe and Dec 14 hearing work are separate;
      not part of this batch.

## Per-state status

- Wyoming: candidate (126 configured, 0 proven reporting).
- Montana (rank 1), Idaho (2), South Dakota (3), North Dakota (4),
  Utah (5), Nebraska (6), Colorado (7), Nevada (8), New Mexico (9),
  Arizona (10), and all remaining entries in national-registry.json:
  not started. Configs disabled until live-verified.
- No national total is claimed as verified coverage.

## Blocked / not done in this batch

- Two Drive credentials (Socrata session credential, C2 PIN) are
  still unrotated. They must be rotated in the source systems by
  Charles before any run that could use them. No values are recorded
  here, and no run in this batch used them.
- cwdm-max repos remain unknown (account-scoped search errors).
- PR #33 (511 files, respect_robots=false for 126 collectors) was
  NOT merged — separate policy decision.
- PR backlogs (13 in bartimoussmith-oss/therealwindycity, 6 in
  TheReelWindyCity) were NOT merged in this batch.
- No grant applications were made. RJI (due 8 Jan 2027) and NSF
  PESOSE require a free/open-source deliverable, which conflicts
  with the paid commercial license unless a separate open module
  is carved out — that split is not resolved in this batch.
