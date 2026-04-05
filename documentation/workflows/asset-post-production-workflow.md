---
title: Asset Post-Production Workflow — Editing & Export Presets
owner: rufus
status: active
updated: 2026-04-05
closes-issue: https://github.com/koad/rufus/issues/5
---

# Asset Post-Production Workflow — Editing & Export Presets

This document defines the post-production workflow for all Rufus content: from raw recording to Mercury-ready export. Emphasis on command-line tooling (ffmpeg, agg) to avoid dependency on GUI editors for routine operations. GUI editing (kdenlive, DaVinci Resolve) reserved for narrative-heavy content.

---

## Workflow Overview

```
[Raw recording] → [Rough cut] → [Audio cleanup] → [Color] → [Export] → [Mercury handoff]
```

**Principle:** Most koad:io content is terminal-based screencasts. No color correction needed. No B-roll. The edit job is: trim, pace, and export. Keep it simple.

---

## Step 1: Ingest & Verify

Before editing, verify the raw recording is clean:

```bash
SESSION="2026-04-05-clone-walkthrough"
RAW=~/.rufus/recordings/$SESSION/raw/${SESSION}-raw.mkv

# Probe the file
ffprobe -v quiet -print_format json -show_streams "$RAW" | jq '.streams[] | {codec_type, codec_name, width, height, r_frame_rate, duration}'

# Check duration (human readable)
ffprobe -v quiet -show_entries format=duration -of csv=p=0 "$RAW" | awk '{printf "%02d:%02d:%02d\n", $1/3600, ($1%3600)/60, $1%60}'

# Spot-check: open first 30 seconds
ffplay -t 30 "$RAW"
```

**Acceptance criteria before editing:**
- [ ] Video stream present at expected resolution
- [ ] Audio stream present (if voice-over recorded live)
- [ ] Duration matches expected session length
- [ ] No corruption artifacts in first 30 seconds
- [ ] No corruption artifacts in last 30 seconds (`ffplay -ss <end-30s> -t 30`)

---

## Step 2: Rough Cut (Trim)

Identify trim points from the raw recording, then apply:

```bash
# Trim dead air from start/end — adjust timestamps per recording
# Format: HH:MM:SS or SS.ss

START="00:00:03"    # trim first 3 seconds (setup dead air)
END="00:06:42"      # trim after close (recorder still running)

ffmpeg -i "$RAW" \
  -ss "$START" -to "$END" \
  -c copy \
  ~/.rufus/recordings/$SESSION/raw/${SESSION}-trimmed.mkv
```

**Notes:**
- `-c copy` avoids re-encoding — no quality loss, fast operation
- If trimming causes A/V sync issues (happens with `-c copy` at non-keyframe boundaries), replace `-c copy` with `-c:v libx264 -crf 18 -c:a aac -b:a 320k` for a re-encode

---

## Step 3: Speed Adjustment (Optional)

For inference sections where real-time is too slow for viewers:

```bash
TRIMMED=~/.rufus/recordings/$SESSION/raw/${SESSION}-trimmed.mkv

# Speed up specific section (e.g., inference segment 01:30 → 04:00 at 2x)
# Split, speed, rejoin
ffmpeg -i "$TRIMMED" -ss 00:01:30 -to 00:04:00 -c copy segment-inference.mkv
ffmpeg -i segment-inference.mkv \
  -vf "setpts=0.5*PTS" \
  -af "atempo=2.0" \
  segment-inference-2x.mkv

# Split intro section (keep at 1x)
ffmpeg -i "$TRIMMED" -ss 00:00:00 -to 00:01:30 -c copy segment-intro.mkv

# Split outro section (keep at 1x)
ffmpeg -i "$TRIMMED" -ss 00:04:00 -c copy segment-outro.mkv

# Concatenate
cat > concat-list.txt << 'EOF'
file 'segment-intro.mkv'
file 'segment-inference-2x.mkv'
file 'segment-outro.mkv'
EOF

ffmpeg -f concat -safe 0 -i concat-list.txt -c copy ${SESSION}-assembled.mkv
```

**Speed reference:**
- 1.5x: subtle acceleration — dialogue/walkthrough sections
- 2.0x: visible speed — inference, long waits
- 3.0x: fast-forward feel — reasoning token streams only

---

## Step 4: Audio Cleanup (If Voice-Over Recorded Live)

For recordings with live microphone:

```bash
ASSEMBLED=${SESSION}-assembled.mkv

# Option 1: ffmpeg filters (no external tool required)
ffmpeg -i "$ASSEMBLED" \
  -af "highpass=f=80, lowpass=f=8000, afftdn=nf=-25, acompressor=threshold=-18dB:ratio=4:attack=6:release=60, alimiter=limit=-3dB" \
  -c:v copy \
  ${SESSION}-audio-cleaned.mkv

# Option 2: Extract audio → clean in Audacity → remux
ffmpeg -i "$ASSEMBLED" -vn -c:a pcm_s16le audio-raw.wav
# [open audio-raw.wav in Audacity, apply Noise Reduction + Compressor]
ffmpeg -i "$ASSEMBLED" -i audio-cleaned.wav -c:v copy -c:a aac -b:a 320k -map 0:v:0 -map 1:a:0 ${SESSION}-audio-cleaned.mkv
```

**For terminal-only screencasts (no voice-over):** Skip this step. No audio processing needed.

---

## Step 5: Title Cards & Captions

### Title Cards (ffmpeg drawtext)

For simple section titles without a full editor:

