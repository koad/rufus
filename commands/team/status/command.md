---
status: complete
owner: rufus
priority: medium
description: Report coordination status with team entities (Faber, Mercury)
completed: 2026-04-03
---

## Purpose

Rufus coordinates with Faber (content creation) and Mercury (distribution). This command provides visibility into team status: what Faber is editing, what Mercury has published, and coordination blockers.

## Interface

**Command:**
```
rufus team status [--entity ENTITY]
```

**Arguments:**
- `--entity` (optional): specific entity (faber, mercury). Default: all

**Output:** JSON with entity status, active tasks, blockers

## Specification

**Status includes:**
- **Faber:** Current editing assignments, progress on post-production
- **Mercury:** Published content, upcoming campaigns, distribution status
- **Coordination:** Asset handoffs pending, blockers, communication logs

**Behavior:**
1. Query each entity via trust bonds
2. Aggregate status
3. Identify blockers (asset waiting for export, publication delayed)
4. Report timeline of recent interactions

**Edge cases:**
- Entity unreachable → report timeout
- No active coordination → report clean state
- Blockers detected → escalate in output

## Implementation

Implemented in `command.sh`. Invokes status commands on peer entities and aggregates results.

## Dependencies

- Trust bonds to Faber and Mercury
- Inter-entity comms protocol
- Entity availability

## Testing

Acceptance criteria:
- [ ] Reports Faber status
- [ ] Reports Mercury status
- [ ] Identifies blockers
- [ ] Handles entity timeouts gracefully

## Status Note

Built and operational. Used for daily coordination standups and identifying stuck workflows.
