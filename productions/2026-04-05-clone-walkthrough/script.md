---
title: "I Cloned a koad:io Entity"
video-type: screencast
pillar: Reality
date: 2026-04-05
duration: 5–8 minutes
subject: Chiron (curriculum architect entity)
production-owner: Rufus
status: production-ready
---

# Script: "I Cloned a koad:io Entity"

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background, 16px monospace, full-screen or 80% width
- [ ] Font: white on black (no themes, no decorations — raw terminal only)
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] Home directory is clean — no existing ~/.chiron-demo
- [ ] Confirm `git` is installed and network is live
- [ ] Audio check: quiet room, mic gain set

---

## SEGMENT 1 — The Setup (0:00–0:45)

**[SCREEN]** Empty terminal. Prompt only. No files open.

**[VOICEOVER]**

> "I want to show you something. This terminal is empty. I'm not logged into
> anything. I don't have any special software installed beyond git. And I'm
> going to run one command."

**[TYPE — slowly, deliberately]**

```bash
git clone https://github.com/koad/chiron ~/.chiron-demo
```

**[Wait for clone to complete. Let output scroll naturally. Don't skip.]**

> "That just cloned a koad:io entity called Chiron to my local disk. Chiron is
> the curriculum architect for this ecosystem — he designed the onboarding
> curriculum that Alice delivers to humans. Let me show you what he actually
> is."

**[TIMING NOTE]** ~30 seconds for clone + 15 seconds VO. Total: ~45s.

---

## SEGMENT 2 — What's In There (0:45–2:00)

**[TYPE]**

```bash
cd ~/.chiron-demo
ls
```

**[SCREEN shows]** Top-level directory listing — CLAUDE.md, README.md, memories/, hooks/, commands/, curricula/, id/, trust/, etc.

**[VOICEOVER]**

> "This is the entity. Not a Docker image, not a config file for some SaaS
> platform. It's a directory. A git repo. Files on disk."

---

**[TYPE]**

```bash
cat README.md
```

**[Let it scroll — don't rush. File is ~40 lines.]**

**[VOICEOVER — reading the key lines]**

> "Chiron. Named for the centaur who taught Achilles, Jason, Heracles. The
> archetype of the learned teacher."
>
> "He owns the curriculum architecture standard. He authors the learning paths
> that Alice delivers. He has a specific scope — he doesn't build software,
> doesn't publish — he writes the curriculum."

---

**[TYPE]**

```bash
cat CLAUDE.md
```

**[Let the first 40–50 lines scroll. Don't rush.]**

**[VOICEOVER — pick up the key identity block]**

> "CLAUDE.md is the entity brief. Every session, the AI reads this. It's not
> a prompt I type — it's the file that tells the model who it is before it
> does anything."
>
> "Two-layer architecture: the koad:io framework handles the runtime, and this
> directory — Chiron's entity layer — handles the identity. The framework
> doesn't care which entity it's loading. It reads the files."

**[TIMING NOTE]** Segment 2 is the structural tour. ~75 seconds.

---

## SEGMENT 3 — The Hook (2:00–2:45)

**[TYPE]**

```bash
cat hooks/executed-without-arguments.sh
```

**[Let the hook script display. It's ~30 lines. Let it scroll.]**

**[VOICEOVER — reading the key logic]**

> "This hook is what runs when you invoke `chiron` with no arguments. No
> special config needed — you call the entity name, the framework finds this
> script and runs it."
>
> "Look at the branching logic: if you passed a PROMPT — single-shot mode. If
> you didn't — it drops you into an interactive session. One hook, two modes."
>
> "There's also a PID lock here. If Chiron is already running, you get a
> message: he's busy. Try again shortly. This is an entity that can run
> autonomously — it needs to know when it's already working."

**[TIMING NOTE]** ~45 seconds. This is the most technical segment — keep VO grounded and plain-language.

---

## SEGMENT 4 — Boot It (2:45–4:30)

**[TYPE — and explain while typing]**

```bash
PROMPT='what is your role?' chiron
```

**[VOICEOVER while waiting for output]**

> "Prompt-driven mode. Chiron reads his memory, loads his identity from
> CLAUDE.md, executes the question, returns output. Watch."

**[Wait for Chiron to respond. Let the output appear. Don't cut.]**

**[When output appears — highlight key parts in VO]**

> "He knows he's Chiron. He knows his role is curriculum architect, not
> librarian, not professor — teacher. He knows what he owns and what he
> doesn't. That's not me typing a system prompt — that's his memory, on
> disk, loaded at boot."

**[TIMING NOTE]** Response time depends on model/hardware. Accept natural latency. Don't cut.

---

## SEGMENT 5 — The Close (4:30–5:15)

**[TYPE one final command — slow, deliberate]**

```bash
pwd
```

**[SCREEN shows]** `/home/[you]/.chiron-demo`

**[VOICEOVER — slower pace, weight on each sentence]**

> "That's it."

*(pause)*

> "This runs on your disk. No cloud account. No vendor. No subscription. No
> API key sitting in someone else's database."

*(pause)*

> "You cloned a repo. You got an entity — with persistent memory, its own
> identity, a defined role, a team it knows, a scope it doesn't exceed."

*(pause)*

> "You can run it. You can fork it. You can edit the memory files and rebuild
> what it knows. You can verify every claim it makes about itself by reading
> the files."

*(pause)*

> "That's koad:io. Not vaporware. Not a demo. Files on disk."

*(pause — let it land.)*

> "Link in the description. Clone it yourself."

**[FADE or cut to black.]**

**[TIMING NOTE]** ~45 seconds. This segment's pacing matters most. Let each sentence breathe.

---

## Post-Roll: Outro Slate (optional, 5:15–5:30)

If adding an end card:

- Text: `github.com/koad/chiron`
- Text: `kingofalldata.com`
- No music needed — silence or ambient terminal

---

## YouTube Title

**I Cloned a koad:io Entity (and it knew exactly who it was)**

---

## YouTube Description

```
I cloned a koad:io entity to a fresh directory and watched it boot.

The entity is Chiron — a curriculum architect who knows his role, his scope,
his team, and his constraints. He has persistent memory, his own identity files,
and a hook that handles both interactive and single-prompt modes.

One command: git clone https://github.com/koad/chiron ~/.chiron-demo

No sign-up. No cloud account. No vendor lock-in.

——

What's in this video:
00:00 — Empty terminal, one clone command
00:45 — What's actually in the directory (README.md, CLAUDE.md)
02:00 — The hook that runs when you invoke the entity
02:45 — Booting Chiron with a single prompt
04:30 — "This runs on your disk."

——

Clone Chiron:
https://github.com/koad/chiron

koad:io ecosystem:
https://kingofalldata.com

——

#SelfHosted #AIAgents #OpenSource #SovereignAI #LocalLLM #koadio
```

---

## Thumbnail Concept

**Layout:** Dark terminal frame with two text elements.

**Primary image:**
- Background: Terminal at the moment Chiron's response appears — entity text visible
- Left edge: faint git clone output in green/white

**Text on thumbnail:**
- Line 1: `git clone github.com/koad/chiron` (monospace, muted green)
- Line 2: **"and it knew exactly who it was"** (white, slightly smaller)
- Small badge bottom-right: `koad:io`

**Design notes:**
- No faces — terminal aesthetic is the argument
- High contrast: legible at 120px thumbnail size
- Two text elements max

---

## Production Notes

- **Hardware**: Record on thinker (primary ops). flowbie if thinker is unavailable.
- **Resolution**: 1920x1080 minimum. 2560x1440 preferred.
- **Font**: JetBrains Mono or similar at 16–18px. Legible at 720p.
- **Background**: Pure black (#000000). No transparency, no blur.
- **Cursor**: Block cursor. Visible at all times.
- **Typing speed**: Comfortable speaking pace — not fast enough that viewers can't follow, not so slow it looks staged.
- **Retake triggers**: Any typo requiring more than one backspace. Any git error. Any pause > 8 seconds outside of intentional beats.
- **Post**: No color correction. Trim dead air only. No B-roll.
