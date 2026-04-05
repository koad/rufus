---
title: "Meet Faber — koad:io Content Strategist"
series: entity-intro
entity: faber
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Faber

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

A 2:30–3:00 terminal screencast introducing Faber: the content strategist who synthesizes research, brand positioning, and audience intelligence into the Reality Pillar post series. The viewer sees the posts directory, reads the frontmatter of a post, and understands that this content pipeline runs entity-to-entity without a human writing each piece.

**Core message:** "Faber doesn't write for the sake of writing — he writes because the ecosystem needs a voice and the audience needs to see the work. Every post is committed. Every one traces back to a research brief."

**Who it's for:** Content creators who wonder if AI can produce consistent, strategic content without a human editor for each piece. Developers who want to understand how the koad:io team produces the Reality Pillar without a dedicated human content team. r/selfhosted readers who care about proof over pitch.

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

**Segment 4 demo for Faber:**

```bash
# Step 1 — show the posts directory
ls ~/.faber/content/

# Expected: a list of date-named post files, multiple entries

# Step 2 — read the header of a post
cat ~/.faber/content/2026-04-05-trust-bonds-arent-policy.md | head -20

# OR if that file doesn't exist, use the most recent post:
# cat ~/.faber/content/$(ls ~/.faber/content/ | tail -1) | head -20
```

**Why this demo:**
- The posts directory shows volume — multiple dates, multiple topics, all committed
- The post header (YAML frontmatter + first paragraph) shows the content is structured, intentional, and attributable
- No live invocation needed — the artifact is the demo
- Keeps the video within the 3-minute ceiling reliably

---

## Key Decisions

**Why show the posts directory rather than invoke Faber live?**
Faber's value is the accumulated body of work, not a single generation. The directory view — 10+ posts, all date-named, all committed — is more compelling than one fresh generation. It also keeps the video predictably short.

**Why read the frontmatter rather than the full post body?**
The frontmatter shows: date, pillar, status, priority, description. That's the strategy layer — not the writing. It proves that each post exists within a system, not just as an isolated document. The writing sells itself on the blog.

**Which post to read:**
Prefer `2026-04-05-trust-bonds-arent-policy.md` if present — it has a strong title that explains the philosophical position. Fallback to the most recent file.

---

## Pre-Recording Checklist

- [ ] `cd ~/.faber && git pull`
- [ ] Confirm posts directory has files: `ls ~/.faber/content/ | wc -l` > 3
- [ ] Confirm target post exists: `ls ~/.faber/content/2026-04-05-trust-bonds-arent-policy.md`
- [ ] If not, identify fallback post: `ls ~/.faber/content/ | tail -1`
- [ ] `head -20` of target post produces readable output (YAML frontmatter visible)
- [ ] Terminal configured: black bg, white text, 16–18px monospace
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed
- [ ] Quiet environment

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-faber/raw/`
- [ ] Trim dead air start/end
- [ ] Export to `final.mp4` (YouTube preset, 1080p)
- [ ] Export `clip-twitter.mp4` (60s, 1280x720)
- [ ] Opening card and closing card frames ready
- [ ] Whisper auto-captions, reviewed and corrected
- [ ] Hand off to Mercury with metadata from `script.md`
- [ ] Update this record: status → published, add YouTube URL

---

## YouTube Metadata

**Title:** `Meet Faber — koad:io Content Strategist`

**Description:**
```
Faber is the content strategist for the koad:io ecosystem — the entity that
writes the Reality Pillar post series, synthesizing research from Sibyl into
content the audience can use. No human wrote these posts. They're committed
to git, dated, and structured for distribution.

Clone Faber: git clone https://github.com/koad/faber

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, content strategy, sovereign AI, entity-intro, terminal, AI content, open source`

**Thumbnail concept:** Terminal showing `ls ~/.faber/content/` — a list of 10+ date-named markdown files. Text overlay: `faber` / `content strategist` / `Reality Pillar`.
