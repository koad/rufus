---
title: "Meet Mercury — koad:io Publisher / Distributor"
series: entity-intro
entity: mercury
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Mercury

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

A 2:30–3:00 terminal screencast introducing Mercury: the publisher and distributor who stands at the end of the koad:io content pipeline. The viewer sees the posting schedule, the distribution queue, and the ops structure that enforces how content moves from the team to the world.

**Core message:** "Mercury doesn't just post. Mercury enforces a discipline — schedule, Veritas check, Argus gate, then publish. Every post goes through the same path."

**Who it's for:** Content creators and developers who want to see how an autonomous team manages external communications without a social media manager. Show HN readers asking "who actually posts this stuff?"

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

**Segment 4 demo for Mercury:**

```bash
# Step 1 — show the posting schedule structure
cat ~/.mercury/SCHEDULE.md | head -30

# Step 2 — show the distribution queue
cat ~/.mercury/QUEUE-2026-04-03.md | head -20

# Step 3 — show ops directory
ls ~/.mercury/ops/
```

**Why this demo:**
- SCHEDULE.md shows the discipline: posting windows, platform gaps, quiet hours — real operational constraints, not vibes
- The queue shows an actual pipeline in motion: drafts awaiting Veritas check, Argus gate, publish window
- `ls ops/` reveals the full infrastructure: incident log, platform publisher spec, Veritas SLA
- Together they prove Mercury is an operations layer, not just a "post things" entity

---

## Key Decisions

**Why show the schedule and queue rather than invoke Mercury live?**
Mercury is currently blocked on platform credentials — a live publish would fail. The schedule and queue demonstrate the operational discipline and pipeline structure that Mercury enforces, which is the real story. The files prove the system exists.

**Why QUEUE-2026-04-03.md specifically?**
It's the most complete queued work artifact — shows all three stages (Veritas check, Argus gate, publish window) in action. It documents real posts with real claims, making the verification workflow tangible.

---

## Pre-Recording Checklist

- [ ] `cd ~/.mercury && git pull`
- [ ] Confirm `cat ~/.mercury/SCHEDULE.md | head -30` produces posting constraints output
- [ ] Confirm `cat ~/.mercury/QUEUE-2026-04-03.md | head -20` shows draft + pipeline structure
- [ ] Confirm `ls ~/.mercury/ops/` shows expected files
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-mercury/raw/`
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

**Title:** `Meet Mercury — koad:io Publisher / Distributor`

**Description:**
```
Mercury is the publisher and distributor for the koad:io ecosystem — the entity
that stands at the end of the creation pipeline and manages how content reaches
the world. In this video: who Mercury is, how the posting schedule works, and
a live look at the distribution queue.

Clone Mercury: git clone https://github.com/koad/mercury

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, sovereign AI, content distribution, social media automation, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing `cat ~/.mercury/SCHEDULE.md` — posting constraints and cadence clearly visible. Text overlay: `mercury` / `publisher / distributor`.
