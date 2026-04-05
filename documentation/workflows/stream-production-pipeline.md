---
title: Stream Production Pipeline — Encoder Settings & Quality Tiers
owner: rufus
status: active
updated: 2026-04-05
closes-issue: https://github.com/koad/rufus/issues/4
---

# Stream Production Pipeline — Encoder Settings & Quality Tiers

This document defines the full production pipeline from live session to streamed output, including encoder configurations, quality tiers for different hardware and network conditions, and platform-specific delivery parameters.

---

## Pipeline Overview

```
[Source Material]
    ↓
[OBS / asciinema / ffmpeg capture]
    ↓
[Local encoding — quality tier determined by hardware]
    ↓
[Stream output (RTMP) or local recording (MKV/MP4)]
    ↓
[Post-processing — remux, trim, export]
    ↓
[Mercury delivery — YouTube, Twitter, Reddit]
```

---

## Quality Tiers

Three tiers based on available hardware and network conditions.

### Tier 1 — Studio Quality (flowbie with GPU)

**When to use:** All content where quality matters. flowbie is the primary studio.

| Setting | Value |
|---------|-------|
| Encoder | NVENC H.264 (GPU hardware) |
| Resolution | 2560x1440 (source) → 1920x1080 (stream output) |
| FPS | 60 |
| Downscale filter | Lanczos |
| Rate control | CBR (stream) / CQP 18 (local recording) |
| Stream bitrate | 8000 kbps (YouTube) / 6000 kbps (Twitch) |
| Keyframe interval | 2 seconds |
| B-frames | 2 |
| Profile | High |
| Level | 4.2 |
| Audio codec | AAC 320 kbps stereo (recording), 160 kbps (stream) |
| Container | MKV (recording), FLV (stream) |

**NVENC settings in OBS:**
- Preset: Quality
- Multipass: Full (2-pass quality)
- Psycho Visual Tuning: enabled
- GPU: 0 (first CUDA device)
- Max B-frames: 2

---

### Tier 2 — Standard (any machine, software encode)

**When to use:** Recordings where GPU is unavailable or underpowered for 60fps encoding.

| Setting | Value |
|---------|-------|
| Encoder | x264 (software) |
| Resolution | 1920x1080 |
| FPS | 30 (drop to 30 to reduce CPU load) |
| Downscale filter | Bicubic |
| Rate control | CBR (stream) / CRF 20 (local recording) |
| Stream bitrate | 4500 kbps |
| Keyframe interval | 2 seconds |
| CPU preset | veryfast (OBS) or fast (ffmpeg) |
| Profile | High |
| Audio codec | AAC 160 kbps |
| Container | MKV (recording) |

**x264 tuning:**
- `tune=fastdecode` if CPU limited
- Avoid `--tune animation` — all content is screen/face
- No lookahead needed for streaming; lookahead for local recording: 40 frames

---

### Tier 3 — Minimal / Terminal (thinker, no OBS)

**When to use:** Entity session recordings where only terminal capture is possible. Text-only output. asciinema is primary; ffmpeg fallback.

| Setting | Value |
|---------|-------|
| Primary tool | asciinema |
| Format | .cast (native asciinema) |
| Export format | MP4 via `agg` or ffmpeg post-processing |
| Resolution | Terminal-defined (export at 1920x1080 equivalent) |
| FPS | 30 (asciinema timestamps are variable; export at 30fps) |
| Audio | Voice-over added in post (not live) |
| Encoding | ffmpeg x264 CRF 22 for exported MP4 |

**asciinema export pipeline:**
```bash
# Option 1: agg (asciinema gif generator — also exports mp4)
agg --fps 30 input.cast output.gif
# Convert gif → mp4 for distribution
ffmpeg -i output.gif -movflags faststart -pix_fmt yuv420p output.mp4

# Option 2: Direct ffmpeg from cast (requires svg2video or custom script)
# Preferred: use asciinema's built-in player embed for web; ffmpeg for social
```

---

## Platform-Specific Delivery Parameters

### YouTube

| Setting | Value |
|---------|-------|
| Container | MP4 |
| Video codec | H.264 |
| Resolution | 1920x1080 (minimum), 2560x1440 (preferred) |
| FPS | 60 |
| Bitrate | 16–25 Mbps for 1440p; 8–12 Mbps for 1080p (YT re-encodes; higher is better) |
| Color space | BT.709 |
| Audio codec | AAC 320 kbps stereo |
| Chapters | Via description `00:00 Section Name` format |
| Thumbnail | 1280x720, JPG or PNG, < 2MB |

**Upload note:** Upload highest-quality source file. YouTube will re-encode. No pre-degradation needed.

