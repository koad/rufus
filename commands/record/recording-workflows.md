---
status: draft
owner: rufus
priority: critical
description: Start and manage recording sessions (video, audio, stream)
---

## Purpose

Rufus needs to initiate and manage recording sessions across different workflow types: interviews, podcasts, live streams, and screen recordings. This command initializes hardware, loads OBS scenes, performs test recordings, and manages the recording lifecycle.

## Interface

**Commands:**
- `rufus record start <TYPE>` — Initialize recording session
- `rufus record stop` — End active recording and finalize asset
- `rufus record status` — Show current recording state
- `rufus record test` — Run test recording (quick check)

**Arguments:**
- `TYPE`: video-interview | podcast-audio | live-stream | screen-recording | multi-camera
- `--hardware` (optional): Specify target hardware (flowbie, fourty4, thinker)
- `--destination` (optional): Override output path
- `--duration` (optional): Expected duration (for warnings/alerts)

**Output:** JSON with recording metadata, file path, duration, codec information

## Specification

**Behavior:**
1. Validate workflow type and load configuration
2. Check hardware availability and health
3. Load and test OBS scene
4. Verify microphone/camera inputs
5. Create asset metadata (recording ID, timestamps)
6. Start recording on all designated devices
7. Monitor recording in real-time (bitrate, dropped frames, storage)
8. On stop: finalize recording, compute checksums, generate asset manifest
9. Return recording metadata to caller

**Output Format:**
```json
{
  "id": "2026-04-03-faber-interview-001",
  "status": "recording",
  "start_timestamp": "2026-04-03T14:30:00Z",
  "expected_duration_seconds": 1800,
  "recording_file": "/home/koad/.rufus/media/2026/04/raw/2026-04-03-faber-interview-001.mp4",
  "hardware": ["flowbie", "fourty4"],
  "encoding": {
    "codec_video": "h264",
    "codec_audio": "aac",
    "bitrate_video": "6000k",
    "bitrate_audio": "128k"
  }
}
```

**Edge cases:**
- OBS not responding → fail with error and recovery instructions
- Microphone not detected → prompt to connect or use fallback
- Storage space insufficient → error before starting
- Multi-device sync drift → log for post-sync correction

## Dependencies

- `hardware-orchestration.md` (device status)
- `obs-configuration-management.md` (scene loading)
- `encoding-standards.md` (codec validation)
- `recording-workflows.md` (workflow definitions)

## Status Note

Not yet built. Requires integration with hardware health checks and OBS automation.
