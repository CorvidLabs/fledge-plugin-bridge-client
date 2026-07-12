---
module: bridge-client
version: 1
status: active
files:
  - bin/fledge-plugin-bridge-client

db_tables: []
depends_on: []
---

# Bridge-client

## Purpose

Send authenticated HTTP requests to corvid-agent for listing and controlling already-connected outbound bridge sessions without opening a port on the bridged machine.

## Public API

| Command | Behavior |
|---------|----------|
| sessions | List connected bridge sessions. |
| ping | Health-check a selected or uniquely connected session. |
| read PATH | Read a remote sandboxed file. |
| write PATH | Send stdin as remote file content. |
| ls PATH | List a remote directory. |
| exec COMMAND | Execute a remote command with an optional working directory. |
| --session ID | Select a session explicitly. |
| --json | Pass through the raw server response. |

## Invariants

1. The client talks only to the configured corvid-agent HTTP API and never connects directly to the bridged machine.
2. Authentication uses the optional bearer token without printing it.
3. A single session is auto-selected; zero or multiple sessions require an explicit resolution.
4. File paths, command text, working directories, and content are JSON-encoded before transport.
5. Remote execution propagates the reported exit code.

## Behavioral Examples

```
Given exactly one connected bridge session
When the user runs `fledge bridge-client read src/main.rs`
Then the client selects that session, sends a `file.read` request, and prints returned content
```

## Error Cases

| Error | When | Behavior |
|-------|------|----------|
| Server unavailable | An API request cannot complete | Report the method/path failure and exit non-zero. |
| No sessions | Automatic selection finds a count of zero | Report that no bridge sessions are connected. |
| Multiple sessions | Automatic selection finds more than one | List sessions and require `--session`. |
| Missing command argument | A path or command is required | Print command-specific usage and exit non-zero. |
| Remote error | Response contains an error field | Print it to stderr and exit non-zero. |

## Dependencies

- Bash, curl, and Python 3
- corvid-agent bridge HTTP API
- an outbound session established by fledge-plugin-bridge

## Change Log

| Version | Date | Changes |
|---------|------|---------|
| 1 | 2026-07-12 | Document existing Bridge client behavior for SpecSync 5 adoption. |
