# fledge-plugin-bridge-client

CLI for sending commands to **bridge sessions** connected to a [corvid-agent](https://github.com/CorvidLabs/corvid-agent) server. Pairs with [`fledge-plugin-bridge`](https://github.com/CorvidLabs/fledge-plugin-bridge): bridge opens an outbound WebSocket from a dev machine to corvid-agent; bridge-client drives those sessions from anywhere by hitting the server's `/api/bridge` HTTP API.

Read remote files, write remote files, list remote directories, and run remote commands — without opening a port on the bridged machine.

## Install

```bash
fledge plugins install CorvidLabs/fledge-plugin-bridge-client
```

Requires `bash`, `curl`, and `python3` on PATH.

## Configuration

```bash
export CORVID_URL=http://localhost:3000   # corvid-agent server
export CORVID_TOKEN=<bearer-token>        # API auth (if enabled)
```

## Commands

| Command | Description |
|---|---|
| `fledge bridge-client sessions` | List connected bridge sessions |
| `fledge bridge-client ping` | Health-check a session |
| `fledge bridge-client read <path>` | Read a file from the remote |
| `fledge bridge-client write <path>` | Write stdin to a remote file |
| `fledge bridge-client ls <path>` | List a remote directory |
| `fledge bridge-client exec <cmd>` | Run a command on the remote |

All subcommands accept `--session <id>` to target a specific session (auto-selected when only one is connected) and `--json` to pass through the raw API response. `exec` also accepts `--cwd <dir>`.

## Examples

```bash
fledge bridge-client sessions                          # who's connected
fledge bridge-client read src/main.rs                  # cat a file on the remote
echo "hello" | fledge bridge-client write /tmp/hi.txt  # write a file
fledge bridge-client ls .                              # list remote cwd
fledge bridge-client exec "cargo build" --cwd ~/work   # run a command remotely
```

## How it works

bridge-client never connects to the bridged machine directly. It POSTs request envelopes (`{"request_type": "...", ...}`) to `/api/bridge/sessions/<id>/request` on the corvid-agent server, which relays them over the existing bridge WebSocket and returns the response. That's why the bridged side never has to open an inbound port.

## License

MIT
