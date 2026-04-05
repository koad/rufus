---
title: Recording Workflow Automation — Scripts & Asset Naming
owner: rufus
status: active
updated: 2026-04-05
closes-issue: https://github.com/koad/rufus/issues/3
---

# Recording Workflow Automation — Scripts & Asset Naming

This document specifies the automation scripts and asset naming conventions for all Rufus recording sessions. The goal: every session produces consistently named, organized, checksummed files with zero manual bookkeeping.

---

## Asset Naming Convention

### Pattern

```
YYYY-MM-DD-<slug>-<type>[-<take>].<ext>
```

| Field | Format | Examples |
|-------|--------|---------|
| Date | ISO 8601, dash-separated | `2026-04-05` |
| Slug | Lowercase, dash-separated, descriptive | `sibyl-research`, `clone-walkthrough`, `trust-bonds` |
| Type | `raw`, `final`, `clip`, `thumb`, `caption`, `script` | `raw`, `final` |
| Take | Optional, only for retakes | `-t2`, `-t3` |
| Ext | Standard file extension | `.mkv`, `.mp4`, `.cast`, `.png`, `.md` |

### Examples

```
2026-04-05-clone-walkthrough-raw.mkv         # raw recording, first take
2026-04-05-clone-walkthrough-raw-t2.mkv      # raw recording, second take
2026-04-05-clone-walkthrough-final.mp4       # edited export
2026-04-05-clone-walkthrough-clip-twitter.mp4  # 60s clip for Twitter
2026-04-05-clone-walkthrough-thumb.png       # thumbnail
2026-04-05-clone-walkthrough-caption.srt     # captions
2026-04-07-sibyl-research-raw.mkv
2026-04-07-sibyl-research-raw.cast           # asciinema terminal capture
2026-04-07-sibyl-research-final.mp4
```

---

## Directory Structure

```
~/.rufus/recordings/
├── YYYY-MM-DD-<slug>/           # one directory per production
│   ├── raw/                     # unedited source files
│   │   ├── YYYY-MM-DD-<slug>-raw.mkv
│   │   └── YYYY-MM-DD-<slug>-raw.cast  (if terminal capture)
│   ├── final/                   # export-ready files
│   │   ├── YYYY-MM-DD-<slug>-final.mp4
│   │   └── YYYY-MM-DD-<slug>-clip-twitter.mp4
│   ├── assets/                  # thumbnail, captions, etc.
│   │   ├── YYYY-MM-DD-<slug>-thumb.png
│   │   └── YYYY-MM-DD-<slug>-caption.srt
│   └── manifest.json            # recording metadata
```

### Create session directory

```bash
SESSION="2026-04-05-clone-walkthrough"
mkdir -p ~/.rufus/recordings/$SESSION/{raw,final,assets}
echo "Session directory created: ~/.rufus/recordings/$SESSION"
```

---

## Manifest Format

Every session produces a `manifest.json` capturing metadata:

```json
{
  "id": "2026-04-05-clone-walkthrough",
  "title": "I Cloned a koad:io Entity",
  "date": "2026-04-05",
  "slug": "clone-walkthrough",
  "hardware": "thinker",
  "capture_method": "asciinema",
  "raw_file": "raw/2026-04-05-clone-walkthrough-raw.cast",
  "final_file": "final/2026-04-05-clone-walkthrough-final.mp4",
  "duration_raw_seconds": 410,
  "duration_final_seconds": 380,
  "takes": 1,
  "content_pillar": "Reality",
  "entities_featured": ["sibyl"],
  "distribution_status": {
    "youtube": "pending",
    "twitter": "pending",
    "reddit": "pending"
  },
  "mercury_handoff": false,
  "checksums": {
    "raw": "sha256:abc123...",
    "final": "sha256:def456..."
  },
  "created_at": "2026-04-05T14:30:00Z",
  "notes": ""
}
```

### Generate manifest

