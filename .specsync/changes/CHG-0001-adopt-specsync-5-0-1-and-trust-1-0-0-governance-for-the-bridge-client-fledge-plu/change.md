---
id: CHG-0001-adopt-specsync-5-0-1-and-trust-1-0-0-governance-for-the-bridge-client-fledge-plu
state: implementing
type: migration
base_commit: 1ae7ccdb260dc60856b2339f5a7e7efe4f88e029
---

# Adopt SpecSync 5.0.1 and Trust 1.0.0 governance for the Bridge client Fledge plugin

## Intent

Adopt SpecSync 5.0.1 and Trust 1.0.0 governance for the Bridge client Fledge plugin

## Affected Canonical Specs

- None

## Acceptance Criteria

- SpecSync strict check passes at advisory threshold 0 without false coverage claims; all four integrations report installed; Trust doctor and verification pass; ShellCheck and executable help smoke remain green

## No-spec Rationale

This governance adoption documents existing Bridge client behavior and verification policy without changing its runtime contract.
