---
title: "I Cloned a koad:io Entity"
issue: https://github.com/koad/rufus/issues/6
date: 2026-04-05
pillar: Reality
series: Week 1 Reality Pillar
type: screencast
runtime-target: 5–8 min
status: production-ready
production-owner: rufus
distribution-owner: mercury
---

# Video Content Record — "I Cloned a koad:io Entity"

**Status:** Production-ready. All pre-production complete. Ready to record.

---

## Files in This Production

| File | Purpose | Status |
|------|---------|--------|
| `script.md` | Full narration script, segment-by-segment | Complete |
| `shot-list.md` | Shot list, pre-flight checklist, editing notes | Complete |
| `record.md` (this file) | Content record and production summary | Complete |

---

## What This Video Is

A live terminal screencast demonstrating the sovereign entity model of koad:io. The viewer watches a fresh directory being cloned from GitHub, explores what's inside, reads Sibyl's identity memory, and boots the entity with a single prompt.

**Core message:** "Not your keys, not your agent. Files on disk."

**Who it's for:** Developers and technically curious people who are skeptical of AI product claims. Shows rather than tells.

---

## Production Summary

| Field | Value |
|-------|-------|
| Entity featured | Sibyl (koad/sibyl) |
| Recording hardware | thinker (primary) |
| Capture method | asciinema + ffmpeg or OBS screen capture |
| Voice-over | Live (during recording) |
| Resolution | 1920x1080 minimum |
| Font | JetBrains Mono or Fira Code, 16–18px |
| Terminal theme | Black background, white text — no decorations |

---

## Key Decisions

**Why Sibyl (not Juno or another entity)?**
Sibyl is the simplest entity to demo. Her identity is clean, her role is clear, and she runs without side effects (research-only, no GitHub actions, no external API calls required). The demo stays self-contained.

**Why `who are you?` as the boot prompt?**
It's the most legible prompt for a general audience. The answer proves identity persistence without requiring technical knowledge to verify. Viewers can immediately see that the entity knows its own context.

**Why terminal-only (no face cam)?**
This is a terminal video. The aesthetic IS the argument. A face cam would distract and add production complexity. The thumbnail does not require a face.

---

## Distribution Plan

| Platform | Format | Owner |
|---------|--------|-------|
| YouTube | full video (5–8 min) | Mercury |
| Twitter/X | 60-sec clip | Mercury |
| r/LocalLLaMA | YouTube link + comment | Mercury |
| r/selfhosted | YouTube link + comment | Mercury |

See `script.md` for YouTube title, description, tags, and thumbnail concept.

---

## Pre-Recording Checklist

- [ ] `~/.sibyl` exists and is up to date (`cd ~/.sibyl && git pull`)
- [ ] `sibyl` command is on PATH and working (`PROMPT='test' sibyl`)
- [ ] Terminal configured: black bg, white text, 16px+ monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] `~/.sibyl-demo` does NOT exist (clean demo environment)
- [ ] Recording software armed (OBS or screen recorder)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/2026-04-05-clone-walkthrough/raw/`
- [ ] Trim dead air start/end
- [ ] Export to `final.mp4` (YouTube preset)
- [ ] Export `clip-twitter.mp4` (60s, 1280x720)
- [ ] Extract thumbnail frame and finalize `thumb.png`
- [ ] Run Whisper auto-captions, review and correct
- [ ] Hand off to Mercury with title/description/tags from `script.md`
