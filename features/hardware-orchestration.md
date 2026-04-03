---
status: in-progress
owner: rufus
priority: critical
description: Coordinate recording hardware (flowbie, fourty4, thinker) for multi-location sessions
started: 2026-04-03
---

## Purpose

Rufus must orchestrate recording across the koad:io hardware inventory: flowbie (24/7 studio, X11, OBS source, physical cameras), fourty4 (Mac Mini, ollama inference, recording capability), and thinker (primary ops, coordination hub). This ensures consistent, synchronized recording across locations and enables multi-source content.

## Specification

**Input:** Hardware manifest request or session setup (list of sources to record, sync mode)

**Output:** Validated hardware status, recording coordination plan, deployment to each device

**Hardware Details:**
- **flowbie**: Linux, X11, OBS instance, connected cameras/mics, 24/7 streaming capability
- **fourty4**: macOS, Mac Mini, ollama inference, local recording, openclaw bridge (messaging)
- **thinker**: primary coordination node, scheduling, artifact management

**Capabilities:**
- List available hardware and capabilities (cameras, microphones, encoders)
- Health check hardware (network, disk space, CPU, encoding readiness)
- Coordinate clock synchronization across devices for multi-source recording
- Deploy recording commands to remote hardware via SSH/trust bonds
- Monitor hardware during recording (bitrate, temperature, dropped frames)
- Retrieve recordings from remote devices post-session
- Aggregate metadata across sources

**Behavior:**
1. Load hardware manifest (HARDWARE_MANIFEST.md)
2. Query each device for current status (available sources, load, disk space)
3. For multi-source sessions, synchronize clocks to within 100ms
4. Deploy recording parameters (scene, encoding, destination) to each device
5. Monitor all sources in real-time during session
6. Collect recordings to central artifact store (thinker)
7. Verify checksums and completeness before handoff to Mercury

**Edge cases:**
- Device unreachable → skip or use fallback source
- Clock drift > 100ms → re-sync or mark for post-sync correction
- Network latency → adjust stream bitrate or reduce quality
- Disk space critically low → alert and prepare overflow handling

## Implementation

In progress. Commands:
- `status/command.sh` — basic hardware status (exists)
- `team/status/command.sh` — team/hardware coordination status (exists)
- Needs: hardware-manifest.sh (full inventory), hardware-health.sh (deep diagnostics), orchestrate-recording.sh (multi-device coordination)

## Dependencies

- HARDWARE_MANIFEST.md (inventory must exist)
- Inter-entity communication (koad openclaw bridge)
- Trust bonds with hardware entities

## Testing

Acceptance criteria:
- [ ] Hardware manifest lists all devices with capabilities
- [ ] Health check detects offline or degraded hardware
- [ ] Multi-device clock sync within 100ms accuracy
- [ ] Recording coordinates across 2+ devices simultaneously
- [ ] Metadata aggregated correctly post-session

## Status Note

Partial implementation. Awaiting detailed HARDWARE_MANIFEST.md and integration with Juno for device orchestration.
