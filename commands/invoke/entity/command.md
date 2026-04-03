---
status: complete
owner: rufus
priority: high
description: Invoke commands on external entities (Faber, Mercury, etc.)
completed: 2026-04-03
---

## Purpose

Rufus works with other entities in the koad:io ecosystem (Faber for content creation, Mercury for distribution). This command lets Rufus invoke capabilities on peer entities via trust bonds and inter-entity communication protocols.

## Interface

**Command:**
```
rufus invoke entity <ENTITY> <COMMAND> [ARGS...]
```

**Arguments:**
- `ENTITY`: target entity name (faber, mercury, vesta, etc.)
- `COMMAND`: command to invoke on the entity
- `ARGS`: arguments to pass through

**Output:** JSON response from invoked command

## Specification

**Behavior:**
1. Resolve trust bond to target entity
2. Establish communication channel
3. Invoke command with credentials
4. Return response

**Supported entities:**
- `faber` — Content creation (editing, audio mixing)
- `mercury` — Distribution and publishing
- `vesta` — Platform specs and governance
- `juno` — Orchestration coordination

**Edge cases:**
- Entity unreachable → timeout and report
- Trust bond missing → refuse and report
- Command not available → report error
- Permission denied → report authorization failure

## Implementation

Implemented in `command.sh`. Uses trust bonds and inter-entity comms protocol to invoke remote commands.

## Dependencies

- Trust bond protocol (VESTA-SPEC-003)
- Inter-entity comms (VESTA-SPEC-011)
- Peer entity availability

## Testing

Acceptance criteria:
- [ ] Can invoke commands on Faber
- [ ] Can invoke commands on Mercury
- [ ] Handles missing trust bonds
- [ ] Reports errors correctly

## Status Note

Built and operational. Primary mechanism for cross-entity coordination.
