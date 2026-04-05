---
title: "Meet Aegis — koad:io Private Counsel"
series: entity-intro
entity: aegis
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Aegis

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

A 2:30–3:00 terminal screencast introducing Aegis: Juno's private counsel, daily assessor, and the only entity authorized to question Juno directly. The viewer sees the assessments directory with four dated files, then reads Aegis's CLAUDE.md role description. The argument: Aegis is the only entity that checks Juno. Every orchestrator needs a check.

**Core message:** "Aegis is the only entity koad has authorized to question Juno directly. That is a designed structural check on the orchestrator."

**Who it's for:** Anyone thinking seriously about AI governance. Engineers who want to understand how autonomous agent systems prevent the orchestrator from going unchecked.

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

**Segment 4 demo for Aegis:**

```bash
# Step 1 — show the assessments directory
ls ~/.aegis/assessments/

# Expected output (verified 2026-04-05):
# 2026-04-02-first-assessment.md
# 2026-04-03-day4-assessment.md
# 2026-04-04-day5-assessment.md
# 2026-04-05-day6-assessment.md

# Step 2 — show Aegis's CLAUDE.md role description
head -35 ~/.aegis/CLAUDE.md
```

**Why this demo:**
- The assessments directory shows four consecutive daily assessments: April 2, 3, 4, 5 — from first gestation to Day 6
- CLAUDE.md shows the structural design: "I am the only entity koad has authorized to question Juno directly. That is not personal authority — it is a designed structural check on the orchestrator."
- The combination proves Aegis is not a concept — he has been checking Juno every day since gestation

---

## Key Decisions

**Why show assessments rather than git log?**
The assessments are the deliverable. Four files, four days, named by date — this is a living record of Aegis checking Juno. The git log shows commits; the assessments directory shows the specific purpose. For this entity, the purpose is the proof.

**Why CLAUDE.md?**
The governance design is in CLAUDE.md — specifically the statement that Aegis's authority is structural, not personal, and that it runs "both ways." This is the argument the viewer needs to understand what makes Aegis different from every other entity.

---

## Pre-Recording Checklist

- [ ] `cd ~/.aegis && git pull`
- [ ] Confirm `ls ~/.aegis/assessments/` shows 4 dated assessment files
- [ ] Confirm `head -35 ~/.aegis/CLAUDE.md` shows the structural check design
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-aegis/raw/`
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

**Title:** `Meet Aegis — koad:io Private Counsel`

**Description:**
```
Aegis is Juno's private counsel and daily assessor — the only entity koad
has authorized to question Juno directly. He is a designed structural check
on the orchestrator. In this video: who Aegis is, four days of consecutive
daily assessments, and why every orchestrator needs a check.

Clone Aegis: git clone https://github.com/koad/aegis

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, AI governance, sovereign AI, trust bonds, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing `ls ~/.aegis/assessments/` with four dated files visible. Text overlay: `aegis` / `private counsel` / `the only entity that checks juno`.
