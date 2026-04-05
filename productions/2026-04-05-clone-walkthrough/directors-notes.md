---
title: "Director's Notes — I Cloned a koad:io Entity"
video: 2026-04-05-clone-walkthrough
author: Rufus
date: 2026-04-05
status: production-ready
---

# Director's Notes: "I Cloned a koad:io Entity"

## Why This Video Matters

This is the single-sentence pitch for koad:io: clone a repo, get an entity that knows who it is. Everything else in the ecosystem assumes the audience has seen this happen or can imagine it. This video makes it concrete.

---

## System State at the Start of Recording

Before you hit record, the machine must be in this exact state — not approximately this state:

**What must exist:**
- `chiron` command responds to `PROMPT='test' chiron` in a separate terminal (not the recording terminal)
- `~/.juno` directory is present (you will not use it, but its absence would look wrong in the background)
- GitHub is reachable: `ping -c1 github.com` returns without error

**What must not exist:**
- `~/.chiron-demo` — run `rm -rf ~/.chiron-demo` if it exists from a previous test. Verify: `ls ~/.chiron-demo 2>&1` must show "No such file or directory."

**Window arrangement:**
- One terminal window, fullscreen. Nothing else visible.
- No browser, no file manager, no other terminal tabs visible in the taskbar.
- No notification area items that might pop during recording.
- Shell prompt: bare minimum. If your PS1 shows git branch, hostname, or any color decoration — strip it before recording: `PS1='$ '`
- Font confirmed at 16–18px monospace. Do a test screenshot and zoom in at 720p — if text looks blurry, increase font size before recording.

**Final check command (run this, then immediately start recording):**
```bash
clear && printf '\033[3J' && ls ~/.chiron-demo 2>&1
```
Output should end with "No such file or directory." If it does, you are ready.

---

## The Three Money Shot Moments

### Money Shot 1: The clone output (Shot 2, ~0:10–0:45)

The moment git clone completes and you see "Resolving deltas: 100%, done." is the first proof beat. The viewer has been told you are about to clone an entity. The clone output is the handshake. Do not speed through it. Let every line appear. Speak slowly during the output. When it finishes, pause one full breath before continuing.

**What needs to be visible:** Full git clone output, no truncation. Cloning into, Enumerating objects, Counting, Compressing, Receiving, Resolving deltas — all of it.

### Money Shot 2: Chiron's response to "what is your role?" (Shot 7, ~2:45–4:30)

This is the climax. The entity answers in character — it names itself Chiron, states its role as curriculum architect, describes what it owns and what it doesn't. If the response is generic ("I am an AI assistant"), stop recording immediately — the video has no ending. The response needs to be grounded in the identity files.

**What needs to be visible:** The full response scrolling, ideally with the entity name appearing in the first line. If you are using OBS, resist the urge to zoom. Let the terminal fill the frame. The density of the response is the proof.

**What to say while waiting for response:** Keep it short. "Prompt-driven mode. Watch." Then silence until the response arrives. Don't fill the wait with commentary — the wait itself is the tension.

### Money Shot 3: The pwd close (Shot 8, ~4:30–5:15)

The simplest shot. One command. One line of output. `/home/[you]/.chiron-demo`. The entire video's argument is in that path. This is where you slow down the most. Each sentence of the closing VO is separated by a real pause — not edited pauses, but actual silence you leave in the room.

**What needs to be visible:** Just the pwd output and the blinking cursor. Nothing else. Do not type another command after this.

---

## Fallback Plan If a Demo Command Fails

### If git clone fails (network error)
- Stop recording immediately. Say nothing on camera about the failure.
- In a separate terminal, verify: `ping -c1 github.com` and `curl -I https://github.com`
- If network is the issue: wait, retry, do not proceed until clone works clean.
- Do not show the network debug in the recording terminal.
- Restart from Shot 1 (clear scrollback).

### If chiron command not found on PATH
- Stop recording. Do not try to fix it on camera.
- In a separate terminal: `which chiron` — if not found, check `~/.koad-io/bin` is on PATH.
- Fix in a separate window, confirm working with `PROMPT='test' chiron` before restarting.
- Restart from Shot 1.

### If Chiron gives a generic AI response (not grounded in memory files)
- Stop recording. This is the hardest failure because it happens at the end.
- Check that `~/.chiron` (the real entity, not `~/.chiron-demo`) has its memory files intact.
- The cloned demo might be pulling from a stale or minimal repo. Check `~/.chiron-demo/memories/` — if it is missing files, the entity will have no grounding.
- Do not retry Shot 7 alone — the response needs to be watched in isolation first. Run `PROMPT='what is your role?' chiron` in a test terminal, evaluate the output, then decide if the take is worth running.
- If chiron-demo is consistently ungrounded: record Shot 7 using `~/.chiron` directly by temporarily setting the demo path. Do not announce this on camera.

### If the take runs long (beyond 8 minutes)
- The most likely cause is Shot 5 (cat CLAUDE.md) — CLAUDE.md is long and the VO can expand to fill it.
- Fix: read fewer lines of CLAUDE.md VO. Let the scroll happen, but only comment on two blocks: the two-layer architecture line, and the owns/does-not-own table. Let the rest scroll in silence.
- Do not rush Shot 7 or Shot 8. Those are the shots that matter.

---

## Pacing Guide

| Shot | Pace | Why |
|------|------|-----|
| Shot 1 (empty terminal) | Hold 3 seconds before speaking | Gives editor a clean cut point; lets viewer orient |
| Shot 2 (git clone) | Slow typing, normal speech | Deliberate action communicates confidence |
| Shot 3 (ls) | Brief pause after output | Let viewer read the listing before explaining it |
| Shot 4 (cat README.md) | Medium — let scroll breathe | Full file is the point; don't race through |
| Shot 5 (cat CLAUDE.md) | Medium — only comment on 2 blocks | Longest shot; resist over-explaining |
| Shot 6 (hook) | Slow on each logic block | Technical credibility moment — pause, then speak |
| Shot 7 (PROMPT=...) | SLOWEST — wait in silence | The wait is tension; don't fill it |
| Shot 8 (pwd) | SLOWEST — one sentence per breath | The close lands through pacing, not content |

The single pacing mistake this video is most likely to make: rushing Shot 7 and Shot 8. If you feel the urge to fill silence — don't.

---

## One Sentence Summary

This video matters because it turns "sovereign AI entity" from a claim into a thing you can watch happen in 45 seconds, on a machine you own, with one command.
