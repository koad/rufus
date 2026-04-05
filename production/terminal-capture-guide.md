---
title: "Terminal Capture Guide — asciinema + Post-Production"
owner: Rufus
created: 2026-04-05
applies-to: all terminal-capture productions (OBS pending)
status: active
---

# Terminal Capture Guide
## asciinema Recording + Post-Production Workflow

This guide covers the full terminal-capture pipeline used when OBS/studio is unavailable.
Terminal-capture mode is the default for all entity session recordings until flowbie studio is confirmed.

---

## Prerequisites

```bash
# Install asciinema (if not present)
pip install asciinema
# or on Debian/Ubuntu:
sudo apt install asciinema

# Install ffmpeg (for mp4 export)
sudo apt install ffmpeg

# Install agg (asciinema gif generator) — optional, for gif output
cargo install agg
# or via npm:
npm install -g @asciinema/agg
```

---

## Recording Command

### Standard entity session recording:

```bash
asciinema rec \
  --title "Sibyl Does Research — koad:io Live Session, Apr 7 2026" \
  --idle-time-limit 2 \
  --env TERM,SHELL \
  ~/.rufus/recordings/2026-04-07-sibyl-research-raw.cast
```

**Flag explanations:**
- `--title` — embeds the title in the cast file metadata
- `--idle-time-limit 2` — collapses idle gaps longer than 2 seconds to 2 seconds (prevents long pauses bloating the recording)
- `--env TERM,SHELL` — captures minimal env (do not expose secrets via `--env`)
- Output path follows filename convention (see below)

### For sessions expected to run 30+ minutes:

```bash
# Use script as a fallback if asciinema has issues with long sessions
script -t 2> ~/.rufus/recordings/2026-04-07-sibyl-research-timing.txt \
  ~/.rufus/recordings/2026-04-07-sibyl-research-raw.log
```

---

## Filename Convention

All recordings use the format:

```
YYYY-MM-DD-<production-slug>-<stage>.ext
```

| Stage | Suffix | Example |
|-------|--------|---------|
| Raw capture | `-raw.cast` | `2026-04-07-sibyl-research-raw.cast` |
| Edited/trimmed cast | `-edit.cast` | `2026-04-07-sibyl-research-edit.cast` |
| GIF export | `-preview.gif` | `2026-04-07-sibyl-research-preview.gif` |
| MP4 export | `-final.mp4` | `2026-04-07-sibyl-research-final.mp4` |
| 1-min clip | `-clip.mp4` | `2026-04-07-sibyl-research-clip.mp4` |
| Thumbnail | `-thumb.png` | `2026-04-07-sibyl-research-thumb.png` |

All files land in `~/.rufus/recordings/` (gitignored — large binaries).

---

## Playback

### Play back a cast file locally:

```bash
asciinema play ~/.rufus/recordings/2026-04-07-sibyl-research-raw.cast
```

### Play at a different speed:

```bash
# 2x speed (for review)
asciinema play --speed 2 ~/.rufus/recordings/2026-04-07-sibyl-research-raw.cast

# 0.5x speed (for detailed review of fast sections)
asciinema play --speed 0.5 ~/.rufus/recordings/2026-04-07-sibyl-research-raw.cast
```

---

## Trimming / Editing a Cast File

asciinema cast files are newline-delimited JSON. Use `asciinema-edit` for trimming:

```bash
# Install asciinema-edit
pip install asciinema-edit

# Trim first N seconds (remove pre-roll stumbling)
asciinema-edit cut --start 0 --end 5 \
  -o ~/.rufus/recordings/2026-04-07-sibyl-research-edit.cast \
  ~/.rufus/recordings/2026-04-07-sibyl-research-raw.cast

# Speed up a section (e.g., 60s–480s at 2x for inference section)
asciinema-edit speed --start 60 --end 480 --factor 2 \
  -o ~/.rufus/recordings/2026-04-07-sibyl-research-edit.cast \
  ~/.rufus/recordings/2026-04-07-sibyl-research-edit.cast
```

**Manual approach** (when asciinema-edit unavailable):
Cast files are plain JSON lines. Each line: `[timestamp, "o", "output_text"]`.
You can adjust timestamps with a Python one-liner:

```python
import json, sys

factor = 2.0   # speed multiplier
start_ts = 60  # seconds to start speedup
end_ts = 480   # seconds to end speedup

with open('raw.cast') as f:
    header = json.loads(f.readline())
    print(json.dumps(header))
    for line in f:
        event = json.loads(line)
        ts = event[0]
        if start_ts <= ts <= end_ts:
            event[0] = start_ts + (ts - start_ts) / factor
        elif ts > end_ts:
            event[0] = start_ts + (end_ts - start_ts) / factor + (ts - end_ts)
        print(json.dumps(event))
```

```bash
python3 speedup.py < 2026-04-07-sibyl-research-raw.cast > 2026-04-07-sibyl-research-edit.cast
```

---

## Convert to GIF

For Twitter/X preview and embedding:

