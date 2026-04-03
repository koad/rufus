---
status: draft
owner: rufus
priority: high
description: Final asset export formats, codec specifications, and platform-specific delivery standards
started: 2026-04-03
---

## Purpose

Different distribution channels (YouTube, podcast platforms, archives, social media) require different asset formats. Rufus must define export standards for each destination, ensuring Mercury receives properly formatted files ready for upload.

## Specification

**Input:** Final edited asset and target platform(s)

**Output:** Exported file(s) in platform-specific format

**Export Targets & Formats:**

### 1. YouTube Video
- **Codec:** H.264 video, AAC audio
- **Resolution:** 1920x1080 (up to 4K if source available)
- **Frame rate:** 30 fps (or 60 fps if source)
- **Bitrate:** 10 Mbps video, 128 kbps audio
- **Container:** MP4 (.mp4)
- **Color space:** Rec. 709
- **Metadata:** Title, description, tags, thumbnail (PNG, 1280x720)

### 2. Podcast Platforms (Spotify, Apple Podcasts, etc.)
- **Codec:** MP3 or AAC
- **Sample rate:** 48 kHz
- **Bitrate:** 128 kbps (mono or stereo)
- **Container:** MP3 (.mp3) or M4A (.m4a)
- **Metadata:** Episode title, description, guest names, publication date
- **Cover art:** PNG/JPG 3000x3000 or 1400x1400

### 3. Archive/Long-Term Storage
- **Codec:** VP9 or H.265 (modern codecs for efficiency)
- **Resolution:** Original source resolution (up to 4K)
- **Bitrate:** 15–20 Mbps (maximum quality)
- **Container:** MKV (.mkv)
- **Color:** Full color space (Rec. 2020 if available)
- **Metadata:** All preservation metadata included

### 4. Social Media (Twitter/X, TikTok, Instagram)
- **Video codec:** H.264
- **Resolution:** 1080x1920 (vertical), 1920x1080 (horizontal)
- **Frame rate:** 30 fps
- **Duration:** < 10 min (Twitter), < 60 sec (TikTok), < 15 min (Instagram)
- **Bitrate:** 4–6 Mbps
- **Container:** MP4

### 5. Transcripts & Captions
- **Format:** SRT or WebVTT for video, plain text for transcripts
- **Encoding:** UTF-8
- **Language:** English (other languages as needed)
- **Accuracy:** > 98% (auto-generated acceptable, review recommended)

**Behavior:**
- Transcode final asset to all required formats automatically
- Generate platform-specific metadata and thumbnails
- Validate file integrity (checksums, duration, codec verification)
- Create asset delivery package with all files and metadata
- Log export manifest for Mercury audit trail

**Edge cases:**
- Source resolution lower than target → upscale or use best available
- Audio-only content → export only to podcast platforms
- Very long content (> 2 hours) → warn about platform limits or suggest splitting
- Multiple languages needed → coordinate subtitle generation

## Implementation

Not yet built. Needs:
1. export-presets.yaml (format/codec specifications)
2. export-video.sh (transcode to video formats)
3. export-audio.sh (transcode to audio formats)
4. export-metadata.sh (generate platform-specific metadata)
5. export-validate.sh (verify exported files)

## Dependencies

- Encoding standards (codec specifications)
- Asset naming conventions (asset organization)
- Post-production direction (final asset source)

## Testing

Acceptance criteria:
- [ ] Export to YouTube format succeeds and validates
- [ ] Podcast export plays correctly on Spotify/Apple Podcasts
- [ ] Archive export matches source quality and duration
- [ ] Social media formats display correctly on each platform
- [ ] All metadata and captions included in exports
- [ ] File checksums verified, no corruption

## Status Note

Format specifications drafted but export pipeline not yet implemented. Requires testing on actual distribution platforms.
