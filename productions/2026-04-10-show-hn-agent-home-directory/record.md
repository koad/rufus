---
title: "Show HN: Agent Home Directory — Three Commands, Then git log"
issue: https://github.com/koad/rufus/issues/TBD
date: 2026-04-10
pillar: Reality
series: Week 2 Reality Pillar
type: terminal-screencast
tier: Tier 3
runtime-target: 4–6 min
status: pre-production
production-owner: rufus
distribution-owner: mercury
faber-source: posts/2026-04-10-show-hn-agent-home-directory.md
---

# Video Content Record — "Show HN: Agent Home Directory"

**Status:** Pre-production. Script and shot list complete. Ready to record once Juno repo is current.

---

## Files in This Production

| File | Purpose | Status |
|------|---------|--------|
| `script.md` | Full narration script, segment-by-segment | Complete |
| `shot-list.md` | Shot list, pre-flight checklist, editing notes | Complete |
| `record.md` (this file) | Content record and production summary | Complete |

---

## What This Video Is

A developer is watching another developer's first encounter with koad:io. Not a polished demo — an honest walkthrough of three Unix commands that tell the complete story: who the entity is, what it's authorized to do, and what it has done.

This is the companion video to the Day 10 Show HN post. The post makes the written argument. The video makes the same argument live, on screen, with real output. A viewer who bounced off the Show HN text gets a second path in.

**Core message:** "Three commands. That's the whole story. Identity. Authorization. History."

**Who it's for:** Developers who just read the Show HN post and want to see it run. Self-hosted developers who are skeptical of AI product claims and respond to "show me the terminal."

---

## Production Summary

| Field | Value |
|-------|-------|
| Entity featured | Juno (koad/juno) |
| Recording hardware | thinker (primary) |
| Capture method | asciinema + ffmpeg or OBS screen capture |
| Voice-over | Live (during recording) |
| Resolution | 1920x1080 minimum |
| Font | JetBrains Mono or Fira Code, 16–18px |
| Terminal theme | Black background (#000000), white text — no decorations |
| Tier | Tier 3 — terminal capture only, no camera required |

---

## Key Decisions

**Why Juno (not Chiron or another entity)?**
The Show HN post is filed by koad and centers on Juno as the operational entity — 213 commits, 6-day history, trust bonds already signed and verifiable. Juno has the most compelling git log of any entity. The post already cites `git log --author="Juno" --oneline` as the accountability proof. The video must show exactly what the post promises. Using Chiron (the clone-walkthrough entity) would dilute the connection.

**Why the three-command structure (cat identity → gpg verify → git log)?**
Faber's Show HN post identifies these three commands as telling the complete story. The video doesn't invent a new arc — it makes the post's arc visible. The viewer who read the post will recognize each command as it runs and feel the alignment between the written claim and the live evidence.

**Why git log as the final shot (not a PROMPT=... invocation)?**
The Day 5 clone-walkthrough already shows an entity booting and responding. This video is not about "does it work" — it's about "does it have history." The git log is the argument the Show HN audience cares about: verifiable, tamper-evident, not a vendor's audit trail. The emotional weight lands on the scroll, not on inference output.

**Why no close-up of inference output?**
This video is for an audience that arrived via Show HN — they are skeptical of demos that show AI being impressive. The git log is more credible than any inference response. Showing commits is showing work. Inference responses can be staged. git history cannot.

---

## Distribution Plan

| Platform | Format | Owner |
|---------|--------|-------|
| YouTube | full video (4–6 min) | Mercury |
| Twitter/X | 60-sec clip (the git log scroll) | Mercury |
| HackerNews | Video link in Show HN comment thread | Mercury / koad |
| Dev.to | Embedded video in cross-posted article | Mercury |

The YouTube description includes the three commands verbatim so viewers can follow along immediately. See `script.md` for full title, description, and tags.

---

## Pre-Recording Checklist

- [ ] `~/.juno` is current: `cd ~/.juno && git pull`
- [ ] `git log --author="Juno" --oneline` returns 6+ days of commits (verify count)
- [ ] `~/.juno/trust/bonds/juno-to-sibyl.md.asc` exists and is verifiable
- [ ] GPG key for Juno imported locally: `gpg --list-keys juno@kingofalldata.com`
- [ ] `gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc` returns "Good signature"
- [ ] `~/.juno/memories/001-identity.md` exists and is current
- [ ] Terminal configured: black bg, white text, 16px+ monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `~/.rufus/recordings/2026-04-10-show-hn-raw.mp4` (or `.cast`)
- [ ] Trim dead air at start/end only
- [ ] Do NOT cut the git log scroll (Shot 4) — this is the emotional core
- [ ] Export to `2026-04-10-show-hn-final.mp4` (YouTube preset)
- [ ] Export `2026-04-10-show-hn-clip-twitter.mp4` (60s, 1280x720 — start at git log scroll)
- [ ] Extract thumbnail frame: the moment git log fills the screen (Shot 4)
- [ ] Run Whisper auto-captions, review and correct entity names and technical terms
- [ ] Hand off to Mercury with title/description/tags from `script.md`

---

## Retake Triggers

- Any typo requiring more than one backspace
- `gpg --verify` returns anything other than "Good signature from..."
- git log returns zero commits or shows wrong author
- Any window or focus switch during recording
