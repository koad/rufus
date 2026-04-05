---
title: "Meet Vulcan — koad:io Builder"
series: entity-intro
entity: vulcan
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Vulcan

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

A 2:30–3:00 terminal screencast introducing Vulcan: the builder who ships real code to real repositories. The viewer sees the GitHub issue list for koad/vulcan — closed issues proving shipped work — then sees `git log --author="Vulcan"` from the Alice repository, proving commits to production. Alice Phase 2A is the anchor: a shipped product, built by an entity.

**Core message:** "Vulcan ships real code to real repos. Alice Phase 2A is on kingofalldata.com because Vulcan built it."

**Who it's for:** Skeptics who think AI entities can't ship real software. Developers who want to know if the build loop actually closes. Show HN readers asking "but does it actually work?"

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

**Segment 4 demo for Vulcan:**

```bash
# Step 1 — show issues Vulcan has closed
gh issue list --repo koad/vulcan --state closed | head -10

# Expected output: 10 most recently closed issues with titles and dates

# Step 2 — show Vulcan's commits on Alice's repo
git -C ~/.demo-koadcom log --author="Vulcan" --oneline -5
# OR if demo repo not available:
# gh api repos/koad/kingofalldata-dot-com/commits?per_page=5 --jq '.[].commit | "\(.author.name): \(.message | split("\n")[0])"'
```

**Why this demo:**
- GitHub issue list with `--state closed` is the fastest proof of shipped work — each line is a task completed, not a task planned
- `git log --author="Vulcan"` on the Alice repo puts Vulcan's name in the commit history of a production codebase — the strongest possible evidence
- The combination of issues closed + commits landed makes the skeptic argument: this is real, on GitHub, verifiable right now
- Any viewer can run these commands themselves after watching

---

## Key Decisions

**Why show closed issues rather than open ones?**
Closed issues are proof of completed work. Open issues are plans. The argument is about shipping, not planning. Every closed issue is a task that went from filed to done — and the commit is the artifact.

**Why Alice specifically rather than another repo?**
Alice Phase 2A is live on kingofalldata.com — a public URL anyone can visit. The commit that shipped it is on GitHub. This is the clearest possible chain: issue filed → Vulcan builds → commit lands → product ships → URL live. No other entity has a chain that direct.

**Alternative demo command (if local clone is unavailable):**
```bash
gh api repos/koad/kingofalldata-dot-com/commits?per_page=5 \
  --jq '.[].commit | "\(.author.name): \(.message | split("\n")[0])"'
```

---

## Pre-Recording Checklist

- [ ] `cd ~/.vulcan && git pull`
- [ ] Confirm `gh issue list --repo koad/vulcan --state closed | head -10` returns 10 results
- [ ] Prepare git log command: either clone koad/kingofalldata-dot-com or use gh API fallback
- [ ] If using local clone: `git clone https://github.com/koad/kingofalldata-dot-com ~/.demo-koadcom` (do this before recording)
- [ ] Terminal configured: black bg, white text, 16–18px monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-vulcan/raw/`
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

**Title:** `Meet Vulcan — koad:io Builder`

**Description:**
```
Vulcan is the builder for the koad:io ecosystem — the entity that ships real
code to real repositories. Alice Phase 2A is live on kingofalldata.com because
Vulcan built it. In this video: who Vulcan is, how the build loop works, and
live proof from GitHub — issues closed, commits landed.

Clone Vulcan: git clone https://github.com/koad/vulcan

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, sovereign AI, software development, Alice, GitHub, entity-intro, terminal, open source`

**Thumbnail concept:** Terminal showing `gh issue list --repo koad/vulcan --state closed` output — CLOSED labels visible in every line. Text overlay: `vulcan` / `builder` / `ships real code`.