**ffmpeg export for YouTube:**
```bash
ffmpeg -i raw.mkv \
  -c:v libx264 \
  -crf 15 \
  -preset slow \
  -profile:v high \
  -level 4.2 \
  -pix_fmt yuv420p \
  -c:a aac \
  -b:a 320k \
  -movflags +faststart \
  youtube-ready.mp4
```

---

### Twitter / X

| Setting | Value |
|---------|-------|
| Container | MP4 |
| Video codec | H.264 |
| Resolution | 1280x720 |
| FPS | 30 |
| Max duration | 2 minutes 20 seconds (2:20) |
| Max file size | 512 MB |
| Bitrate | ~5 Mbps |
| Audio | AAC 128 kbps |

**Twitter clip export:**
```bash
ffmpeg -i final.mp4 \
  -ss 00:00:00 -to 00:01:00 \
  -c:v libx264 \
  -crf 23 \
  -preset fast \
  -vf "scale=1280:720" \
  -pix_fmt yuv420p \
  -c:a aac \
  -b:a 128k \
  -movflags +faststart \
  clip-twitter.mp4
```

---

### Reddit (r/LocalLLaMA, r/selfhosted, etc.)

Post as YouTube link — no direct Reddit video upload. Include:
- Top-level comment with chapter breakdown (same format as YouTube description)
- Link to relevant repo (`github.com/koad/<entity>`)
- No native upload required

---

## Live Streaming Configuration

### YouTube Live (primary stream target)

OBS Output settings:
```
Service: YouTube - RTMPS
Server: Primary (auto-selected)
Stream Key: [from YouTube Studio → Go Live]
Bitrate: 8000 kbps
Keyframe interval: 2s
Encoder: NVENC H.264 (Tier 1) or x264 CBR (Tier 2)
Audio bitrate: 160 kbps AAC
```

**Required for stream health:**
- Minimum 10 Mbps upload bandwidth (test with `speedtest-cli` before stream)
- Enable "Rescale Output" in OBS Output settings if canvas is 1440p but stream is 1080p
- Always record simultaneously: OBS Settings → Output → Recording tab, separate from stream settings

### Twitch (secondary, optional)

```
Service: Twitch
Bitrate: 6000 kbps (max for partners) / 4500 kbps (non-partner)
All other settings: same as YouTube Live
```

---

## Monitoring During Production

Critical metrics to watch during any live or recorded session:

| Metric | Threshold | Action if exceeded |
|--------|-----------|-------------------|
| Dropped frames (encoding) | > 0.5% | Switch to Tier 2 or lower resolution |
| Dropped frames (rendering) | > 0.5% | Close other GPU-intensive apps |
| Dropped frames (network) | > 0.1% | Lower bitrate 10%, check ethernet vs WiFi |
| CPU usage (OBS) | > 80% | Change x264 preset to veryfast or ultrafast |
| Disk space | < 5 GB | Stop recording, clear space, resume |

OBS status bar shows these in real-time. For remote machines, query via WebSocket:
```bash
obs-cmd --websocket obsws://flowbie:4455/PASSWORD stats
```

---

## Post-Processing Pipeline

After recording stops, before Mercury handoff:

```bash
# 1. Remux from MKV to MP4 (safe, no quality loss)
ffmpeg -i raw.mkv -c copy raw-remuxed.mp4

# 2. Trim dead air at start/end (update timestamps per recording)
ffmpeg -i raw-remuxed.mp4 -ss 00:00:03 -to 00:06:45 -c copy trimmed.mp4

# 3. Export final cut for YouTube (full quality)
ffmpeg -i trimmed.mp4 \
  -c:v libx264 -crf 15 -preset slow -pix_fmt yuv420p \
  -c:a aac -b:a 320k -movflags +faststart \
  final.mp4

# 4. Export 1-minute clip for Twitter
ffmpeg -i trimmed.mp4 \
  -ss 00:00:00 -to 00:01:00 \
  -c:v libx264 -crf 23 -preset fast -vf "scale=1280:720" \
  -c:a aac -b:a 128k -movflags +faststart \
  clip-twitter.mp4

# 5. Verify outputs
ffprobe -v quiet -print_format json -show_streams final.mp4 | jq '.streams[0] | {width, height, r_frame_rate, codec_name}'
```

---

## Status

- [x] Quality tiers defined (Tier 1 / 2 / 3)
- [x] Platform delivery parameters (YouTube, Twitter, Reddit)
- [x] Live streaming configuration
- [x] Monitoring thresholds
- [x] Post-processing pipeline (ffmpeg commands)
- [ ] NVENC confirmed available on flowbie
- [ ] YouTube Live stream key stored in `~/.rufus/.credentials`
- [ ] First Tier 1 test recording completed on flowbie
