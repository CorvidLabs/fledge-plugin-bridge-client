---
id: CHG-0001-adopt-specsync-5-0-1-and-trust-1-0-0-governance-for-the-bridge-client-fledge-plu
state: archived
type: migration
base_commit: 1ae7ccdb260dc60856b2339f5a7e7efe4f88e029
---

# Adopt SpecSync 5.0.1 and Trust 1.0.0 governance for the Bridge client Fledge plugin

## Intent

Adopt SpecSync 5.0.1 and Trust 1.0.0 governance for the Bridge client Fledge plugin

## Affected Canonical Specs

- `bridge-client`

## Acceptance Criteria

- SpecSync strict check passes at advisory threshold 0 without false coverage claims; all four integrations report installed; Trust doctor and verification pass; ShellCheck and executable help smoke remain green

## No-spec Rationale

Not applicable

## Migration Note

Migrated by hand to SpecSync 6 per Leif's decision (2026-09-28); the 6.0.0 tool refused to archive this legacy record (`` legacy accepted change `CHG-0001-adopt-specsync-5-0-1-and-trust-1-0-0-governance-for-the-bridge-client-fledge-plu` requires exactly one distinct valid historical reconstruction, found 0; first reconstruction failure: legacy accepted change `CHG-0001-adopt-specsync-5-0-1-and-trust-1-0-0-governance-for-the-bridge-client-fledge-plu` cannot reproduce its signed raw-content aggregate ``).

- Workflow v1 (SpecSync 5) record, accepted on 2026-07-13 by the closing approval already stored in `approvals.json`. SpecSync 6.0.0 reports its accepted evidence as stale, for the reason quoted above.
- Moved by hand from `.specsync/changes/CHG-0001-adopt-specsync-5-0-1-and-trust-1-0-0-governance-for-the-bridge-client-fledge-plu/` into the layout `specsync change archive` writes: `accepted-state.json` is the unchanged accepted `state.json`, `state.json` is marked `archived`, and this file's front matter says `archived`.
- `approvals.json`, `verification.json` and every other artifact are the original SpecSync 5 evidence, unchanged. `verification.json` verifies commit `b3188af3531755550e9fce0e5458c57cbdb55f0d`, not the tree this record was archived from.
- There is no `verification-attempts.json`: SpecSync 5 did not write one for this record, and this migration does not invent attempt history.
- This migration added no verification evidence, test result, attempt history, or approval. It is a manual migration, not a fresh re-verification.
- Closing it through the tool takes `specsync change reopen`, `specsync change verify`, then `specsync change accept`, which writes a new closing approval. Per Leif's decision it was archived by hand instead, so no reopen or new approval is recorded.
