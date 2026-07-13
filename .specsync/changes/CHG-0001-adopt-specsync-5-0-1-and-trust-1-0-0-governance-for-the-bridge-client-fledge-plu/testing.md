---
change: CHG-0001-adopt-specsync-5-0-1-and-trust-1-0-0-governance-for-the-bridge-client-fledge-plu
artifact: testing
---

# Testing

- `shellcheck bin/*`
- `bin/fledge-plugin-bridge-client --help`
- `specsync check --strict --force` at advisory threshold 0
- `specsync agents status`
- `fledge trust doctor`
- `fledge trust verify`
