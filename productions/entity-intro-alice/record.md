---
title: "Meet Alice — koad:io Learning System"
series: entity-intro
entity: alice
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Alice

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

A 2:30–3:00 terminal screencast introducing Alice: koad:io's learning system and ambassador to the world. The viewer sees Alice's directory structure, then sees that Chiron's alice-onboarding curriculum begins at Level 0 — a curriculum that exists and is live. The argument: Alice is not a chatbot interface. She delivers Chiron's curriculum to humans.

**Core message:** "Alice delivers Chiron's curriculum to humans. Thirteen levels. Level 0 is live."

**Who it's for:** Anyone curious about how the koad:io system teaches itself to new users. Educators, developers building onboarding flows, anyone who has asked "how do users actually get started?"

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

**Segment 4 demo for Alice:**

```bash
# Step 1 — show Alice's directory structure
ls ~/.alice/

# Expected output (verified 2026-04-05):
# avatar.png  certificates  CLAUDE.md  commands  curriculum
# id  memories  opencode  passenger.json  PRIMER.md  README.md  reviews

# Step 2 — show Chiron's curriculum for Alice exists and begins at Level 0
ls ~/.chiron/curricula/alice-onboarding/levels/

# Expected output (verified 2026-04-05):
# level-00.md  level-01.md  level-02.md  level-03.md  level-04.md
# level-05.md  level-06.md  level-07.md  level-08.md  level-09.md
# level-10.md  level-11.md  level-12.md

# Step 3 — show Level 0 exists and is real content
head -10 ~/.chiron/curricula/alice-onboarding/levels/level-00.md
```

**Why this demo:**
- Alice's directory structure shows `curriculum/` as a first-class directory — she is built to deliver learning
- The 13 levels in Chiron's alice-onboarding prove the curriculum is complete, not a stub
- `head -10` of level-00 shows it is real authored content with front matter — not a placeholder
- The two-entity relationship (Alice delivers what Chiron designs) is shown, not just described

---

## Key Decisions

**Why show Chiron's directory rather than just Alice's?**
Alice delivers Chiron's curriculum — they are a pair. Showing both proves the separation of concerns: Chiron designs the learning, Alice delivers it. This is the architectural insight that makes the demo more than a simple directory listing.

**Why Level 0 specifically?**
Level 0 is the entry point. Its existence proves the system can receive a new human. The series starts at zero and goes to twelve — that structure is visible in the `ls` output.

---

## Pre-Recording Checklist

- [ ] `cd ~/.alice && git pull`
- [ ] `cd ~/.chiron && git pull`
- [ ] Confirm `ls ~/.alice/` shows expected structure including `curriculum/`
- [ ] Confirm `ls ~/.chiron/curricula/alice-onboarding/levels/` shows level-00.md through level-12.md
- [ ] Confirm `head -10 ~/.chiron/curricula/alice-onboarding/levels/level-00.md` shows real front matter
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-alice/raw/`
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

**Title:** `Meet Alice — koad:io Learning System`

**Description:**
```
Alice is koad:io's learning system and ambassador to the world. She delivers
Chiron's curriculum to humans — thirteen levels, from first contact to full
sovereignty. In this video: who Alice is, how she connects to Chiron, and
proof that Level 0 is live.

Clone Alice: git clone https://github.com/koad/alice

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, onboarding, learning system, sovereign AI, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing 13 level files in Chiron's alice-onboarding directory. Text overlay: `alice` / `learning system` / `level 0 is live`.
