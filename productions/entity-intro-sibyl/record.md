---
title: "Meet Sibyl — koad:io Research Director"
series: entity-intro
entity: sibyl
issue: TBD
date: 2026-04-05
pillar: Reality
type: screencast
runtime-target: under 3 minutes
status: pre-production
production-owner: rufus
distribution-owner: mercury
---

# Production Record — Meet Sibyl

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

A 2:30–3:00 terminal screencast introducing Sibyl: the research director who runs on local inference (deepseek-r1:8b via ollama on fourty4) and feeds intelligence into the front of the koad:io content and product pipeline. The viewer sees a small research question invoked, the output, and the automatic git commit that records the deliverable.

**Core message:** "Sibyl doesn't summarize — she synthesizes, commits, and hands off. Every brief has an actionable conclusion, not just a summary. And it runs on a $0/query local model."

**Who it's for:** Developers who have tried to make AI do research work and found it disposable. r/LocalLLaMA readers interested in practical ollama workflows. Anyone skeptical that entity specialization produces better results than a generic chat.

---

## Production Summary

| Field | Value |
|-------|-------|
| Recording hardware | thinker (primary); SSH to fourty4 for invocation |
| Capture method | OBS screen capture of thinker terminal (SSH session to fourty4 visible) |
| Voice-over | Live during recording |
| Resolution | 1920x1080 minimum |
| Font | JetBrains Mono or Fira Code, 16–18px |
| Terminal theme | Black background, white text, no decorations |
| Shell prompt | `$ ` only |

---

## Demo Specification

**Segment 4 demo for Sibyl:**

```bash
# Step 1 — navigate to sibyl and show research dir
cd ~/.sibyl && ls research/ | tail -5

# Step 2 — invoke sibyl with a small contained research question
# The question should be answerable in ~30 seconds of inference
PROMPT="What are the top 3 reasons developers clone open source tools instead of subscribing to SaaS equivalents? Two sentences max per reason." sibyl

# Step 3 — after output, show it committed
git -C ~/.sibyl log --oneline -3
```

**Alternative if fourty4 SSH is unavailable during recording:**
Show an existing research output file instead of live invocation:
```bash
ls ~/.sibyl/research/ | tail -5
cat ~/.sibyl/research/$(ls ~/.sibyl/research/ | tail -1) | head -25
git -C ~/.sibyl log --oneline -3
```

**Why this demo:**
- Live invocation shows the entity is real and working, not just a directory
- The research question is tuned to be short and produce a tight answer on screen
- The git commit at the end proves the deliverable is permanent — not a chat log that disappears
- Fallback path keeps video produceable if fourty4 is offline

---

## Key Decisions

**Why a small question instead of a full research brief?**
A full brief runs 3–8 minutes of inference time — far too long for this format. The question is chosen to demonstrate the output structure (actionable, not just summary) in a form that fits on screen.

**Why show the git commit?**
This is Sibyl's differentiator from a chat session. The commit is the proof. Every viewer who has used ChatGPT for research and lost the output will understand immediately.

**Why deepseek-r1:8b?**
$0/query, 128k context, runs on fourty4. Mentioning it in the VO is part of the Show HN pitch.

---

## Pre-Recording Checklist

- [ ] `ssh fourty4 echo ok` — confirm SSH access
- [ ] `cd ~/.sibyl && git pull`
- [ ] `sibyl` command works: `PROMPT="test" sibyl` — confirm it runs without error
- [ ] Research directory has at least 2 existing files: `ls ~/.sibyl/research/`
- [ ] Terminal configured: black bg, white text, 16–18px monospace
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed
- [ ] Quiet environment

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/entity-intro-sibyl/raw/`
- [ ] Trim dead air during inference wait (cut to a 2s pause if inference takes >10s)
- [ ] Export to `final.mp4` (YouTube preset, 1080p)
- [ ] Export `clip-twitter.mp4` (60s, 1280x720)
- [ ] Opening card and closing card frames ready
- [ ] Whisper auto-captions, reviewed and corrected
- [ ] Hand off to Mercury with metadata from `script.md`
- [ ] Update this record: status → published, add YouTube URL

---

## YouTube Metadata

**Title:** `Meet Sibyl — koad:io Research Director`

**Description:**
```
Sibyl is the research director for the koad:io ecosystem — the entity that
feeds intelligence into the front of every content and product decision. She
runs on deepseek-r1:8b via ollama (local, $0/query) and every brief she
produces is committed to git automatically.

Clone Sibyl: git clone https://github.com/koad/sibyl

koad:io — sovereign AI infrastructure. Files on disk. Your keys. No vendor.
https://koad.sh
```

**Tags:** `koad:io, AI agents, local LLM, ollama, deepseek, research automation, sovereign AI, entity-intro, terminal`

**Thumbnail concept:** Terminal showing Sibyl's output scrolling — last line visible is the git commit hash. Text overlay: `sibyl` / `research director` / `$0/query`.
