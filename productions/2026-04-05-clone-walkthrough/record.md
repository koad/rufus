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

A live terminal screencast demonstrating the sovereign entity model of koad:io. The viewer watches a fresh directory being cloned from GitHub, explores what's inside (README.md, CLAUDE.md, the hook), and boots the entity with a single prompt.

**Core message:** "Not your keys, not your agent. Files on disk."

**Who it's for:** Developers and technically curious people who are skeptical of AI product claims. Shows rather than tells.

---

## Production Summary

| Field | Value |
|-------|-------|
| Entity featured | Chiron (koad/chiron) |
| Recording hardware | thinker (primary) |
| Capture method | asciinema + ffmpeg or OBS screen capture |
| Voice-over | Live (during recording) |
| Resolution | 1920x1080 minimum |
| Font | JetBrains Mono or Fira Code, 16–18px |
| Terminal theme | Black background, white text — no decorations |

---

## Key Decisions

**Why Chiron (not Juno or another entity)?**
Chiron is already on GitHub (koad/chiron), has a clean README, a well-defined role with hard scope edges, and a hook that demonstrates both prompt-driven and interactive modes. His CLAUDE.md explicitly enumerates what he owns and does not own — making the scope conversation legible to a general audience without requiring technical knowledge.

**Why `what is your role?` as the boot prompt?**
It's the most direct identity verification a viewer can follow. Chiron's answer will reference curriculum architecture, pedagogy, and team position — all of which can be verified against the files the viewer just watched scroll by. The alignment between the memory files and the live response is the proof.

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

- [ ] `~/.chiron` exists and is up to date (`cd ~/.chiron && git pull`)
- [ ] `chiron` command is on PATH and working (`PROMPT='test' chiron`)
- [ ] Terminal configured: black bg, white text, 16px+ monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] `~/.chiron-demo` does NOT exist (clean demo environment)
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