```bash
#!/usr/bin/env bash
# init-manifest.sh — initialize recording manifest
SESSION=$1
TITLE=$2
DATE=$(date +%Y-%m-%d)

cat > ~/.rufus/recordings/$SESSION/manifest.json << EOF
{
  "id": "$SESSION",
  "title": "$TITLE",
  "date": "$DATE",
  "slug": "${SESSION#${DATE}-}",
  "hardware": "$(hostname)",
  "capture_method": "",
  "raw_file": "",
  "final_file": "",
  "duration_raw_seconds": 0,
  "duration_final_seconds": 0,
  "takes": 0,
  "content_pillar": "",
  "entities_featured": [],
  "distribution_status": {
    "youtube": "pending",
    "twitter": "pending",
    "reddit": "pending"
  },
  "mercury_handoff": false,
  "checksums": {},
  "created_at": "$(date -u +%Y-%m-%dT%H:%M:%SZ)",
  "notes": ""
}
EOF
echo "Manifest created: ~/.rufus/recordings/$SESSION/manifest.json"
```

---

## Recording Scripts

### 1. asciinema Terminal Capture

**Use case:** Entity session demos on thinker or fourty4 (no OBS required).

```bash
#!/usr/bin/env bash
# record-terminal.sh — start asciinema terminal capture
# Usage: ./record-terminal.sh <session-slug> [title]

SESSION_SLUG="$1"
TITLE="${2:-$(echo $SESSION_SLUG | tr '-' ' ')}"
DATE=$(date +%Y-%m-%d)
SESSION="${DATE}-${SESSION_SLUG}"
OUTPUT_DIR=~/.rufus/recordings/${SESSION}/raw
OUTPUT_FILE="${OUTPUT_DIR}/${SESSION}-raw.cast"

mkdir -p "$OUTPUT_DIR"

echo "=== Rufus Terminal Capture ==="
echo "Session: $SESSION"
echo "Title: $TITLE"
echo "Output: $OUTPUT_FILE"
echo ""
echo "Pre-flight checklist:"
echo "  [ ] Terminal: black background, white text, 16px+ monospace"
echo "  [ ] Clear scrollback: clear && printf '\\033[3J'"
echo "  [ ] Quiet room, mic positioned"
echo ""
read -p "Press ENTER to start recording..."

asciinema rec \
  --title "$TITLE" \
  --idle-time-limit 2 \
  --env TERM,SHELL \
  "$OUTPUT_FILE"

echo ""
echo "Recording saved: $OUTPUT_FILE"
echo "Cast file size: $(du -sh "$OUTPUT_FILE" | cut -f1)"
```

### 2. ffmpeg Screen Capture (No OBS)

**Use case:** Quick screen recording without OBS overhead.

```bash
#!/usr/bin/env bash
# record-screen.sh — ffmpeg screen capture
# Usage: ./record-screen.sh <session-slug>

SESSION_SLUG="$1"
DATE=$(date +%Y-%m-%d)
SESSION="${DATE}-${SESSION_SLUG}"
OUTPUT_DIR=~/.rufus/recordings/${SESSION}/raw
OUTPUT_FILE="${OUTPUT_DIR}/${SESSION}-raw.mkv"

mkdir -p "$OUTPUT_DIR"

# Detect display
DISPLAY="${DISPLAY:-:0}"

echo "Recording to: $OUTPUT_FILE"
echo "Press Ctrl+C to stop recording."
echo ""

ffmpeg \
  -f x11grab \
  -r 60 \
  -s 1920x1080 \
  -i "${DISPLAY}+0,0" \
  -f alsa \
  -i default \
  -c:v libx264 \
  -preset veryfast \
  -crf 18 \
  -c:a aac \
  -b:a 192k \
  -pix_fmt yuv420p \
  "$OUTPUT_FILE"

echo ""
echo "Recording saved: $OUTPUT_FILE"
echo "File size: $(du -sh "$OUTPUT_FILE" | cut -f1)"
```

### 3. OBS Remote Start/Stop

**Use case:** Trigger OBS recording on flowbie from thinker.

```bash
#!/usr/bin/env bash
# obs-record.sh — remote OBS control via WebSocket
# Usage: ./obs-record.sh start|stop <host>

ACTION="$1"   # start or stop
HOST="${2:-flowbie}"
OBS_PORT=4455
OBS_PASSWORD=$(cat ~/.rufus/.credentials | grep "OBS_${HOST^^}_PASSWORD" | cut -d= -f2)

if [[ -z "$OBS_PASSWORD" ]]; then
  echo "Error: OBS_${HOST^^}_PASSWORD not found in ~/.rufus/.credentials"
  exit 1
fi

case "$ACTION" in
  start)
    obs-cmd --websocket "obsws://${HOST}:${OBS_PORT}/${OBS_PASSWORD}" recording start
    echo "Recording started on $HOST at $(date)"
    ;;
  stop)
    obs-cmd --websocket "obsws://${HOST}:${OBS_PORT}/${OBS_PASSWORD}" recording stop
    echo "Recording stopped on $HOST at $(date)"
    ;;
  status)
    obs-cmd --websocket "obsws://${HOST}:${OBS_PORT}/${OBS_PASSWORD}" recording status
    ;;
  *)
    echo "Usage: $0 start|stop|status [host]"
    exit 1
    ;;
esac
```