```bash
# Using agg (recommended — best quality)
agg \
  --theme monokai \
  --font-size 14 \
  --speed 1.5 \
  ~/.rufus/recordings/2026-04-07-sibyl-research-edit.cast \
  ~/.rufus/recordings/2026-04-07-sibyl-research-preview.gif
```

**GIF size target:** Under 15MB for Twitter/X compatibility. If over, reduce `--speed` or trim the cast further.

---

## Convert to MP4

For YouTube upload and archival:

```bash
# Step 1: Convert cast to raw video via asciinema server (self-hosted) or local render
# Using agg to produce frames, then ffmpeg to encode:

# Option A — agg direct to mp4 (if supported by your agg version):
agg \
  --theme monokai \
  --font-size 16 \
  ~/.rufus/recordings/2026-04-07-sibyl-research-edit.cast \
  ~/.rufus/recordings/2026-04-07-sibyl-research-final.mp4

# Option B — ffmpeg from gif:
ffmpeg \
  -i ~/.rufus/recordings/2026-04-07-sibyl-research-preview.gif \
  -vf "scale=1920:-1:flags=lanczos,fps=30" \
  -c:v libx264 -crf 18 -preset slow \
  -pix_fmt yuv420p \
  ~/.rufus/recordings/2026-04-07-sibyl-research-final.mp4
```

**MP4 specs for YouTube:**
- Resolution: 1920×1080 (upscale terminal output to fill — use ffmpeg scale filter)
- FPS: 30
- Codec: H.264, CRF 18–22
- Pixel format: yuv420p (required for YouTube compatibility)

---

## Adding Audio (Background Music)

If lo-fi music is desired during inference sections:

```bash
# Overlay audio on a section of the mp4
ffmpeg \
  -i ~/.rufus/recordings/2026-04-07-sibyl-research-final.mp4 \
  -i ~/.rufus/audio/lofi-ambient-track.mp3 \
  -filter_complex "[1:a]volume=0.15[a]" \
  -map 0:v -map "[a]" \
  -c:v copy -c:a aac -shortest \
  ~/.rufus/recordings/2026-04-07-sibyl-research-with-audio.mp4
```

**Audio note:** Volume at 0.15 (15%) — background music should be barely audible. The terminal is the content.

---

## Extract 1-Minute Clip

```bash
ffmpeg \
  -i ~/.rufus/recordings/2026-04-07-sibyl-research-final.mp4 \
  -ss 00:00:00 -t 00:01:00 \
  -c copy \
  ~/.rufus/recordings/2026-04-07-sibyl-research-clip.mp4
```

Adjust `-ss` (start) and `-t` (duration) per the shot script's clip cut notes.

---

## Extract Thumbnail

```bash
# Extract a single frame at the git log moment (~12:30 in the final cut)
ffmpeg \
  -i ~/.rufus/recordings/2026-04-07-sibyl-research-final.mp4 \
  -ss 00:12:30 -vframes 1 \
  ~/.rufus/recordings/2026-04-07-sibyl-research-thumb.png
```

**Thumbnail target frame:** The `git log --oneline` output showing the commit hash. This is the visual proof the whole video delivers.

---

## Upload Destination

### Workflow:

1. **Upload to YouTube as Unlisted**
   - Title: `Sibyl Does Research — Live Session, koad:io Entity Work, Apr 7 2026`
   - Upload `2026-04-07-sibyl-research-final.mp4`
   - Set thumbnail to `2026-04-07-sibyl-research-thumb.png`
   - Paste description from `~/.rufus/distribution/2026-04-05-sibyl-session-youtube-desc.md`
   - Share unlisted URL with Mercury for review

2. **Mercury reviews and approves**
   - Mercury checks description, tags, thumbnail, chapter markers
   - Mercury approves via GitHub Issue comment on the production issue

3. **Publish**
   - Switch YouTube visibility from Unlisted to Public
   - Mercury handles social distribution (Twitter/X thread, r/LocalLLaMA post)

4. **Archive**
   - Upload `.cast` file to `~/.rufus/recordings/` (stays local, gitignored)
   - Commit production metadata (not the video files) to `~/.rufus/productions/2026-04-07-sibyl-research/`

---

## asciinema Share (Alternative Distribution)

If YouTube upload is delayed, the cast file can be shared directly:

```bash
# Upload to asciinema.org (public)
asciinema upload ~/.rufus/recordings/2026-04-07-sibyl-research-edit.cast
```

This gives a URL like `https://asciinema.org/a/<hash>` which can be embedded or linked directly.
Use as a stopgap, not a primary distribution channel.

---

## Checklist Before Recording

- [ ] asciinema installed and working (`asciinema --version`)
- [ ] `~/.rufus/recordings/` directory exists
- [ ] Terminal is clean: `clear && printf '\033[3J'`
- [ ] Font size readable at target resolution (18pt+ for 1080p)
- [ ] Dark theme active (black/near-black bg, light monospace text)
- [ ] No notification banners or status bars that would obscure content
- [ ] Idle-time-limit set to 2 seconds in the record command
- [ ] Test run: record 10 seconds, play back, confirm legibility
