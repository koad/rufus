---
title: "Meet Muse — koad:io Visual Designer"
series: entity-intro
entity: muse
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Muse

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

A 2:30–3:00 terminal screencast introducing Muse: the visual designer who produces design briefs before Vulcan builds anything. The viewer sees the full briefs library with `ls ~/.muse/briefs/` — 20+ files, dating back to the first week — then reads the Alice UI brief header to show what a design brief from an entity looks like in practice.

**Core message:** "The UI is designed before it's built. Muse does that design — in markdown, in git, before Vulcan writes a line of code."

**Who it's for:** Designers who didn't expect to see their domain in a terminal. Developers who wonder where the visual direction comes from. Show HN readers asking "does any of this look good?"

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

**Segment 4 demo for Muse:**

```bash
# Step 1 — show the full design library
ls ~/.muse/briefs/

# Expected output: 20+ files — alice-ui-design-brief.md and dated briefs from 2026-04-02 onward

# Step 2 — read the Alice UI brief header
head -20 ~/.muse/briefs/alice-ui-design-brief.md
```

**Why this demo:**
- `ls ~/.muse/briefs/` shows volume and cadence — the dated filenames make clear that design work is ongoing and frequent
- `alice-ui-design-brief.md` is the canonical showcase: it's the brief for the most visible product (Alice), and the header immediately shows status, audience, entity, and references
- Both commands are instantly readable — no domain knowledge required to understand what a design brief is
- The combination of the full library plus one deep read makes the volume/depth argument in under 50 seconds

---

## Key Decisions

**Why the briefs directory rather than a live Muse invocation?**
Muse's output IS the briefs. The files on disk are the deliverables. A live invocation would produce new content during recording, which is unpredictable and risks overrunning the segment. The existing library proves real work, consistently.

**Why `alice-ui-design-brief.md` specifically?**
It's the most referenced brief in the ecosystem — Vulcan, Veritas, and Chiron all reference it. Its header shows status updates (April 5 revision), multiple audiences (Vulcan + Juno), and cross-entity references. It demonstrates that Muse's work feeds the build process directly.

---

## Pre-Recording Checklist

- [ ] `cd ~/.muse && git pull`
- [ ] Confirm `ls ~/.muse/briefs/` shows 10+ files
- [ ] `head -20 ~/.muse/briefs/alice-ui-design-brief.md` produces expected output (status, date, audience, entity, references)
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-muse/raw/`
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

**Title:** `Meet Muse — koad:io Visual Designer`

**Description:**
```
Muse is the visual designer for the koad:io ecosystem — the entity that writes
design briefs before Vulcan builds anything. 10+ briefs in the library, from
the koad.sh homepage to Alice's 12-level learning interface. In this video:
who Muse is, what the design library looks like, and a live read of the Alice
UI design brief.

Clone Muse: git clone https://github.com/koad/muse

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, sovereign AI, UI design, design system, Alice, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing `ls ~/.muse/briefs/` output — full list of brief filenames visible. Text overlay: `muse` / `visual designer`.
