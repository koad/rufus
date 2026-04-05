---
title: "Meet Livy — koad:io Documentation Lead"
series: entity-intro
entity: livy
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Livy

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

A 2:30–3:00 terminal screencast introducing Livy: the historian and documentation keeper. The viewer sees the reference library Livy has built — nine structured documents covering every layer of the koad:io architecture — then gets a word count that shows volume. The argument closes quietly: the documentation is the deliverable.

**Core message:** "Livy doesn't describe the system. Livy IS the system's permanent record."

**Who it's for:** Developers evaluating koad:io who want to know how it works before committing. Anyone who has tried to understand a complex open-source project from a sparse README.

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

**Segment 4 demo for Livy:**

```bash
# Step 1 — show the reference library
ls ~/.livy/docs/reference/

# Expected output (verified 2026-04-05):
# daemon-architecture.md
# entity-directory-structure-claude-section.md
# entity-directory-structure.md
# framework-layer.md
# gestation-process.md
# operations-architecture.md
# packages-structure.md
# README.md
# trust-bond-system.md

# Step 2 — show the volume
wc -l ~/.livy/docs/reference/*.md

# Expected output (verified 2026-04-05):
#    259 daemon-architecture.md
#     61 entity-directory-structure-claude-section.md
#    424 entity-directory-structure.md
#    343 framework-layer.md
#    496 gestation-process.md
#    422 operations-architecture.md
#    229 packages-structure.md
#     18 README.md
#    651 trust-bond-system.md
#   2903 total
```

**Why this demo:**
- The `ls` of `docs/reference/` shows nine files covering every major system layer: daemon, entities, framework, gestation, operations, packages, trust bonds
- The `wc -l` total of 2,903 lines proves volume — this is not stub documentation
- The combination of breadth (nine topics) and depth (2,903 lines) is the argument: someone did the work to document a complex system completely

---

## Key Decisions

**Why wc -l rather than cat a document?**
Volume is the proof, not any single line. 2,903 lines across nine files is the argument. `wc -l` makes that argument in one command, with per-file breakdown visible.

**Why docs/reference/ specifically?**
Reference documentation is the most durable artifact. Posts age. Specs iterate. Reference docs are the stable layer that survives all of it. This is what Livy's value proposition rests on.

---

## Pre-Recording Checklist

- [ ] `cd ~/.livy && git pull`
- [ ] Confirm `ls ~/.livy/docs/reference/` returns 9 files
- [ ] Confirm `wc -l ~/.livy/docs/reference/*.md` shows ~2903 total
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-livy/raw/`
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

**Title:** `Meet Livy — koad:io Documentation Lead`

**Description:**
```
Livy is the documentation lead for the koad:io ecosystem — named for Titus
Livius, Rome's master historian. Livy documents everything users need to know:
daemon architecture, entity structure, gestation process, trust bonds, and more.
In this video: who Livy is, the reference library she's built, and why
documentation is the deliverable.

Clone Livy: git clone https://github.com/koad/livy

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, documentation, sovereign AI, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing `wc -l` output with 2903 total visible. Text overlay: `livy` / `documentation lead` / `2903 lines`.
