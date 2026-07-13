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

The client SHALL JSON-encode write content, write paths, command text, and working directories and optionally authenticate with a bearer token.

Acceptance Criteria
- Write and exec payloads preserve quotes and other user-controlled text.
- Authentication tokens are sent only in the authorization header and are not printed.

### REQ-bridge-client-004

The client SHALL support raw JSON pass-through and SHALL propagate remote command exit status in formatted output mode.

Acceptance Criteria
- `exec --json` prints the server response after a successful HTTP request without interpreting its exit-code field.
- Formatted `exec` exits with the remote command's reported status.

## Constraints

- Requires Bash, curl, Python 3, corvid-agent, and an established bridge session.

## Out of Scope

- Creating bridge sessions or opening direct inbound connectivity.
