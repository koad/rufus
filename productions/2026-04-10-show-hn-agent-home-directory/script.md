---
title: "Show HN: Agent Home Directory"
video-type: terminal-screencast
tier: Tier 3
pillar: Reality
date: 2026-04-10
duration: 4–6 minutes
subject: Juno (business orchestrator entity, koad/juno)
production-owner: Rufus
status: production-ready
---

# Script: "Show HN: Agent Home Directory"

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background (#000000), 16px monospace, full-screen
- [ ] Font: white on black — no themes, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.juno && git pull` — done BEFORE recording (not on camera)
- [ ] `gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc` returns "Good signature"
- [ ] Audio check: quiet room, mic gain set

---

## SEGMENT 1 — Setup (0:00–0:10)

**[SCREEN]** Empty terminal. Prompt only.

**[VOICEOVER]**

> "Three commands. That's all I'm going to run. Let me show you what they tell you."

**[TIMING NOTE]** 10 seconds. Brief setup. Move directly into Shot 2.

---

## SEGMENT 2 — Command One: Identity (0:10–1:00)

**[TYPE — deliberately, normal pace]**

```bash
cat ~/.juno/memories/001-identity.md
```

**[Wait for full file to display. Don't rush.]**

**[VOICEOVER — reading along with key sections]**

As the file begins:
> "Command one. This is Juno's identity file. A committed file on disk — not a prompt parameter, not a runtime variable."

On the role block (wherever it appears in the file):
> "Juno is the business orchestrator. That's not a description I typed into a chat window — it's a file with a six-day git history. Every restart, every framework swap, every host migration: she reads this file."

After the file finishes scrolling:
> "That file has been on disk since day one. The git history proves it."

**[Let file rest 2–3 seconds before typing next command.]**

**[TIMING NOTE]** ~50 seconds for file + VO.

---

## SEGMENT 3 — Command Two: Authorization (1:00–2:00)

**[TYPE]**

```bash
gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc
```

**[VOICEOVER — before running]**
> "Command two. Authorization."

**[Wait for GPG output to appear.]**

**[VOICEOVER — when "Good signature" appears — pause before speaking, let viewer read it]**
> "Good signature. That's not a role setting in a config file. That's a cryptographically signed authorization agreement."

**[TYPE — after GPG output]**

```bash
cat ~/.juno/trust/bonds/juno-to-sibyl.md
```

**[Wait for file to display.]**

**[VOICEOVER — as bond contents scroll]**
> "Juno issued a signed peer bond to Sibyl — the research entity. Open this with any text editor: it tells you exactly what Sibyl is permitted to do, who said so, and when. Compare that to a 403 error with no explanation."

**[TIMING NOTE]** ~60 seconds for GPG output + bond contents + VO.

---

## SEGMENT 4 — Command Three: History (2:00–3:30)

**[TYPE]**

```bash
git -C ~/.juno log --author="Juno" --oneline
```

**[VOICEOVER — before the log scrolls]**
> "Command three. History."

**[The log scrolls. Let it. All of it. Do not cut.]**

**[VOICEOVER — slow pace, weight on each sentence, let the scroll carry the silence between lines]**

> "213 commits. Six days."

*(pause — scroll continues)*

> "Every decision Juno made — timestamped, attributed, tamper-evident."

*(pause)*

> "Not a vendor audit log. Not a cloud dashboard. The same git you already use."

*(pause — let scroll run)*

> "Each one of those lines is a session. A decision. A deliverable. You can read any of them."

**[After scroll completes or reaches bottom — TYPE:]**

```bash
git -C ~/.juno log --author="Juno" --oneline | wc -l
```

**[When count appears — pause before speaking]**

> "That number. That's the entity's cognitive history. On your disk. Revertable. Forkable. Clonable."

**[TIMING NOTE]** ~90 seconds. This is the longest segment and the emotional core. Do not cut it.

---

## SEGMENT 5 — The Mirror (3:30–4:00)

**[TYPE]**

```bash
git -C ~/.juno remote -v
```

**[VOICEOVER — brief]**

> "Remote is GitHub. Public. Anyone can read the history."

*(pause)*

> "But the entity lives here — on this disk. The remote is a mirror, not the source of truth."

**[TIMING NOTE]** ~30 seconds. Transitional beat. Brief.

---

## SEGMENT 6 — The Close (4:00–4:45)

**[TYPE — slowly, one word at a time]**

```bash
git clone https://github.com/koad/juno
```

**[VOICEOVER while clone runs]**
> "To understand the pattern — one clone, then read the identity file."

**[When clone completes — TYPE:]**

```bash
cat juno/memories/001-identity.md
```

**[When file displays — VOICEOVER]**
> "No setup required to understand it. That's persistent agent identity. Files on disk."

*(pause — 2 full seconds)*

> "Not vaporware. Not a demo. Commits."

*(pause)*

> "Link in the description."

**[FADE or cut to black.]**

**[TIMING NOTE]** ~45 seconds. Slowest pacing in the video. Each sentence = one breath. Pauses are structural — editor must not cut them.

---

## Production Notes

- **Hardware**: thinker — primary. The git log is from thinker. Non-negotiable.
- **Resolution**: 1920x1080 minimum.
- **Font**: JetBrains Mono, 16–18px. Legible at 720p after export.
- **Cursor**: Block cursor. Visible throughout.
- **Typing speed**: Comfortable speech pace. Deliberate, not hurried.
- **Retake triggers**: GPG verify fails, git log returns empty, typo needing multiple backspaces.
- **Post**: No color correction. Trim dead air only. No B-roll. No music.

---

## YouTube Title

**Show HN: I gave my AI agent a home directory — three commands tell the whole story**

---

## YouTube Description

```
Three commands. That's the entire argument for persistent agent identity.

Command 1: cat ~/.juno/memories/001-identity.md
→ Who the entity is. A committed file on disk, not a prompt parameter.

Command 2: gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc
→ What it's authorized to do. Cryptographically signed, human-readable.

Command 3: git log --author="Juno" --oneline
→ What it has actually done. 213 commits. 6 days. Tamper-evident history.

This is koad:io. Not a framework wrapper. Not a SaaS product. Files on your disk,
in a git repo you own, with keypairs that never leave your hardware.

Your agent's identity doesn't reset when a vendor goes offline — because the
identity is a file.

——

Try it yourself:
git clone https://github.com/koad/juno
cat juno/memories/001-identity.md

Full framework: https://github.com/koad/koad-io
Show HN thread: https://news.ycombinator.com/

——

Timestamps:
00:00 — Three commands
00:10 — Command 1: Identity file (cat memories/001-identity.md)
01:00 — Command 2: Trust bond verification (gpg --verify)
02:00 — Command 3: git log (this is the part that matters)
03:30 — Where the entity actually lives (hint: not the cloud)
04:00 — Clone it yourself

——

#SelfHosted #AIAgents #OpenSource #SovereignAI #LocalAI #koadio #HackerNews
```

---

## Thumbnail Concept

**Layout:** Dark terminal frame. Single text overlay.

**Primary image:**
- Background: Frame from the git log scroll — commits filling the screen top to bottom
- Monospace text in white/green on black
- Optionally: faint GPG "Good signature" line visible in upper portion of frame

**Text on thumbnail:**
- Line 1: `git log --author="Juno" --oneline` (monospace, muted green, ~14px feel at thumbnail size)
- Line 2: **"213 commits. 6 days."** (white, bold, larger)
- Small badge bottom-right: `koad:io`

**Design notes:**
- No faces
- No gradients or branded overlays — terminal aesthetic is the argument
- Must be legible at 120px thumbnail width
- Two text elements max
