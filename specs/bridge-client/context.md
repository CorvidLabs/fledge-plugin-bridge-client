---
spec: bridge-client.spec.md
---

## Context

This shell plugin is the operator-side client for sessions established by fledge-plugin-bridge through corvid-agent.

## Related Modules

- fledge-plugin-bridge
- corvid-agent bridge HTTP API

## Design Decisions

- Keep transport server-mediated so the bridged host remains outbound-only.
- Use Python's JSON encoder for request fields rather than shell interpolation.
