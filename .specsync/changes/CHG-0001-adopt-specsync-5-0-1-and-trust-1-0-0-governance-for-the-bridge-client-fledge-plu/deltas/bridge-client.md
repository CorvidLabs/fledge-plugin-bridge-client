## MODIFIED

### SPEC SECTION Invariants

1. The client talks only to the configured corvid-agent HTTP API and never connects directly to the bridged machine.
2. Authentication uses the optional bearer token without printing it.
3. A single session is auto-selected; zero or multiple sessions require an explicit resolution.
4. Payloads are serialized as JSON before transport; write and exec preserve user-controlled fields, while read and list currently require paths without apostrophes.
5. Formatted remote execution propagates the reported exit code; raw JSON mode passes the server response through after a successful HTTP request.

### SPEC SECTION Error Cases

| Error | When | Behavior |
|-------|------|----------|
| Server unavailable | An API request cannot complete | Report the method/path failure and exit non-zero. |
| No sessions | Automatic selection finds a count of zero | Report that no bridge sessions are connected. |
| Multiple sessions | Automatic selection finds more than one | List sessions and require `--session`. |
| Missing command argument | A path or command is required | Print command-specific usage and exit non-zero. |
| Remote error in formatted read, list, or exec output | A decoded response contains an `error` field | Print it to stderr and exit non-zero. |
| Raw JSON response | `--json` is requested after a successful HTTP request | Pass the response through without interpreting remote error or exit-code fields. |

### REQUIREMENT REQ-bridge-client-003

The client SHALL JSON-encode write content, write paths, command text, and working directories and optionally authenticate with a bearer token.

Acceptance Criteria
- Write and exec payloads preserve quotes and other user-controlled text.
- Authentication tokens are sent only in the authorization header and are not printed.

### REQUIREMENT REQ-bridge-client-004

The client SHALL support raw JSON pass-through and SHALL propagate remote command exit status in formatted output mode.

Acceptance Criteria
- `exec --json` prints the server response after a successful HTTP request without interpreting its exit-code field.
- Formatted `exec` exits with the remote command's reported status.
