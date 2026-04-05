---
title: "Meet Veritas — koad:io Quality and Fact-Check"
series: entity-intro
entity: veritas
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Veritas

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

A 2:30–3:00 terminal screencast introducing Veritas: the fact-checker and quality officer who sits between every creative entity and the outside world. The viewer sees the reviews directory (21 reviews and counting), reads the opening of a real review file showing the verdict structure — PASS / NEEDS_REVISION / FAIL — and understands why an autonomous team needs a dedicated truth function.

**Core message:** "Veritas doesn't block — it catches. Nothing factual leaves the team without passing through here. Twenty-one reviews on disk, each one with a verdict."

**Who it's for:** Developers building AI pipelines who haven't thought about verification. Journalists and researchers who want to see how the koad:io team handles factual accuracy without a human editor in the loop.

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

**Segment 4 demo for Veritas:**

```bash
# Step 1 — count the reviews
ls ~/.veritas/reviews/ | wc -l

# Expected output: 21

# Step 2 — list review files
ls ~/.veritas/reviews/

# Step 3 — read the opening of a real review
head -20 ~/.veritas/reviews/2026-04-04-faber-pipeline-review.md
```

**Why this demo:**
- `wc -l` gives a concrete number — 21 reviews proves operational history, not a demo entity
- `ls reviews/` shows the breadth: Mercury, Vulcan, Sibyl, Faber, competitive claims — every team function has been reviewed
- `head -20` of a real review shows the verdict structure: reviewer, status, confidence level, method — immediately legible
- Together they prove Veritas is the active gatekeeper of team accuracy

---

## Key Decisions

**Why show reviews directory count rather than invoke Veritas live?**
A live verification run would be long and model-variable. The 21 existing reviews prove real operational history — every one of them is a real review of real team output. The files are the demo.

**Why 2026-04-04-faber-pipeline-review.md specifically?**
It's the most recent complex review — covers three posts, multiple claims, and shows the NEEDS_REVISION verdict with specific line-level feedback. It demonstrates Veritas's full verification workflow in the most compact view.

---

## Pre-Recording Checklist

- [ ] `cd ~/.veritas && git pull`
- [ ] Confirm `ls ~/.veritas/reviews/ | wc -l` returns 21 (or current count — note it before recording)
- [ ] `head -20 ~/.veritas/reviews/2026-04-04-faber-pipeline-review.md` produces expected output
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-veritas/raw/`
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

**Title:** `Meet Veritas — koad:io Quality and Fact-Check`

**Description:**
```
Veritas is the fact-checker and quality officer for the koad:io ecosystem —
the entity that sits between creation and publication in every team workflow.
In this video: who Veritas is, how the verification protocol works, and a live
look at 21 reviews on disk.

Clone Veritas: git clone https://github.com/koad/veritas

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, sovereign AI, fact-checking, quality assurance, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing `ls ~/.veritas/reviews/` — multiple dated review files visible with clear team output names. Text overlay: `veritas` / `quality and fact-check`.
