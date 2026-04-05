---
title: "Meet Chiron — koad:io Curriculum Architect"
series: entity-intro
entity: chiron
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Chiron

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

A 2:30–3:00 terminal screencast introducing Chiron: the curriculum architect who designed Alice's 13-level onboarding sequence. The viewer sees the curricula directory structure, reads the first lines of level-00.md, and understands why a sovereign AI entity building pedagogy is both unusual and important.

**Core message:** "Chiron doesn't teach — he designs the paths that Alice walks learners through. Every level was authored by an entity, on disk, in git."

**Who it's for:** Developers curious about how the koad:io team divides labor. Teachers and curriculum designers who didn't expect to see their domain in an AI entity ecosystem. Show HN readers asking "wait, what does each entity actually do?"

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

**Segment 4 demo for Chiron:**

```bash
# Step 1 — show curricula exist
ls ~/.chiron/curricula/alice-onboarding/levels/

# Expected output: level-00.md through level-12.md (13 files)

# Step 2 — read the primer
cat ~/.chiron/curricula/alice-onboarding/levels/level-00.md | head -30
```

**Why this demo:**
- Immediately legible to any technical viewer
- Proves a real artifact exists, not just a README claim
- The 13 levels in one `ls` output is a compelling visual unit
- `head -30` of level-00.md shows YAML frontmatter + stated learning objective — exactly what a curriculum architect produces

---

## Key Decisions

**Why show the curricula directory rather than invoke Chiron live?**
Chiron's output IS the curricula. Showing the files proves the entity has done real work. A live invocation would run long and risk model variability — the files are the demo.

**Why level-00.md specifically?**
Level 0 is the zero-threshold entry point — "one file, no setup." Its design philosophy is immediately legible and sets up why the 13-level structure exists. It's the best introduction to Chiron's thinking.

---

## Pre-Recording Checklist

- [ ] `cd ~/.chiron && git pull`
- [ ] Confirm `ls ~/.chiron/curricula/alice-onboarding/levels/` shows 13 files (level-00 through level-12)
- [ ] `cat ~/.chiron/curricula/alice-onboarding/levels/level-00.md | head -30` produces expected output
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-chiron/raw/`
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

**Title:** `Meet Chiron — koad:io Curriculum Architect`

**Description:**
```
Chiron is the curriculum architect for the koad:io ecosystem — the entity that
designed Alice's 13-level onboarding sequence. In this video: who Chiron is,
what a curriculum entity actually produces, and a live look at the files on disk.

Clone Chiron: git clone https://github.com/koad/chiron

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, sovereign AI, curriculum design, Alice, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing `ls ~/.chiron/curricula/alice-onboarding/levels/` output — 13 level files clearly visible. Text overlay: `chiron` / `curriculum architect`.
