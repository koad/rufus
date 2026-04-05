---
title: "Meet Vesta — koad:io Protocol Keeper"
series: entity-intro
entity: vesta
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Vesta

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

A 2:30–3:00 terminal screencast introducing Vesta: the protocol keeper who has written over 45 specs governing every behavior in the koad:io ecosystem. The viewer sees the volume of the specs directory with a simple `wc -l`, then reads the first lines of VESTA-SPEC-033 — the signed executable code blocks spec — to show the depth and precision of what Vesta produces.

**Core message:** "Every behavior in koad:io has a spec. Vesta wrote it."

**Who it's for:** Developers who want to understand how a distributed multi-entity system stays coherent. Engineers who recognize that governance is a technical problem. Show HN readers asking "how do you keep the agents in sync?"

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

**Segment 4 demo for Vesta:**

```bash
# Step 1 — show volume
ls ~/.vesta/specs/ | wc -l

# Expected output: 45 (or higher — the count is the argument)

# Step 2 — read VESTA-SPEC-033 header
head -20 ~/.vesta/specs/VESTA-SPEC-033-signed-executable-code-blocks.md
```

**Why this demo:**
- `wc -l` after `ls` is the fastest possible proof of volume — one number that speaks for itself
- VESTA-SPEC-033 is the most recent significant spec (signed code blocks, 2026-04-05) and its frontmatter immediately shows scope, authority, and cross-spec references
- Both commands are instantly readable to any technical viewer
- The contrast of one number (45+) followed by dense spec frontmatter makes the argument without commentary

---

## Key Decisions

**Why `ls | wc -l` rather than `ls` scrolling through filenames?**
Volume is the point. A single number is more legible on screen and in narrative than a wall of filenames. The number lands. Then SPEC-033 shows what one spec looks like in depth.

**Why VESTA-SPEC-033 specifically?**
It's the most recent high-complexity spec and it demonstrates cross-spec integration — it references SPEC-007 (Trust Bonds), SPEC-020 (Hook Architecture), and SPEC-027 (CID Privacy). That web of references shows Vesta isn't just writing docs — she's building a coherent system.

---

## Pre-Recording Checklist

- [ ] `cd ~/.vesta && git pull`
- [ ] Confirm `ls ~/.vesta/specs/ | wc -l` returns 45 or more
- [ ] Confirm `head -20 ~/.vesta/specs/VESTA-SPEC-033-signed-executable-code-blocks.md` shows full frontmatter
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-vesta/raw/`
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

**Title:** `Meet Vesta — koad:io Protocol Keeper`

**Description:**
```
Vesta is the protocol keeper for the koad:io ecosystem — 45+ specs covering
every behavior, from trust bond verification to signed executable code blocks.
In this video: who Vesta is, what the spec library looks like, and a live read
of VESTA-SPEC-033.

Clone Vesta: git clone https://github.com/koad/vesta

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, sovereign AI, protocol design, governance, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing `ls ~/.vesta/specs/ | wc -l` with the number prominently visible. Text overlay: `vesta` / `protocol keeper` / `45 specs`.