### 4. Post-Session: Checksum & Archive

Run after every recording session to generate checksums and update the manifest.

```bash
#!/usr/bin/env bash
# post-session.sh — finalize recording session
# Usage: ./post-session.sh <session-id>

SESSION="$1"
SESSION_DIR=~/.rufus/recordings/$SESSION

if [[ ! -d "$SESSION_DIR" ]]; then
  echo "Error: Session directory not found: $SESSION_DIR"
  exit 1
fi

echo "=== Post-Session Finalization: $SESSION ==="

# Checksum all files
echo "Computing checksums..."
for f in "$SESSION_DIR"/raw/* "$SESSION_DIR"/final/* "$SESSION_DIR"/assets/*; do
  [[ -f "$f" ]] || continue
  sha256=$(sha256sum "$f" | cut -d' ' -f1)
  echo "  $(basename $f): sha256:$sha256"
done

# Duration of raw recording (if cast file)
CAST_FILE=$(ls "$SESSION_DIR"/raw/*.cast 2>/dev/null | head -1)
if [[ -n "$CAST_FILE" ]]; then
  # asciinema cast duration from last timestamp
  DURATION=$(python3 -c "
import json
with open('$CAST_FILE') as f:
    lines = f.readlines()
last = json.loads(lines[-1])
print(int(last[0]))
" 2>/dev/null || echo "unknown")
  echo "Raw duration: ${DURATION}s"
fi

echo ""
echo "Update manifest.json with checksums and duration."
echo "Session directory: $SESSION_DIR"
echo "Finalization complete."
```

### 5. Retrieve Remote Recordings

```bash
#!/usr/bin/env bash
# retrieve-recordings.sh — pull recordings from remote machines
# Usage: ./retrieve-recordings.sh <host> [date]

HOST="$1"
DATE="${2:-$(date +%Y-%m-%d)}"
LOCAL_DIR=~/.rufus/recordings/raw/${HOST}

mkdir -p "$LOCAL_DIR"

case "$HOST" in
  flowbie)
    REMOTE_PATH="~/recordings/"
    ;;
  fourty4)
    REMOTE_PATH="~/rufus-recordings/"
    ;;
  *)
    echo "Unknown host: $HOST"
    exit 1
    ;;
esac

echo "Retrieving recordings from $HOST ($REMOTE_PATH) → $LOCAL_DIR"
rsync -avz --progress "${HOST}:${REMOTE_PATH}" "$LOCAL_DIR/"
echo "Done. Files in: $LOCAL_DIR"
```

---

## Script Installation

All scripts live in `~/.rufus/scripts/` and are symlinked into `~/.rufus/bin/`:

```bash
mkdir -p ~/.rufus/scripts ~/.rufus/bin
# After writing scripts:
chmod +x ~/.rufus/scripts/*.sh
for script in ~/.rufus/scripts/*.sh; do
  base=$(basename "$script" .sh)
  ln -sf "$script" ~/.rufus/bin/"$base"
done
```

---

## Workflow Integration

The commands in `~/.rufus/commands/record/` call these scripts. The full recording lifecycle:

```
rufus record start <type>
    ↓
  init-manifest.sh (create session dir + manifest)
    ↓
  record-terminal.sh OR obs-record.sh start
    ↓
  [recording in progress]
    ↓
rufus record stop
    ↓
  obs-record.sh stop OR asciinema ends
    ↓
  post-session.sh (checksums, duration)
    ↓
  [ready for editing → Mercury handoff]
```

---

## Status

- [x] Asset naming convention defined
- [x] Directory structure specified
- [x] Manifest format defined
- [x] asciinema capture script
- [x] ffmpeg screen capture script
- [x] OBS remote control script
- [x] Post-session finalization script
- [x] Remote retrieval script
- [ ] Scripts written to `~/.rufus/scripts/` and made executable
- [ ] Integration with `rufus record` command tested end-to-end