```bash
# Add title card at start (0:00 → 0:03)
ffmpeg -i input.mkv \
  -vf "drawtext=text='Sibyl Does Research — Live Session, Apr 7 2026':fontcolor=white:fontsize=36:x=(w-text_w)/2:y=(h-text_h)/2:enable='between(t,0,3)'" \
  -c:a copy \
  with-title.mkv
```

**Preferred approach:** Add title cards as separate overlaid image sources in OBS before recording, not in post. Avoids re-encoding.

### Auto-Generated Captions

```bash
# Using Whisper (local, no API)
pip install openai-whisper

whisper audio-extract.wav \
  --model medium \
  --language en \
  --output_format srt \
  --output_dir ~/.rufus/recordings/$SESSION/assets/
```

**Manual caption review required after auto-generation:**
- Check entity names (Sibyl, Juno, Mercury, Vulcan — Whisper often mishears)
- Check technical terms (koad:io, asciinema, ollama, NVENC)
- Check timestamps for accuracy at section transitions

---

## Step 6: Thumbnail Production

For terminal-based content, the thumbnail is a screenshot with minimal text overlay.

```bash
# Extract thumbnail frame from recording
THUMB_TIME="00:04:05"   # adjust to best frame
SESSION_DIR=~/.rufus/recordings/$SESSION

ffmpeg -i "$SESSION_DIR/raw/${SESSION}-raw.mkv" \
  -ss "$THUMB_TIME" \
  -vframes 1 \
  "$SESSION_DIR/assets/${SESSION}-thumb-raw.png"

# Resize to YouTube thumbnail spec
ffmpeg -i "$SESSION_DIR/assets/${SESSION}-thumb-raw.png" \
  -vf "scale=1280:720" \
  "$SESSION_DIR/assets/${SESSION}-thumb.png"
```

**Text overlay on thumbnail:** Done in a graphics tool (GIMP, Inkscape, or imagemagick) — not ffmpeg drawtext, which lacks typography control.

**Quick imagemagick overlay (if no GUI available):**
```bash
convert "$SESSION_DIR/assets/${SESSION}-thumb.png" \
  -font "DejaVu-Sans-Bold" \
  -pointsize 64 \
  -fill white \
  -stroke black \
  -strokewidth 2 \
  -annotate +60+680 "No cloud. No account. Just files." \
  "$SESSION_DIR/assets/${SESSION}-thumb-final.png"
```

---

## Export Presets

### Preset: YouTube Final

```bash
# High quality, YouTube-optimized
ffmpeg -i assembled.mkv \
  -c:v libx264 \
  -crf 15 \
  -preset slow \
  -profile:v high \
  -level 4.2 \
  -pix_fmt yuv420p \
  -c:a aac \
  -b:a 320k \
  -movflags +faststart \
  -metadata title="$TITLE" \
  -metadata artist="Rufus / koad:io" \
  -metadata date="$(date +%Y)" \
  final.mp4
```

### Preset: Twitter Clip (60 seconds)

```bash
# Trim to 60s clip, lower resolution
ffmpeg -i assembled.mkv \
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

### Preset: Preview / Review Cut

For internal review before Mercury handoff (small file, fast):

```bash
ffmpeg -i assembled.mkv \
  -c:v libx264 \
  -crf 28 \
  -preset veryfast \
  -vf "scale=1280:720" \
  -c:a aac \
  -b:a 96k \
  -movflags +faststart \
  review-cut.mp4
```

---

## Terminal Capture Post-Production (asciinema)

Special workflow for `.cast` files:

```bash
# Option 1: Publish to asciinema.org (easiest for web embedding)
asciinema upload ~/.rufus/recordings/$SESSION/raw/${SESSION}-raw.cast

# Option 2: Export to animated GIF (for GitHub READMEs, etc.)
agg \
  --cols 80 \
  --rows 24 \
  --fps 30 \
  --speed 1.5 \
  --theme asciinema \
  ~/.rufus/recordings/$SESSION/raw/${SESSION}-raw.cast \
  ~/.rufus/recordings/$SESSION/assets/${SESSION}.gif

# Option 3: GIF → MP4 for social
ffmpeg -i ~/.rufus/recordings/$SESSION/assets/${SESSION}.gif \
  -movflags faststart \
  -pix_fmt yuv420p \
  -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" \
  ~/.rufus/recordings/$SESSION/final/${SESSION}-cast.mp4
```

---

## Mercury Handoff Checklist

Before handing a production to Mercury for distribution:

```
[ ] final.mp4 — YouTube-quality export, correct duration
[ ] clip-twitter.mp4 — 60s clip, 1280x720
[ ] thumb.png — 1280x720 thumbnail
[ ] caption.srt — reviewed and corrected captions
[ ] manifest.json — updated with final checksums and durations
[ ] YouTube title, description, tags — from production script.md
[ ] Twitter caption text — 280 characters, from production script.md
[ ] Reddit post title — from production script.md
[ ] Upload to unlisted YouTube for Mercury review before publishing
```

Delivery directory structure:
```
~/.rufus/recordings/YYYY-MM-DD-<slug>/
├── final/
│   ├── final.mp4
│   └── clip-twitter.mp4
├── assets/
│   ├── thumb.png
│   └── caption.srt
└── manifest.json
```

---

## Status

- [x] Post-production workflow defined (ingest through Mercury handoff)
- [x] ffmpeg export presets (YouTube, Twitter, review)
- [x] Audio cleanup pipeline
- [x] Thumbnail extraction procedure
- [x] asciinema terminal capture post-production
- [x] Mercury handoff checklist
- [ ] Whisper installed on thinker / fourty4 for auto-captioning
- [ ] agg installed for asciinema → gif pipeline
- [ ] First production run through full workflow
