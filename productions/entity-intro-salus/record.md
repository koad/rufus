---
title: "Meet Salus — koad:io Entity Health"
series: entity-intro
entity: salus
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Salus

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

A 2:30–3:00 terminal screencast introducing Salus: the entity responsible for healing the koad:io ecosystem when entities drift. The viewer sees Salus's CLAUDE.md self-description, then her heal reports directory showing daily operations. The argument: when entities drift, Salus corrects them.

**Core message:** "Salus runs daily heal on all entities. When the system drifts, she brings it back."

**Who it's for:** Engineers who want to understand how an autonomous multi-agent system maintains integrity over time. Anyone asking "what happens when an entity breaks or goes stale?"

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

**Segment 4 demo for Salus:**

```bash
# Step 1 — show Salus's CLAUDE.md (role description and healing protocol)
head -35 ~/.salus/CLAUDE.md

# Key content (verified 2026-04-05):
# "I am Salus — healer of the koad:io ecosystem."
# "I work from two sources of truth: Argus's diagnosis tells me what's broken;
#  Vesta's protocol tells me what healthy looks like."
# Daily healing protocol, healthy entity checklist

# Step 2 — show heal reports committed
ls ~/.salus/reports/

# Expected output (verified 2026-04-05):
# 2026-04-02-heal-team.md
# 2026-04-03-cascade-environment-verification.md
# 2026-04-03-github-connectivity.md
# 2026-04-03.md
# 2026-04-03-re-audit-vesta-spec-008.md
# 2026-04-03-vesta-patch-audit.md
# 2026-04-04.md
# post-vesta-specs-20260403.md
# vulcan-20260403.md
```

**Why this demo:**
- CLAUDE.md shows Salus's self-knowledge: named for the Roman goddess of safety, works from Argus's diagnosis and Vesta's protocol as sources of truth
- The heal reports directory shows continuous operation — dated reports from April 2, 3, and 4 prove daily cadence
- The combination of role description + evidence of daily operation makes the argument: Salus is not a concept, she is running

---

## Key Decisions

**Why CLAUDE.md rather than git log?**
Salus's CLAUDE.md contains the healing protocol with the healthy entity checklist — that table is the most powerful proof of what Salus does. The git log alone would show commits without context. CLAUDE.md + reports together show the full picture.

**Why the reports directory?**
Dated heal reports prove cadence. The reports from April 2–4 show three consecutive days of operation. The volume (9 files including specialized audits) shows Salus is not just running a simple check — she handles cascade verification, GitHub connectivity, Vesta spec audits, and more.

---

## Pre-Recording Checklist

- [ ] `cd ~/.salus && git pull`
- [ ] Confirm `head -35 ~/.salus/CLAUDE.md` shows role description and healing protocol
- [ ] Confirm `ls ~/.salus/reports/` shows dated heal report files
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-salus/raw/`
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

**Title:** `Meet Salus — koad:io Entity Health`

**Description:**
```
Salus is the healer of the koad:io ecosystem — named for the Roman goddess
of safety and wellbeing. She runs daily health checks on all 12 entities,
fixes what she can directly, and escalates what she can't to Juno. In this
video: who Salus is, how the healing protocol works, and her heal reports
proving daily operation.

Clone Salus: git clone https://github.com/koad/salus

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, health monitoring, entity healing, sovereign AI, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing `ls ~/.salus/reports/` with dated heal reports visible. Text overlay: `salus` / `entity health` / `daily healing protocol`.
