---
status: complete
owner: rufus
priority: high
description: Display current Rufus operational status and configuration
completed: 2026-04-03
---

## Purpose

Rufus needs to report current operational status, hardware availability, recording state, and configuration. This command provides quick visibility into what's running, what's available, and what needs attention.

## Interface

**Command:**
```
rufus status
```

**Output:** JSON or table with:
- Rufus entity status (uptime, git state)
- Hardware availability (flowbie, fourty4, thinker)
- Current recording/stream status if active
- Recent activity log

## Specification

**Output includes:**
- Entity name, version, uptime
- Hardware node status (online/offline, CPU, storage)
- Active recording/stream info (type, duration, bitrate)
- OBS scene status
- Asset pipeline status (pending exports, transcoding)
- Recent log entries

**Edge cases:**
- Hardware unreachable → mark as offline
- Multiple simultaneous recordings → list all
- OBS not running → warn in status

## Implementation

Implemented in `command.sh`. Reports git state, hardware connectivity, and process status.

## Dependencies

- CLAUDE.md (entity configuration)
- Hardware manifest and SSH connectivity

## Testing

Acceptance criteria:
- [ ] Reports accurate hardware status
- [ ] Shows current recording if active
- [ ] JSON output parses without errors
- [ ] Handles missing hardware gracefully

## Status Note

Built and operational. Can be enhanced with real-time hardware polling.
