# CM Civic Verification — Build Status / Validation Checklist
Date: 2026-11-23
By CM (Charles Miller)

## What this batch did — with raw evidence

Two single batch runs. No repo was created one at a time.

### Batch run 1 (4 write calls)
- create_repository `bartimoussmith-oss/cm-civic-verification`:
  FAILED — 403 "Resource not accessible by integration". The GitHub
  App installation cannot create new repositories. No new repo was
  created through the connector.
- push_files to that (non-existent) repo: FAILED — 404, consequence
  of the failed creation.
- push_files `therealwindycity/transcript-sync`: FAILED — 403 at
  create-tree.
- push_files `bartimoussmith-oss/casper-record-mirror`: SUCCESS —
  commit f91e23292c0a18c2d16f5512595175b2c3d3ca51, 2026-11-23
  23:35:10Z. Added `wayback_source.py` + patched `collect.py`
  (`--source wayback`, default `live`). Verified live by read-back.

### Batch run 2 (3 write calls)
- create_or_update_file `therealwindycity/transcript-sync`
  `scripts/fetch_transcripts_wayback.py`: SUCCESS — commit
  c6815909e893d53f1162c07aa1a544f796ad9f41, 2026-11-23 23:36:29Z,
  file SHA 2f66810d, 19,802 bytes. Verified live by read-back.
- create_or_update_file `therealwindycity/transcript-sync`
  `.github/workflows/sync.yml`: FAILED — 403 on PUT to
  `.github/workflows/`. The App cannot write workflow files.
  The workflow file must be added through the GitHub website UI,
  or the App's workflow permission must be granted. The daily
  sync cannot run in Actions until that file exists.
- push_files `bartimoussmith-oss/promethean-civic-atlas` main:
  SUCCESS — commit d66e70f2abab1f64e76426ecd9008b2f25fdf0d7,
  2026-11-23 23:36:55Z. 68 files under `national/`:
  `national-registry.json`, 64 state/territory/tribal stubs,
  README, LICENSE-COMMERCIAL, BUILD-STATUS. Verified live by
  read-back (`national/national-registry.json` SHA df428d02).
  The national scaffolding lives in the existing atlas repo
  because new-repo creation is blocked (see above).

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

- [x] Casper pilot, local: `collect.py --source wayback --dry-run`
      enumerates 155 documents (verified locally 2026-11-23).
- [ ] Casper pilot, in Actions: `--source wayback --max-new 5`,
      manifest verified, before any full run. Blocked until the
      Casper workflow is confirmed runnable.
- [x] Transcript fetcher, local: one run from archive.org `cochwy`
      captions — 31,449 words for 2026-11-09 council
      (YouTube id LspPbRmg9xg).
- [ ] Transcript sync, in Actions: BLOCKED — `.github/workflows/sync.yml`
      is not in the repo (403, see above). No daily run exists yet.
- [ ] Only after a successful sync run: retire YOUTUBE_COOKIES
      and close Issue #2 in The-Real-Windy-City-.

## Per-state status

- Wyoming: candidate (126 configured, 0 proven reporting).
- Montana (rank 1), Idaho (2), South Dakota (3), North Dakota (4),
  Utah (5), Nebraska (6), Colorado (7), Nevada (8), New Mexico (9),
  Arizona (10), and all remaining entries in national-registry.json:
  not started. Configs disabled until live-verified.
- Registry has 64 entries: 50 states, District of Columbia,
  5 territories, 8 tribal nations. No national total is claimed
  as verified coverage.

## Blocked / not done in this batch

- New-repo creation is 403-blocked for the GitHub App. To create
  new repos, Charles must change the App installation/permissions
  or create repos on the GitHub website. Until then, new content
  goes into existing repos.
- Workflow-file writes are 403-blocked. `sync.yml` must be added
  via the GitHub website UI.
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
