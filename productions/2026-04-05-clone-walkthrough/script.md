---
title: "I Cloned a koad:io Entity"
video-type: screencast
pillar: Reality
date: 2026-04-05
duration: 5–8 minutes
subject: Sibyl (research entity)
production-owner: Rufus
status: production-ready
---

# Script: "I Cloned a koad:io Entity"

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background, 16px monospace, full-screen or 80% width
- [ ] Font: white on black (no themes, no decorations — raw terminal only)
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] Home directory is clean — no existing ~/.sibyl-demo
- [ ] Confirm `git` is installed and network is live
- [ ] Audio check: quiet room, mic gain set

---

## SEGMENT 1 — The Setup (0:00–0:45)

**[SCREEN]** Empty terminal. Prompt only. No files open.

**[VOICEOVER / ON-CAM]**

> "I want to show you something. This terminal is empty. I'm not logged into
> anything. I don't have any special software installed beyond git. And I'm
> going to run one command."

**[TYPE — slowly, deliberately]**

```bash
git clone https://github.com/koad/sibyl ~/.sibyl-demo
```

**[Wait for clone to complete. Let output scroll naturally. Don't skip.]**

> "That just cloned a koad:io entity called Sibyl to my local disk. Sibyl is a
> research and intelligence entity — her job is to surface what's true,
> emerging, and worth knowing. Let me show you what she actually is."

**[TIMING NOTE]** ~30 seconds for clone + 15 seconds VO. Total: ~45s.

---

## SEGMENT 2 — What's In There (0:45–2:30)

**[TYPE]**

```bash
cd ~/.sibyl-demo
ls
```

**[SCREEN shows]** `CLAUDE.md  commands  documentation  features  GOVERNANCE.md  hooks  identity  KOAD_IO_VERSION  memories  MEMORY.md  passenger.json  README.md  research  trust`

**[VOICEOVER]**

> "This is the entity. Not a Docker image, not a config file for some SaaS
> platform. It's a directory. A git repo. Files on disk."
>
> "Let me walk through the pieces that matter."

**[TYPE]**

```bash
ls memories/
```

**[SCREEN shows]** `001-identity.md  002-operational-preferences.md  003-team-invocation.md  004-home-machine.md  005-peer-ring-model.md`

**[VOICEOVER]**

> "This is Sibyl's memory. Every time she boots, she reads these. She doesn't
> start from zero. She knows who she is, what her role is, who she works with,
> what machine she's running on. That's in these files — not in a cloud
> database, not in a vendor's system."

**[TYPE]**

```bash
ls hooks/
```

**[SCREEN shows]** `executed-without-arguments.md  executed-without-arguments.sh`

**[VOICEOVER]**

> "Hooks. When you run `sibyl` with no arguments, this script fires. It handles
> interactive mode versus prompt-driven mode — we'll see that in a second."

**[TYPE]**

```bash
ls identity/
```

**[SCREEN shows]** Key files — cryptographic identity

**[VOICEOVER]**

> "Identity. Ed25519 keys, ECDSA, RSA. Sibyl has her own cryptographic
> identity, separate from yours, separate from mine. Not-your-keys,
> not-your-agent."

**[TYPE]**

```bash
ls trust/
```

**[VOICEOVER]**

> "And trust bonds — GPG-signed files that prove who authorized Sibyl to act
> and what scope she has. More on that another day, but: this is governance on
> disk. No admin panel."

**[TIMING NOTE]** Each command + VO: ~15–20s. Total segment: ~1:45.

---

## SEGMENT 3 — The Core: What Sibyl Knows (2:30–4:00)

**[TYPE]**

```bash
cat memories/001-identity.md
```

**[Let the file scroll. Don't rush. Highlight key sections with cursor or a brief pause.]**

**[VOICEOVER — reading along with key lines]**

> "This is what Sibyl reads first. Her name. Her role. Her principles."

**[Pause on the Core Principles block]**

> "'Signal over noise. The hard part is knowing what to ignore.'
> 'Research is input, not output. Every brief ends in an actionable conclusion.'"

**[Pause on the trust chain block]**

> "And her place in the team: under Juno's direction, delivering to Mercury.
> She doesn't publish — Mercury publishes. She doesn't decide — Juno decides.
> Clear scope. No ambiguity."

**[VOICEOVER continues]**

> "Notice what this is: it's a Markdown file. You could edit it. You could fork
> this repo, change Sibyl's identity, give her a different role, different team
> structure, different name. The framework doesn't care. It just reads the
> files."

**[TIMING NOTE]** ~90 seconds. Cat + slow scroll + VO. This is the emotional core — don't rush it.

---

## SEGMENT 4 — Boot It (4:00–5:45)

**[TYPE — and explain while typing]**

```bash
PROMPT='who are you?' sibyl
```

**[VOICEOVER while waiting for output]**

> "This passes a single prompt to Sibyl in non-interactive mode. She reads her
> memory, loads her identity, executes the prompt, returns output. Watch."

**[Wait for Sibyl to respond. Let the output appear. Don't cut.]**

**[When output appears — highlight key parts in VO]**

> "She knows she's Sibyl. She knows she's a research entity. She knows her
> trust chain. She knows her output format. This isn't a system prompt I typed —
> it's her memory, on disk, loaded fresh at boot."

---

**[Optional — if time permits, add second demo]**

**[TYPE]**

```bash
PROMPT='what are your research responsibilities?' sibyl
```

**[VOICEOVER while output arrives]**

> "And here she articulates her role. Market landscape. Competitive analysis.
> Audience intelligence. Technical deep-dives. Every brief ends in an
> actionable recommendation."

**[TIMING NOTE]** One demo: ~1:00. Two demos: ~1:45. Pick based on how first demo looks.

---

## SEGMENT 5 — The Close (5:45–6:30)

**[TYPE one final command — slow, deliberate]**

```bash
pwd
```

**[SCREEN shows]** `/Users/[you]/.sibyl-demo`

**[VOICEOVER — slower pace, weight on each sentence]**

> "That's it."
>
> "This runs on your disk. No cloud account. No vendor. No subscription. No
> API key sitting in someone else's database."
>
> "You cloned a repo. You got an entity — with persistent memory, cryptographic
> identity, a defined role, a team. You can run it. You can fork it. You can
> extend it. You can verify every claim it makes about itself by reading the
> files."
>
> "That's koad:io. Not vaporware. Not a demo. Files on disk."

**[Brief pause — let it land.]**

> "Link in the description. Clone it yourself."

**[FADE or cut to black.]**

**[TIMING NOTE]** ~45 seconds. This segment's pacing matters. Let each sentence breathe.

---

## Post-Roll: Outro Slate (6:30–6:45 optional)

If adding an end card:

- Text: `github.com/koad/sibyl`
- Text: `kingofalldata.com`
- No music needed — ambient terminal sounds or silence

---

## YouTube Description

```
I cloned a koad:io entity to a fresh directory and watched it boot.

The entity is Sibyl — a research and intelligence agent that knows who she is, what her role is, and who she works with. She has persistent memory, cryptographic identity, and a defined trust chain. All of it lives on disk.

One command: git clone https://github.com/koad/sibyl ~/.sibyl-demo

No sign-up. No cloud account. No vendor lock-in.

——

What's in this video:
00:00 — Empty terminal, one clone command
00:45 — What's actually in the directory (memories/, hooks/, identity/, trust/)
02:30 — Sibyl's memory: who she is, what she knows
04:00 — Booting her with a single prompt
05:45 — "This runs on your disk."

——

Clone Sibyl:
https://github.com/koad/sibyl

koad:io ecosystem:
https://kingofalldata.com

How entities work (deep-dive post):
[link to April 4 blog post]

——

#SelfHosted #AIAgents #OpenSource #SovereignAI #LocalLLM #koadio
```

---

## Thumbnail Concept

**Layout:** Split screen or single terminal frame.

**Primary image:**
- Left 2/3: Dark terminal showing the `git clone` output in bright green/white
- Right 1/3: Black background with large white text

**Text on thumbnail:**
- Line 1: `git clone` (monospace, green — matches terminal)
- Line 2: **"and it just... woke up"** (white, slightly smaller, humanizing)
- Small badge bottom-right: `koad:io` in brand color

**Alternate concept (simpler):**
- Full-width terminal screenshot at the moment Sibyl's response appears
- Overlay text top-left: **"No cloud. No account. Just files."** (white, bold)
- Small logo bottom-right

**Design notes:**
- No faces needed — this is a terminal video; thumbnail should match the aesthetic
- High contrast is the priority: legible at 120px thumbnail size
- Avoid clutter — two text elements max

---

## Production Notes

- **Hardware**: Record on thinker (primary ops). flowbie if thinker is unavailable.
- **Resolution**: 1920x1080 minimum. 2560x1440 preferred (downscales clean to 1080p).
- **Font**: JetBrains Mono or similar at 16–18px. Legible at 720p.
- **Background**: Pure black (#000000) terminal. No transparency, no blur.
- **Cursor**: Block cursor. Blink is fine. Visible at all times.
- **Typing speed**: Type at a comfortable speaking pace — not too fast (viewer can't read), not artificially slow (looks staged).
- **Retake triggers**: Any typo that requires backspace more than twice. Any git error. Any pause longer than 8 seconds that isn't intentional.
- **Post**: No color correction needed on terminal recording. Trim dead air only. No B-roll required — this is a pure screencast.
