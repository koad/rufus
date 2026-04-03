---
status: draft
owner: rufus
priority: critical
description: Templated recording workflows for video, audio, and stream production
started: 2026-04-03
---

## Purpose

Rufus needs standardized, repeatable recording workflows for different content types (interview, podcast, live stream, screen recording, multi-camera shoot). Each workflow specifies hardware, OBS scene, encoding settings, and post-production handoff to Mercury.

## Specification

**Input:** Workflow type (video-interview, podcast-audio, live-stream, screen-recording), content metadata (title, creator, duration estimate)

**Output:** Recording artifact with metadata, encoding status, asset manifest for Mercury

**Workflow Types:**
- `video-interview` — two-person on-camera discussion (web cam + microphone)
- `podcast-audio` — long-form audio with multi-speaker setup
- `live-stream` — real-time broadcast with chat/audience (Twitch, YouTube)
- `screen-recording` — code walkthrough or demo with voiceover
- `multi-camera` — coordinated recording from multiple hardware locations

**Behavior per workflow:**
1. **Initialization:** Select hardware (flowbie, fourty4, thinker), load OBS scene, test audio/video
2. **Recording:** Monitor bitrate, CPU usage, dropped frames; alert if degrading
3. **Finalization:** Stop recording, compute checksums, generate metadata
4. **Handoff:** Create asset manifest (filename, duration, codecs, resolution) and pass to Mercury via trust bond

**Edge cases:**
- Network drop during stream → recover gracefully, log gap
- Microphone failure → switch to fallback input or pause
- Storage full → alert and stop recording before corruption
- Multi-location sync drift → timestamp all segments for post-sync

## Implementation

Not yet built. Needs workflow playbooks in OPERATIONS.md and integration with hardware-orchestration.

## Dependencies

- OBS configuration management (obs-configuration-management.md)
- Hardware orchestration (hardware-orchestration.md)
- Asset naming conventions (asset-naming-conventions.md)

## Testing

Acceptance criteria:
- [ ] Complete video interview workflow from start to finish
- [ ] Complete podcast workflow with multi-speaker setup
- [ ] Live stream workflow with audience/chat integration
- [ ] All recordings have correct metadata and asset manifest
- [ ] Mercury can locate and process recordings via manifest

## Status Note

Defined in CLAUDE.md and README.md but not yet operationalized. Requires detailed OPERATIONS.md playbooks for each workflow type.
