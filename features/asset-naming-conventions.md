---
status: draft
owner: rufus
priority: high
description: Standardized naming and organization for video, audio, and supporting assets
started: 2026-04-03
---

## Purpose

Consistent asset naming enables Mercury to automatically discover, organize, and publish recordings. Rufus must define naming conventions for raw recordings, edited cuts, thumbnails, transcripts, and supplementary files.

## Specification

**Input:** Content metadata (type, creator, date, subject)

**Output:** Asset filename and storage path following convention

**Asset Naming Format:**

```
<DATE>-<CREATOR>-<TYPE>-<SUBJECT>-<VERSION>.<EXT>

Examples:
  2026-04-03-faber-interview-kubernetes-scaling-001.mp4
  2026-04-03-faber-podcast-episode-42-draft.wav
  2026-04-03-faber-screencast-rust-async-v2.mkv
  2026-04-03-faber-stream-twitch-daily-standup.mp4
```

**Components:**
- `DATE`: YYYY-MM-DD (ISO format, recording date)
- `CREATOR`: Entity name (faber, etc.)
- `TYPE`: Content type (interview, podcast, screencast, stream, multi-camera)
- `SUBJECT`: Content topic (kebab-case, max 30 chars)
- `VERSION`: Sequential version (001, 002, draft, final)
- `EXT`: File extension (mp4, wav, mkv, webm, m4a)

**Storage Paths:**
```
~/.rufus/media/
├── 2026/
│   └── 04/
│       ├── raw/                    # Raw recordings
│       │   └── 2026-04-03-faber-interview-*.mp4
│       ├── archive/                # Full quality backups
│       │   └── 2026-04-03-faber-interview-*-archive.mkv
│       └── metadata/               # Accompanying files
│           ├── 2026-04-03-faber-interview-*.json (asset manifest)
│           ├── 2026-04-03-faber-interview-*.srt (captions)
│           ├── 2026-04-03-faber-interview-*.txt (transcript)
│           └── 2026-04-03-faber-interview-*.png (thumbnail)
```

**Asset Manifest (JSON):**
```json
{
  "id": "2026-04-03-faber-interview-kubernetes-scaling-001",
  "type": "interview",
  "creator": "faber",
  "date": "2026-04-03",
  "subject": "kubernetes-scaling",
  "duration_seconds": 1847,
  "recording": {
    "filename": "2026-04-03-faber-interview-kubernetes-scaling-001.mp4",
    "codec_video": "h264",
    "codec_audio": "aac",
    "resolution": "1920x1080",
    "bitrate": "6000k",
    "size_bytes": 1374000000
  },
  "metadata": {
    "thumbnail": "2026-04-03-faber-interview-kubernetes-scaling-001.png",
    "transcript": "2026-04-03-faber-interview-kubernetes-scaling-001.txt",
    "captions": "2026-04-03-faber-interview-kubernetes-scaling-001.srt",
    "created_timestamp": "2026-04-03T14:30:00Z",
    "checksum_sha256": "abc123..."
  }
}
```

**Behavior:**
- Generate filenames and directories automatically based on content metadata
- Create asset manifest (JSON) alongside every recording
- Validate naming compliance before handing off to Mercury
- Support searching by date, creator, type, or subject
- Preserve version history (001, 002, etc. for iterative recording)

**Edge cases:**
- Subject name > 30 chars → truncate and suffix with content hash
- Multiple recordings same day → use version suffix (001, 002, 003)
- Alternate formats (transcoding) → add format suffix (2026-04-03-...-h265.mp4)

## Implementation

Not yet built. Needs:
1. naming-conventions.yaml (format specifications)
2. generate-asset-name.sh (filename generation)
3. create-asset-manifest.sh (metadata generation)

## Dependencies

- Recording workflows (need content metadata)
- Asset export standards (coordinate with distribution formats)

## Testing

Acceptance criteria:
- [ ] Filename generated correctly from metadata
- [ ] Asset manifest created with all required fields
- [ ] Storage path conforms to date-based hierarchy
- [ ] Mercury can parse manifest and discover assets
- [ ] Checksum verification successful

## Status Note

Convention designed but not yet operationalized. Requires integration with recording workflows.
