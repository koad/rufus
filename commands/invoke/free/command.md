---
status: complete
owner: rufus
priority: medium
description: Invoke free/unbound commands on local hardware
completed: 2026-04-03
---

## Purpose

Some operational tasks need to be invoked on hardware without formal entity constraints (hardware diagnostics, network testing, resource monitoring). This command runs unbound scripts on local or remote hardware.

## Interface

**Command:**
```
rufus invoke free <HARDWARE> <SCRIPT> [ARGS...]
```

**Arguments:**
- `HARDWARE`: target node (flowbie, fourty4, thinker)
- `SCRIPT`: script name or path to execute
- `ARGS`: arguments to pass to script

**Output:** Script output (stdout/stderr)

## Specification

**Behavior:**
1. Resolve hardware SSH connection
2. Execute script with arguments
3. Stream output
4. Report exit code

**Security:**
- Scripts must exist in trusted locations
- SSH key authentication
- Command logging for audit

**Edge cases:**
- Hardware unreachable → fail with timeout
- Script not found → report 404
- Execution timeout → kill and report
- Permission denied → report auth failure

## Implementation

Implemented in `command.sh`. SSH into hardware and execute scripts, capturing output.

## Dependencies

- SSH keys for hardware access
- Hardware manifest (HARDWARE_MANIFEST.md)

## Testing

Acceptance criteria:
- [ ] Can execute scripts on each hardware node
- [ ] Output captured correctly
- [ ] Timeouts work
- [ ] Exit codes reported

## Status Note

Built and operational. Used for low-level hardware diagnostics and maintenance.
