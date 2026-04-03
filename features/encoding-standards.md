---
status: draft
owner: rufus
priority: high
description: Define video/audio codec, bitrate, resolution, and quality presets for production
started: 2026-04-03
---

## Purpose

Rufus must maintain authoritative encoding standards for all video and audio content. This ensures consistency across recording sources and provides Mercury with predictable asset specifications for distribution (YouTube, podcast platforms, archives).

## Specification

**Input:** Content type (video, audio, stream)

**Output:** Encoding preset (codec, bitrate, resolution, frame rate, sample rate)

**Encoding Profiles:**
- **Video — Interview/Talking Head:**
  - Codec: H.264 (VP9 for archive)
  - Resolution: 1920x1080 (1080p)
  - Frame rate: 30 fps
  - Bitrate: 6 Mbps (live stream), 10 Mbps (archive)
  
- **Video — Screen Recording/Code Walkthrough:**
  - Codec: H.264 or VP9
  - Resolution: 1920x1080 (or 2560x1440 if source supports)
  - Frame rate: 60 fps
  - Bitrate: 8 Mbps (live), 12 Mbps (archive)
  
- **Audio — Podcast/Interview:**
  - Codec: AAC
  - Sample rate: 48 kHz
  - Bitrate: 128 kbps (stereo)
  - Format: MP3 for distribution, WAV for archive
  
- **Audio — Music/Ambient:**
  - Codec: AAC/MP3
  - Sample rate: 44.1 kHz or 48 kHz
  - Bitrate: 192 kbps (lossy) or lossless (FLAC)
  
- **Live Stream:**
  - Codec: H.264 (compatibility)
  - Resolution: 1920x1080
  - Bitrate: 4–6 Mbps (adaptive based on network)
  - Frame rate: 30 fps

**Behavior:**
- Generate OBS encoding presets from standard definitions
- Validate encoding parameters before recording starts
- Log encoding metadata in asset manifest
- Support transcoding to alternate formats for different platforms
- Monitor real-time encoding performance (CPU, dropped frames)

**Edge cases:**
- Insufficient bandwidth → use lower bitrate preset
- Source lower resolution than preset → scale appropriately
- Multi-source with mixed resolutions → normalize to target resolution

## Implementation

Not yet built. Needs:
1. encoding-standards.yaml (preset library)
2. encoding-validate.sh (pre-recording verification)
3. encoding-transcode.sh (format conversion for distribution)

## Dependencies

- OBS configuration management (for preset integration)
- Asset export standards (for format specifications)

## Testing

Acceptance criteria:
- [ ] All encoding presets match OBS codec availability
- [ ] Real-time encoding monitor detects CPU throttling
- [ ] Archive transcoding produces valid output files
- [ ] Mercury receives correct bitrate/codec metadata

## Status Note

Specifications drafted but not operationalized. Awaiting detailed bitrate calculations and network optimization.
