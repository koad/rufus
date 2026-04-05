---
title: "Meet Argus — koad:io Diagnostics"
series: entity-intro
entity: argus
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Argus

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

A 2:30–3:00 terminal screencast introducing Argus: diagnostics entity and gate between Mercury's content pipeline and OpenClaw. The viewer sees Argus's recent commits proving active operation, then reads his CLAUDE.md role description. The argument: every system needs someone watching it.

**Core message:** "Argus sees everything and misses nothing. Nothing reaches a platform without his verdict."

**Who it's for:** Engineers who want to understand how quality and integrity are maintained in an autonomous agent system. Anyone asking "what stops the agents from publishing garbage?"

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

**Segment 4 demo for Argus:**

```bash
# Step 1 — show Argus's recent commits
git -C ~/.argus log --author="Argus" --oneline -5

# Expected output (verified 2026-04-05):
# 93cb65d docs: add PRIMER.md — session orientation for arriving agents
# 66600c7 hooks: inject $CWD/PRIMER.md into prompt when present
# 61b1caa readme: lead with architecture, remove quote opener
# bc1cdab hooks: add PID lock — prevent concurrent task invocations
# 8479a06 hooks: remove -c from non-interactive path — tasks run fresh, not resuming stale sessions

# Step 2 — show Argus's CLAUDE.md role description
head -30 ~/.argus/CLAUDE.md
```

**Why this demo:**
- The git log proves Argus has been operational: hook architecture, PID locking, PRIMER injection — these are real commits by an active entity
- `head -30` of CLAUDE.md shows his self-description: "hundred-eyed giant who sees everything and misses nothing" plus the Mercury gate protocol
- The combination of active commits + clear role description makes the argument: Argus is not a concept, he is running

---

## Key Decisions

**Why show CLAUDE.md rather than a diagnostic report?**
CLAUDE.md is Argus's self-knowledge — it explains what he is, what he checks, and why nothing reaches a platform without his verdict. A diagnostic report shows a single run. CLAUDE.md shows the permanent role. The Mercury gate protocol section makes the content pipeline argument directly.

**Why the recent commits specifically?**
The hook architecture commits (PID lock, fresh sessions, PRIMER injection) are exactly the kind of infrastructure work Argus owns. They prove he is not just watching — he is building the watching infrastructure.

---

## Pre-Recording Checklist

- [ ] `cd ~/.argus && git pull`
- [ ] Confirm `git log --author="Argus" --oneline -5` returns 5 results
- [ ] Confirm `head -30 ~/.argus/CLAUDE.md` shows role description and Mercury gate protocol
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-argus/raw/`
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

**Title:** `Meet Argus — koad:io Diagnostics`

**Description:**
```
Argus is the diagnostics entity for the koad:io ecosystem — named for the
hundred-eyed giant of mythology. He examines every entity against the koad:io
protocol, gates the content pipeline, and reports exactly what's wrong.
In this video: who Argus is, what he watches, and live proof from his git log.

Clone Argus: git clone https://github.com/koad/argus

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, diagnostics, monitoring, sovereign AI, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing Argus git log commits — hook architecture visible. Text overlay: `argus` / `diagnostics` / `sees everything`.
