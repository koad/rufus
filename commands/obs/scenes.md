---
status: draft
owner: rufus
priority: high
description: Manage OBS scene configuration, load scenes, and control multi-source routing
---

## Purpose

Rufus needs fine-grained control over OBS scene configuration across recording hardware. This command loads pre-defined scene templates, switches between scenes during recording, and coordinates multi-source mixing.

## Interface

**Commands:**
- `rufus obs load <SCENE>` — Load OBS scene template on specified hardware
- `rufus obs list` — List available scene templates
- `rufus obs switch <SCENE>` — Switch active scene during recording
- `rufus obs test <SCENE>` — Test scene on hardware without recording
- `rufus obs export <SCENE>` — Export current scene to version control

**Arguments:**
- `SCENE`: interview | screen-recording | live-stream | multi-camera | podcast
- `--hardware` (optional): Target device (flowbie, fourty4); default: all
- `--validate` (optional): Verify all sources are available before loading

**Output:** JSON with scene status, source availability, encoding parameters

## Specification

**Scene Management:**
```json
{
  "scene": "interview",
  "status": "loaded",
  "hardware": "flowbie",
  "sources": {
    "host_camera": {"status": "connected", "resolution": "1920x1080", "fps": 30},
    "guest_camera": {"status": "connected", "resolution": "1920x1080", "fps": 30},
    "microphone_host": {"status": "connected", "sample_rate": 48000},
    "microphone_guest": {"status": "connected", "sample_rate": 48000},
    "background_audio": {"status": "ready", "file": "interview_bg.mp3"}
  },
  "audio_mixing": {
    "host_volume": -3,
    "guest_volume": -3,
    "background_volume": -20,
    "output_loudness_lufs": -16
  },
  "encoding": {
    "codec_video": "h264",
    "bitrate": "6000k",
    "resolution": "1920x1080",
    "fps": 30
  }
}
```

**Scene Templates:**
- Interview: Two-camera layout, host/guest audio mixing, background music
- Screen Recording: Display capture + face-cam optional, system audio capture
- Live Stream: Scene switching, chat overlay, bitrate adaptation
- Multi-Camera: Coordinated recording from multiple hardware locations
- Podcast: Audio-focused, optional background video or static image

**Behavior:**
1. Validate scene template exists and is compatible with hardware
2. Query hardware for available sources (cameras, mics, displays)
3. Load scene XML/JSON configuration into OBS
4. Verify all sources are connected and functioning
5. Set audio mixing levels and filters
6. Configure encoding parameters
7. Perform test render to verify quality
8. Return scene readiness status

**Edge cases:**
- Required source missing → suggest alternatives or fail gracefully
- Source resolution mismatch → scale automatically or warn
- Audio level clipping → auto-adjust or alert for manual adjustment
- Multi-camera sync drift → flag for correction after recording

## Dependencies

- `obs-configuration-management.md` (scene definitions)
- `hardware-orchestration.md` (device capability checking)
- `encoding-standards.md` (codec validation)

## Status Note

Not yet built. Requires OBS WebSocket API integration and scene template library.
