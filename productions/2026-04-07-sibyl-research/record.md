---
title: "Live Session: Sibyl Does Research"
issue: https://github.com/koad/rufus/issues/7
date: 2026-04-07
pillar: Reality
series: Week 1 Reality Pillar
type: live-session-recording
runtime-target: 6–8 min (edited from ~9 min raw)
status: production-ready
production-owner: rufus
distribution-owner: mercury
recording-machine: fourty4
---

# Video Content Record — "Live Session: Sibyl Does Research"

**Status:** Production-ready. Script and shot list complete. Ready to record on fourty4.

---

## Files in This Production

| File | Purpose | Status |
|------|---------|--------|
| `shot-list.md` | Full shot list, recording guide, edit notes | Complete |
| `record.md` (this file) | Content record and production summary | Complete |

**Note:** No separate script.md — this is an unscripted live session. The shot-list.md contains section-by-section guidance. Voice-over is not used; title cards carry the narrative.

---

## What This Video Is

An unedited (in spirit) live recording of Sibyl executing a real research task, start to finish. Juno files a task brief, Sibyl reads it, runs inference on local ollama, writes structured output to disk, commits to git. Proof that entities do actual work, not canned demos.

**Core message:** "Sibyl received a task, did the work, committed the result. No cloud. No API calls. Local hardware."

**Who it's for:** Technical audience who want to see what "entity work" actually looks like. The git commit is the receipt.

---

## Production Summary

| Field | Value |
|-------|-------|
| Entity featured | Sibyl (via ollama on fourty4) |
| Recording hardware | fourty4 (Mac Mini, local ollama) |
| Capture method | OBS (macOS) or QuickTime screen capture |
| Voice-over | None — title cards only |
| Terminal layout | Two-pane split (tmux or iTerm): 70% left (Sibyl session), 30% right (watch pane) |
| Resolution | 1920x1080 |
| Edit style | Sections 1, 2, 4, 5 at 1x; Section 3 (inference) at 2x–3x |

---

## Research Task

**Task brief:** Top 3 distribution channels for a privacy-first AI infrastructure project targeting self-hosted developers in 2026. For each: name, audience quality signal, ideal content format, one concrete posting strategy.

**Why this task:**
- Real, relevant, verifiable (not a toy demo)
- Produces structured output that reads well on screen
- Cross-references Sibyl's existing content calendar work (viewers who follow the series can verify she's consistent)
- Demonstrates Juno → Sibyl handoff pattern (cross-entity coordination visible on screen)

See `shot-list.md` Section 2 for the exact task brief and heredoc command.

---

## Key Decisions

**Why fourty4 (not thinker or flowbie)?**
The whole point is local inference. Running Sibyl on fourty4's ollama proves the sovereign stack — no API call leaving the building. If it ran on thinker with Claude API calls, we'd need to qualify "local." fourty4 keeps it clean.

**Why no voice-over?**
The terminal output tells the story. Voice-over would require scripting or skilled improvisation, and risks talking over key readable moments. Title cards are sufficient and faster to produce.

**Why git commit as the closing beat?**
The commit hash is a verifiable timestamp. Anyone watching can cross-reference the koad/sibyl GitHub repo. It's not just output — it's proof, on disk, in public.

---

## Pre-Recording Checklist (fourty4)

- [ ] fourty4 is online and SSH accessible (`ssh fourty4 'echo ok'`)
- [ ] ollama is running with correct model (`ssh fourty4 'ollama list && ollama ps'`)
- [ ] `~/.sibyl` on fourty4 is up to date (`ssh fourty4 'cd ~/.sibyl && git pull'`)
- [ ] `~/.sibyl/tasks/incoming/` directory exists
- [ ] `~/.sibyl/research/` directory exists and is writable
- [ ] `~/.sibyl` is a clean git repo (`ssh fourty4 'cd ~/.sibyl && git status'`)
- [ ] tmux or iTerm split configured (70/30)
- [ ] Font size set for legibility at 1080p after 2x speedup (≥18pt body)
- [ ] Recording software ready on fourty4
- [ ] Dry run: confirm ollama responds to a test prompt before recording

---

## Edit Notes Summary

| Section | Speed | Reason |
|---------|-------|--------|
| 1 — Date + identity | 1x | Authenticity anchor — must not be sped up |
| 2 — Task filing | 1x | Coordination handoff — must be readable |
| 3 — Inference | 2x (3x for reasoning tokens) | Keep viewer engaged without boring them |
| 3.4 pause (first output) | 1x | Let first channel result land |
| 4 — Output review | 1x | Proof moment — do not rush |
| 5 — Git commit | 1x | Timestamp proof — non-negotiable |

Full edit notes in `shot-list.md` → "Edit Notes Summary" section.

---

## Distribution Plan

| Platform | Format | Owner |
|---------|--------|-------|
| YouTube | Full video (6–8 min) | Mercury |
| Twitter/X | 1-min clip (per shot-list.md "1-Minute Twitter/X Clip Cut") | Mercury |
| r/LocalLLaMA | YouTube link, post title: "Ran a local AI entity doing actual research work — here's the session recording" | Mercury |

Mercury to draft YouTube title/description. Thumbnail frame: `git log --oneline` output (Section 5.3 of shot list).

---

## Post-Production Checklist

- [ ] Raw recording saved to `productions/2026-04-07-sibyl-research/raw/`
- [ ] Speed adjustments applied per edit notes (sections 3 at 2x/3x)
- [ ] Title cards added at section transitions (text per shot-list.md)
- [ ] Background music added for Section 3 only (lo-fi, low volume)
- [ ] Export to `final.mp4` (YouTube preset, 1920x1080)
- [ ] Export `clip-twitter.mp4` (1-min cut, 1280x720, per shot-list.md)
- [ ] Thumbnail extracted from git log frame (Section 5.3)
- [ ] Research output file link confirmed active (`~/.sibyl/research/2026-04-07-channel-analysis.md` committed and pushed)
- [ ] Hand off to Mercury with distribution package
