---
title: "The Week 1 Skeptics Were Right"
issue: https://github.com/koad/rufus/issues/TBD
date: 2026-04-12
pillar: Reality
series: Week 2 Reality Pillar
type: terminal-screencast
tier: Tier 3
runtime-target: 7–9 min
status: pre-production
production-owner: rufus
distribution-owner: mercury
faber-source: posts/ (to be written — Day 12 blog post)
---

# Video Content Record — "The Week 1 Skeptics Were Right"

**Status:** Pre-production. Script and shot list complete. Faber's blog post for Day 12 is not yet written (see Week 2 calendar). This production record was built from the objections documented in Juno's Show HN honest-accounting section and from the operational state as of Day 6.

---

## Files in This Production

| File | Purpose | Status |
|------|---------|--------|
| `script.md` | Full narration script, segment-by-segment | Complete |
| `shot-list.md` | Shot list, pre-flight checklist, editing notes | Complete |
| `record.md` (this file) | Content record and production summary | Complete |

---

## What This Video Is

A direct, honest engagement with the four genuine objections to Week 1. Not a defensive rebuttal. Not a dismissal. An honest video that acknowledges what's real in each objection, then explains why the architecture still holds.

The four objections addressed:

1. **"No daemon yet."** Cross-entity trust verification is manual. The daemon that enforces trust scope is in progress, not shipped. This is real.
2. **"Manual coordination."** koad files GitHub Issues; Juno delegates by creating issues; entities comment back. That's a human-dependent loop, not autonomous orchestration. This is real.
3. **"koad is the bottleneck."** One human. Every unblocked action routes through koad. API auth, Chiron gestation, fourty4 issues — all blocked on koad. This is real.
4. **"No sponsors yet."** GitHub Sponsors is live. Tiers exist. Zero sponsors after 6 days. This is real.

Each objection gets a terminal segment that shows the actual state, not a slide claiming otherwise. Then each objection gets an honest explanation of why the architecture holds anyway.

**Core message:** "The skeptics identified the real gaps. Here's what's real, here's why it matters, and here's what the architecture gives you that those gaps don't touch."

**Who it's for:** Technical readers who read the Show HN post, had legitimate objections, and are deciding whether to dig deeper. The audience that rewards honesty over polish.

---

## Production Summary

| Field | Value |
|-------|-------|
| Entities featured | Juno, Vulcan (via GitHub Issues), Sibyl (via commits) |
| Recording hardware | thinker (primary) |
| Capture method | asciinema + ffmpeg or OBS screen capture |
| Voice-over | Live (during recording) |
| Resolution | 1920x1080 minimum |
| Font | JetBrains Mono or Fira Code, 16–18px |
| Terminal theme | Black background (#000000), white text — no decorations |
| Tier | Tier 3 — terminal capture only, no camera required |

---

## Key Decisions

**Why show the gaps in a video rather than just writing about them?**
Text claims about honesty are cheap. A terminal showing zero sponsors, showing a blocked GitHub issue, showing a manual coordination loop — that's harder to fake. The video earns the honesty claim by showing the actual state. The viewer sees what Juno's git log looks like, what the issue queue looks like, what "blocked on koad" means in practice.

**Why four objections, not more?**
These four are the ones that are (a) genuinely correct and (b) structurally important. Lesser objections (UX, docs, naming) don't change the architecture argument and would dilute the segment. These four are the ones a serious developer would raise after reading a week of content.

**Why not just title it "Week 1 Retrospective"?**
Because "retrospective" signals introspection. "The Skeptics Were Right" signals accountability. The title does work before the viewer presses play — it signals that this is not a defensive video. That's the trust-building move.

**Why no inference output in this video?**
The skeptics aren't questioning whether entities respond to prompts. They're questioning the operational architecture. Showing inference output would be changing the subject. The evidence that addresses these objections is all in the repo state — commits, issues, blocked items, sponsor count.

**Why end with the architecture holding, not just "we'll fix it"?**
"We'll fix it" is a promise. "Here's what the architecture gives you that those gaps don't touch" is a demonstration. The daemon gap doesn't affect the git-native identity claim. The manual coordination gap doesn't affect the trust bond claim. The video should be precise about which objections touch which claims — and where the objections stop.

---

## Distribution Plan

| Platform | Format | Owner |
|---------|--------|-------|
| YouTube | full video (7–9 min) | Mercury |
| Twitter/X | 60-sec clip (the "koad is the bottleneck" segment) | Mercury |
| HackerNews | Submitted as follow-up to Show HN thread | Mercury / koad |
| r/selfhosted | YouTube link with honest framing comment | Mercury |

See `script.md` for full YouTube title, description, and tags.

---

## Pre-Recording Checklist

- [ ] `~/.juno` is current: `cd ~/.juno && git pull`
- [ ] `gh issue list --state open --repo koad/juno` returns the actual open issue list
- [ ] Blocked items visible in issue list (confirm which issues are blocked on koad)
- [ ] `git log --author="Juno" --oneline` returns commits
- [ ] `git log --author="Vulcan" --oneline` in `~/.vulcan` returns commits (or use GitHub)
- [ ] Confirm GitHub Sponsors page is live: `open https://github.com/sponsors/koad`
- [ ] Terminal configured: black bg, white text, 16px+ monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed
- [ ] Quiet environment for voice-over

---

## Post-Production Checklist

- [ ] Raw recording saved to `~/.rufus/recordings/2026-04-12-skeptics-raw.mp4` (or `.cast`)
- [ ] Trim dead air at start/end only
- [ ] Do NOT speed-ramp or cut the git log segment — real-time only
- [ ] Export to `2026-04-12-skeptics-final.mp4` (YouTube preset)
- [ ] Export `2026-04-12-skeptics-clip-twitter.mp4` (60s, 1280x720 — the bottleneck segment)
- [ ] Extract thumbnail frame: the open issue list showing "blocked on koad" items
- [ ] Run Whisper auto-captions, review and correct entity names and technical terms
- [ ] Hand off to Mercury with title/description/tags from `script.md`

---

## Retake Triggers

- Any typo requiring more than one backspace
- `gh issue list` returns an error (auth issue — fix before recording)
- Any window or focus switch during recording
- Any segment where the VO sounds defensive rather than factual
