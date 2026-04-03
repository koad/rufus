---
status: in-progress
owner: rufus
priority: critical
description: OBS scene configuration, source management, and live mixing setup
started: 2026-04-03
---

## Purpose

Rufus must be able to configure, manage, and version-control OBS (Open Broadcaster Software) scenes, sources, and mixing profiles across multiple recording locations (flowbie 24/7 studio, fourty4 inference box, thinker ops). This enables consistent, repeatable stream and recording workflows.

## Specification

**Input:** OBS configuration request (scene setup, source definitions, mixing profile)

**Output:** Validated OBS scene file (JSON/XML), deployment status

**Capabilities:**
- Define scene templates (interview, coding stream, multi-camera, screen recording)
- Configure audio routing and mixing (sources, levels, filters)
- Set video encoding profiles and bitrate presets
- Define source inputs (webcam, screen, microphone, external feeds)
- Export scenes as version-controlled files
- Deploy to OBS instances across hardware

**Behavior:**
- Parse scene definitions from YAML or JSON
- Validate source availability on target hardware
- Generate OBS-compatible XML configuration
- Test streaming/recording output before deployment
- Log configuration changes in git

**Edge cases:**
- Source unavailable on target hardware → fallback to alternative or warn
- Bandwidth constraints → adjust bitrate or enable quality profiles
- Multi-source conflicts → prioritize critical sources (primary speaker, screen share)

## Implementation

In progress. Needs:
1. OBS scene template library (YAML-based definitions)
2. Configuration validation and deployment script
3. Scene documentation (OBS_SETUP.md)

## Dependencies

- Hardware manifest (hardware-orchestration.md)
- Asset encoding standards (encoding-standards.md)

## Testing

Acceptance criteria:
- [ ] OBS scene loads without errors on flowbie
- [ ] Audio sources route correctly through mixer
- [ ] Video encoding uses correct bitrate/codec
- [ ] Multi-camera switching works in scene
- [ ] Configuration can be version-controlled and reproduced

## Status Note

Core design in CLAUDE.md. Awaiting detailed OBS_SETUP.md and scene template definitions.
