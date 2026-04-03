---
status: complete
owner: rufus
priority: high
description: Spawn and manage production processes (OBS, encoders, etc.)
completed: 2026-04-03
---

## Purpose

Production requires coordinating multiple long-running processes (OBS for capture, ffmpeg for encoding, network streams). This command spawns, monitors, and manages those processes across hardware nodes.

## Interface

**Command:**
```
rufus spawn process <TYPE> [--hardware NODE] [--args "ARGS"]
```

**Arguments:**
- `TYPE`: process type (obs, ffmpeg-encode, stream, monitor)
- `--hardware`: target node (flowbie, fourty4, thinker)
- `--args`: arguments to pass to process

**Output:** Process ID, status, monitoring link

## Specification

**Process types:**
- `obs` — OBS Studio capture/mixing
- `ffmpeg-encode` — Video/audio transcoding
- `stream` — Streaming output (Twitch, YouTube)
- `monitor` — Resource monitoring daemon

**Behavior:**
1. Validate process type and arguments
2. SSH to target hardware
3. Start process with logging
4. Return PID and monitoring endpoint
5. Keep track of process lifecycle

**Monitoring:**
- Log all output
- Alert if process dies unexpectedly
- Report resource usage
- Support graceful shutdown

**Edge cases:**
- Port already in use → find alternate
- Hardware unreachable → fail gracefully
- Process crashes → log and alert
- Cleanup on exit

## Implementation

Implemented in `command.sh`. Uses SSH and systemd/process management to spawn and monitor processes.

## Dependencies

- SSH connectivity to hardware
- Process management (systemd or supervisor)
- Hardware manifest

## Testing

Acceptance criteria:
- [ ] Can spawn OBS on flowbie
- [ ] Can spawn ffmpeg on fourty4
- [ ] Monitoring endpoints work
- [ ] Processes survive network blips
- [ ] Cleanup on shutdown

## Status Note

Built and operational. Critical for live production coordination.
