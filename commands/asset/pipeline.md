---
status: draft
owner: rufus
priority: high
description: Manage asset pipeline from raw recording through post-production to export
---

## Purpose

Rufus must orchestrate the full asset lifecycle: creating manifests, organizing recordings, coordinating post-production with Faber, and exporting final assets to Mercury. This command provides visibility and control over asset status throughout the pipeline.

## Interface

**Commands:**
- `rufus asset manifest <RECORDING_ID>` — Generate or view asset metadata
- `rufus asset list` — List all assets and their status
- `rufus asset transcode <ASSET> <FORMAT>` — Export to platform-specific format
- `rufus asset validate <ASSET>` — Verify file integrity and metadata
- `rufus asset handoff <ASSET>` — Prepare final asset for Mercury delivery

**Arguments:**
- `RECORDING_ID`: Asset identifier (2026-04-03-faber-interview-001)
- `FORMAT`: youtube | podcast | archive | social-media | custom
- `--quality` (optional): high | medium | low (transcoding preset)
- `--platforms` (optional): Comma-separated list of target platforms

**Output:** JSON with asset status, manifest, export paths

## Specification

**Asset Manifest:**
```json
{
  "id": "2026-04-03-faber-interview-kubernetes-scaling-001",
  "type": "interview",
  "creator": "faber",
  "date": "2026-04-03",
  "subject": "kubernetes-scaling",
  "status": "exported",
  "recording": {
    "file": "/home/koad/.rufus/media/2026/04/raw/2026-04-03-faber-interview-001.mp4",
    "size_bytes": 1374000000,
    "duration_seconds": 1847,
    "codec_video": "h264",
    "resolution": "1920x1080",
    "bitrate_video": "6000k"
  },
  "metadata": {
    "thumbnail": "/home/koad/.rufus/media/2026/04/metadata/2026-04-03-faber-interview-001.png",
    "transcript": "/home/koad/.rufus/media/2026/04/metadata/2026-04-03-faber-interview-001.txt",
    "captions": "/home/koad/.rufus/media/2026/04/metadata/2026-04-03-faber-interview-001.srt"
  },
  "checksum_sha256": "abc123...",
  "post_production": {
    "editing_status": "in_progress",
    "assigned_to": "faber",
    "notes": "Review edit_notes_001.md"
  },
  "exports": {
    "youtube": {
      "file": "/home/koad/.rufus/media/2026/04/exports/2026-04-03-faber-interview-001-youtube.mp4",
      "status": "ready"
    },
    "podcast": {
      "file": "/home/koad/.rufus/media/2026/04/exports/2026-04-03-faber-interview-001-podcast.m4a",
      "status": "ready"
    }
  }
}
```

**Asset Lifecycle:**
1. **Raw** — After recording capture
2. **Manifest Created** — Metadata and checksums computed
3. **Post-Production** — Editing assigned to Faber (optional)
4. **Exported** — Transcoded to distribution formats
5. **Validated** — All files verified and metadata complete
6. **Handed Off** — Delivered to Mercury via trust bond

**Transcoding:**
- Load encoding presets from encoding-standards.md
- Transcode raw recording to platform-specific formats (YouTube, podcast, archive)
- Generate metadata (thumbnails, captions, descriptions)
- Validate output file integrity

**Validation:**
- Verify file format matches specification
- Check duration and codec match manifest
- Validate checksums
- Ensure all metadata complete
- Test playback (sample frames)

**Handoff to Mercury:**
- Create delivery package with all exports and metadata
- Sign manifest with Rufus key
- Push to Mercury via trust bond
- Log handoff timestamp

**Edge cases:**
- Post-production taking too long → alert and escalate
- Transcode quality insufficient → re-encode with higher bitrate
- File corruption detected → recover from backup or re-record
- Missing metadata → auto-generate or prompt for input

## Dependencies

- `asset-naming-conventions.md` (filename/path standards)
- `export-standards.md` (transcoding formats)
- `post-production-direction.md` (editing workflow)
- Mercury trust bond (for delivery)

## Status Note

Not yet built. Requires integration with post-production workflow and Mercury delivery.
