---
spec: bridge-client.spec.md
---

## User Stories

- As an operator, I want to inspect and control a connected bridge session through corvid-agent.
- As an automation author, I want raw JSON output and propagated remote exit codes.

## Acceptance Criteria

### REQ-bridge-client-001

The client SHALL list sessions and require unambiguous session selection before sending a request.

### REQ-bridge-client-002

The client SHALL support ping, file read, file write, directory list, and command execution requests.

### REQ-bridge-client-003

The client SHALL JSON-encode user-controlled payload fields and optionally authenticate with a bearer token.

### REQ-bridge-client-004

The client SHALL support raw JSON output and propagate remote command exit status.

## Constraints

- Requires Bash, curl, Python 3, corvid-agent, and an established bridge session.

## Out of Scope

- Creating bridge sessions or opening direct inbound connectivity.
