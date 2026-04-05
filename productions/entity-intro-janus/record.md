---
title: "Meet Janus — koad:io Stream Watcher"
series: entity-intro
entity: janus
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Janus

**Status:** Pre-production complete. Ready to record.

---

## Files in This Production

| File | Purpose | Status |
|------|---------|--------|
| `record.md` (this file) | Production summary and checklists | Complete |
| `script.md` | Full narration script, segment-by-segment | Complete |
| `shot-list.md` | Shot list, pre-flight checklist, editing notes | Complete |

---

## What This Video Is

A 2:30–3:00 terminal screencast introducing Janus: the stream watcher who monitors GitHub atom feeds across all 12 entity repos, looking for stalled entities, role drift, pipeline breaks, and trust chain gaps. The viewer reads the first 30 lines of CLAUDE.md — which precisely defines what Janus watches and what it doesn't — then sees a real watch log showing the observation format.

**Core message:** "Janus doesn't fix anything. It alerts. It's the filter between the stream and the team — watching what no individual entity can see."

**Who it's for:** Developers who wonder who watches the watchers in an autonomous agent team. Security researchers interested in how AI systems detect anomalies in other AI systems.

---

## Production Summary

| Field | Value |
|-------|-------|
| Recording hardware | thinker (primary) |
| Capture method | asciinema + ffmpeg export, or OBS screen capture |
| Voice-over | Live during recording |
| Resolution | 1920x1080 minimum |
| Font | JetBrains Mono or Fira Code, 16–18px |
| Terminal theme | Black background, white text, no decorations |
| Shell prompt | `$ ` only |

---

## Demo Specification

**Segment 4 demo for Janus:**

```bash
# Step 1 — show the CLAUDE.md role definition (the "what I watch" section)
head -30 ~/.janus/CLAUDE.md

# Step 2 — show the watch logs directory
ls ~/.janus/watches/

# Step 3 — read the opening of a watch log
head -20 ~/.janus/watches/2026-04-02-afternoon-stream.md
```

**Why this demo:**
- `head -30 CLAUDE.md` shows the exact surveillance scope — named repos, signal types, intervention protocol — in the most compact possible proof
- `ls watches/` shows that Janus has been running: real watch logs with dates, two streams per day
- `head -20` of a watch log shows the observation format: date range, watcher, status, commit volume across named entities
- Together they prove this is an operational monitoring entity, not a concept

---

## Key Decisions

**Why show CLAUDE.md rather than invoke Janus live?**
Janus's value is its surveillance definition — what it watches, how it decides to file, when it doesn't. CLAUDE.md contains the complete signal specification. A live invocation would be a new feed scan; the existing watch logs prove the surveillance has been running.

**Why 2026-04-02-afternoon-stream.md specifically?**
It's the most complete watch log — shows commit volume across five entities, structured observation format, clear date range. It demonstrates Janus's observation discipline without requiring context about any specific event.

---

## Pre-Recording Checklist

- [ ] `cd ~/.janus && git pull`
- [ ] Confirm `head -30 ~/.janus/CLAUDE.md` shows "What I Watch" section with named repos
- [ ] Confirm `ls ~/.janus/watches/` shows at least two watch log files
- [ ] `head -20 ~/.janus/watches/2026-04-02-afternoon-stream.md` produces expected output
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-janus/raw/`
- [ ] Trim dead air start/end
- [ ] Export to `final.mp4` (YouTube preset, 1080p)
- [ ] Export `clip-twitter.mp4` (60s, 1280x720)
- [ ] Extract or produce opening card frame (`card-open.png`)
- [ ] Extract or produce closing card frame (`card-close.png`)
- [ ] Run Whisper auto-captions, review and correct
- [ ] Hand off to Mercury with title/description/tags from `script.md`
- [ ] Update this record: status → published, add YouTube URL

---

## YouTube Metadata

**Title:** `Meet Janus — koad:io Stream Watcher`

**Description:**
```
Janus is the stream watcher for the koad:io ecosystem — the entity that monitors
GitHub atom feeds across all 12 entity repos, watching for stalled entities,
role drift, and pipeline breaks. Named for the Roman god who looks both
directions simultaneously. In this video: what Janus watches, how it alerts,
and a live look at the watch logs on disk.

Clone Janus: git clone https://github.com/koad/janus

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, sovereign AI, monitoring, anomaly detection, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing `head -30 ~/.janus/CLAUDE.md` — the "What I Watch" list with named repos clearly visible. Text overlay: `janus` / `stream watcher`.
