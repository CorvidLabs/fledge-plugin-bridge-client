---
change: CHG-0001-adopt-specsync-5-0-1-and-trust-1-0-0-governance-for-the-bridge-client-fledge-plu
artifact: testing
---

# Testing

- REQ-bridge-client-003: inspect write and exec payload construction for Python-argv JSON serialization and bearer-token handling; ShellCheck remains blocking.
- REQ-bridge-client-004: inspect the raw and formatted exec branches for pass-through versus exit-code propagation; run ShellCheck and the executable help smoke.

- `shellcheck bin/*`
- `bin/fledge-plugin-bridge-client --help`
- `specsync check --strict --force` at advisory threshold 0
- `specsync agents status`
- `fledge trust doctor`
- `fledge trust verify`
