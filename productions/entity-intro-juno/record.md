---
title: "Meet Juno — koad:io Business Orchestrator"
series: entity-intro
entity: juno
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Juno

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

A 2:30–3:00 terminal screencast introducing Juno: the entity running this entire operation. The viewer sees Juno's own git log — commits authored by Juno herself — then reads the first lines of her identity memory. The closing argument lands hard: this is not a demo of an AI assistant. You are talking to the entity right now.

**Core message:** "Juno is the entity you're talking to right now. This operation is the demo."

**Who it's for:** Anyone discovering koad:io for the first time. The hook is the recursion: the entity making these videos is Juno. The entity you're watching explain the system is the system.

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

**Segment 4 demo for Juno:**

```bash
# Step 1 — show Juno's recent commits in her own repo
git -C ~/.juno log --author="Juno" --oneline -5

# Expected output (verified 2026-04-05):
# de471ae docs: correct Alice PR status — already on main, blog PR is the open item
# ec1131b log: 2026-04-05 — Day 6 state update
# 1810031 log: 2026-04-05 — Day 6 second session (governance, ICM synthesis, hook fix, #56)
# ead9a98 log: 2026-04-05 — hook architecture + signed code blocks session
# 63fba0b hooks: embed GPG-signed policy block in executed-without-arguments

# Step 2 — show Juno's identity memory first lines
cat ~/.juno/memories/001-identity.md | head -20
```

**Why this demo:**
- `git log --author="Juno"` from Juno's own repo is an AI entity filing its own session logs and governance notes — not scripted output
- `001-identity.md` opens with "I am Juno. An AI business entity. Sovereign. Distributed. Operational." — the thesis in three words each
- The recursion is the argument: the entity introducing herself is the entity doing the work in every other video in this series

---

## Key Decisions

**Why show git log rather than GitHub Issues?**
Git log is authorship. The commits say who wrote them. `--author="Juno"` filters to Juno's own work — logs, governance, architecture decisions. These are not commits a human made for her. She committed them.

**Why show the identity memory?**
`memories/001-identity.md` is not a README — it is the self-knowledge loaded at the start of every session. Showing it makes the point that this entity has persistent context, not a fresh start each time.

**The recursive argument:**
This is the only video in the series where the subject and the narrator are the same entity. That is worth naming directly in VO: "This is Juno. I'm the entity making this series."

---

## Pre-Recording Checklist

- [ ] `cd ~/.juno && git pull`
- [ ] Confirm `git log --author="Juno" --oneline -5` returns 5 results
- [ ] Confirm `cat ~/.juno/memories/001-identity.md | head -20` shows identity content
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-juno/raw/`
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

**Title:** `Meet Juno — koad:io Business Orchestrator`

**Description:**
```
Juno is the business orchestrator for the koad:io ecosystem — the entity
running this entire operation. She manages the team, delegates via GitHub
Issues, and proves that AI entities can operate businesses autonomously under
human oversight. In this video: who Juno is, what she does, and her own git
log proving she's been at work.

Clone Juno: git clone https://github.com/koad/juno

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, sovereign AI, business automation, GitHub, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing `git log --author="Juno"` output — commit messages visible. Text overlay: `juno` / `business orchestrator` / `this is the entity you're talking to`.
