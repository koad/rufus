---
title: "The $200 Laptop Experiment"
video-type: terminal-capture
tier: 3
pillar: Reality
series: "2-Week Reality Proof"
day: 7
date: 2026-04-07
duration: 7–10 minutes
hardware: thinker
production-owner: Rufus
status: production-ready
---

# Script: "The $200 Laptop Experiment"

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background (#000000), 16px+ monospace, fullscreen
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] Confirm `neofetch` or `inxi` is installed and returns clean output
- [ ] Confirm `~/.juno` is up to date: `cd ~/.juno && git pull`
- [ ] Confirm SSH to fourty4 works: `ssh fourty4 echo ok`
- [ ] Audio check: quiet room, mic gain set
- [ ] asciinema armed: `asciinema rec --title "..." --idle-time-limit 2 ~/.rufus/recordings/2026-04-07-200-dollar-laptop-raw.cast`

---

## SEGMENT 1 — Cold Open: The Machine (0:00–1:00)

**[SCREEN]** Empty terminal. Cursor blinking. Nothing else.

**[VOICEOVER]**

> "Seven days ago, koad:io's first operation started on this machine."

**[TYPE — slowly]**

```bash
neofetch
```

**[Wait for neofetch output. Let it render fully. The specs are the point.]**

**[VOICEOVER — reading the specs as they appear]**

> "This is thinker. A refurbished laptop. You can see the specs."

**[Pause on the memory and CPU lines]**

> "Not a cloud VM. Not a workstation with a GPU. A commodity machine — the kind
> you buy used when you're not sure you need anything better."

**[Continue]**

> "Today is Day 7. The experiment has a result."

**[TIMING NOTE]** ~45 seconds for neofetch + VO. Brief pause before next segment.

---

## SEGMENT 2 — The Argument (1:00–2:30)

**[SCREEN]** Terminal, prompt only.

**[VOICEOVER — no typing yet]**

> "Here's what most people assume about AI infrastructure: capability lives
> with resources. More compute, better results. Cloud providers sell this.
> You pay for their GPUs, their memory, their redundancy."

> "koad:io was built on the opposite assumption."

**[TYPE — slowly, let viewer read it]**

```bash
echo "The entity is the directory."
```

**[Wait for the echo to print. Brief pause.]**

**[VOICEOVER]**

> "The entity is the directory. The model is just the reasoning engine that
> reads the directory. Sovereignty — the ability to own, control, fork,
> revert, survive vendor changes — lives entirely in the files."

**[TYPE]**

```bash
ls ~/.juno/
```

**[Let the listing appear.]**

**[VOICEOVER]**

> "That's Juno. An AI business orchestrator. CLAUDE.md tells her who she
> is. memories/ holds her context. trust/ holds her authorization bonds.
> commands/ holds her skills. All of it: files on disk. git repo."

**[TYPE]**

```bash
du -sh ~/.juno/
```

**[Wait for output]**

**[VOICEOVER]**

> "If that's true — if sovereignty lives in the files — then any machine
> that can run git and SSH is sufficient. You don't need the cloud.
> You don't need expensive hardware."

> "That was the bet. Seven days of production work to test it."

**[TIMING NOTE]** ~1:30. This is the thesis — let it breathe.

---

## SEGMENT 3 — What the Hardware Actually Does (2:30–4:30)

**[SCREEN]** Terminal, prompt.

**[VOICEOVER]**

> "When you run an entity command from thinker, here's what actually happens."

**[TYPE]**

```bash
cat ~/.juno/hooks/executed-without-arguments.sh
```

**[Wait for the file to display. Let it scroll.]**

**[VOICEOVER — narrating the key steps as they appear in the code]**

> "This is thinker's job. The hook reads the prompt. Base64-encodes it.
> SSHes to fourty4 — the Mac Mini. fourty4 starts a Claude Code session."

**[Pause at the SSH line in the code]**

> "The inference happens on fourty4. thinker's contribution: run a shell
> script and establish an SSH connection."

**[After the file finishes]**

> "That's it. That's thinker's job in every entity invocation."

**[TYPE]**

```bash
ssh fourty4 echo "fourty4 is up"
```

**[Wait for the response]**

**[VOICEOVER]**

> "fourty4 is always on. It's a Mac Mini — roughly $400, one-time. It's
> doing the Claude API calls. But that's not GPU inference either — it's
> API calls over the network. A $50-a-month VPS does the same job."

> "Total infrastructure: thinker, fourty4, flowbie — existing hardware.
> No cloud platform subscriptions. No SaaS fees. No vendor with admin
> access to your entities."

**[TYPE — brief]**

```bash
echo "thinker: \$200 one-time. fourty4: \$400 one-time. Cloud: \$0/month."
```

**[VOICEOVER]**

> "The expensive part isn't hardware. I'll show you what is."

**[TIMING NOTE]** ~2:00. The SSH step is critical — don't cut it.

---

## SEGMENT 4 — The Evidence: Seven Days of Commits (4:30–6:30)

**[SCREEN]** Terminal.

**[VOICEOVER]**

> "Here's what seven days on this machine produced. Not a slide. Commits."

**[TYPE]**

```bash
cd ~/.juno && git log --oneline --since="2026-03-30" --until="2026-04-06"
```

**[Wait for log to appear. Let it scroll. This is the emotional core — do not rush.]**

**[VOICEOVER — reading key commits as they scroll, at a measured pace]**

> "Juno gestated and pushed to GitHub. Vulcan built Alice Phase 2A — it's
> live on kingofalldata.com right now."

**[Pause as relevant commits scroll]**

> "Faber wrote six posts. Sibyl synthesized a research paper. Chiron
> bootstrapped with a full curriculum spec. Trust bonds signed, committed,
> GPG-verified."

**[Let the rest of the log scroll]**

> "Fifteen entities migrated to fourty4. Hook architecture fixed and
> signed. GitHub Sponsors live. Three-node infrastructure running."

**[After log completes]**

**[TYPE]**

```bash
git log --oneline --since="2026-03-30" --until="2026-04-06" | wc -l
```

**[Wait for count]**

**[VOICEOVER]**

> "These are commits. Auditable. Check the git log yourself if you want
> to verify — it's public at github.com/koad/juno."

**[Pause]**

> "One human. A $200 laptop. A Mac Mini. A team of entities with
> directories on disk."

**[TIMING NOTE]** ~2:00. Speak slowly during the log scroll. Each commit line is a data point.

---

## SEGMENT 5 — The Close: Files Don't Age (6:30–7:30)

**[SCREEN]** Terminal, prompt.

**[VOICEOVER — slower pace, weight on each sentence]**

> "Here's what Day 7 actually demonstrates."

**[TYPE]**

```bash
cat ~/.juno/memories/001-identity.md | head -20
```

**[Let the first 20 lines of Juno's identity memory appear]**

**[VOICEOVER]**

> "Juno knows who she is at the start of Day 7 the same way she did on
> Day 1. Same CLAUDE.md. Same memories committed to git. Same trust bonds."

**[Pause]**

> "There's no session state to expire. No persistent process to crash.
> No database to corrupt."

**[TYPE — slow, deliberate]**

```bash
echo "The entity's state is files on disk."
```

**[Wait for it to print]**

**[VOICEOVER]**

> "Files on disk don't age."

**[Pause — let it land]**

> "thinker could fail today. The data survives — it's committed and
> pushed. New machine, git clone, SSH key. The operation continues.
> Not after a migration. Not after a support ticket."

**[TYPE — the final line, slow]**

```bash
git clone https://github.com/koad/juno
```

**[Do NOT wait for it to finish — stop recording at the first line of clone output]**

**[VOICEOVER — over the clone starting]**

> "After git clone."

**[Cut or fade as clone begins.]**

**[TIMING NOTE]** ~60 seconds. Slowest segment. Every pause is intentional — editor keeps them.

---

## Post-Roll: Outro Slate (7:30–8:00 optional)

If adding end card:

- Text: `github.com/koad/juno`
- Text: `kingofalldata.com`
- Text: `Day 7 of the 2-Week Reality Proof`
- No music — silence or ambient terminal

---

## YouTube Metadata

### Title (pick one)

**Primary:**
> The $200 Laptop Experiment — 7 Days of Sovereign AI Operations

**Alternate:**
> I Ran a 15-Entity AI Team From a $200 Laptop For 7 Days

### Description

```
Seven days ago, koad:io's first operation started on a $200 refurbished laptop.

Not a demo. Not a proof of concept. Production work: entity gestation, trust bonds signed, Vulcan building and shipping real code, content written, research synthesized, infrastructure wired across three nodes.

Day 7 is the result.

This video shows thinker's actual specs, walks through what happens when an entity is invoked (the SSH dispatch chain), shows the git log of what shipped, and ends on the architectural property that makes any of this viable: files on disk don't age.

——

What's in this video:
00:00 — thinker's specs (the actual $200 laptop)
01:00 — The argument: sovereignty is a software property
02:30 — What the hardware actually does (the hook, the SSH dispatch chain)
04:30 — Seven days of commits (the git log is auditable)
06:30 — "Files don't age"

——

The git log:
https://github.com/koad/juno

koad:io framework:
https://kingofalldata.com

The post this video is based on:
[link to Faber's Day 7 post]

——

#SovereignAI #SelfHosted #AIAgents #koadio #LocalLLM #Linux
```

### Tags

```
sovereign AI, self-hosted AI, AI agents, koad:io, git, terminal, $200 laptop, AI infrastructure, files on disk, entity, autonomous agents
```

---

## Thumbnail Concept

**Primary concept:**

- Left 60%: Terminal screenshot showing `neofetch` output with thinker's actual (modest) specs
- Right 40%: Black background, large white text

**Text overlay:**
- Line 1: `$200 laptop` (monospace green — matches terminal)
- Line 2: **"7 days. 15 entities."** (white, bold)
- Small badge bottom-right: `koad:io`

**Alternate concept (if neofetch is visually cluttered):**

- Full-width terminal screenshot at the git log moment — commits filling the screen
- Overlay top-left: **"7 days of production on a $200 laptop"** (white, bold)
- Logo bottom-right

**Design rules:**
- No faces
- High contrast — legible at 120px
- Two text elements maximum
- Terminal aesthetic throughout — do not break the visual

---

## Production Notes

- **Hardware**: Record on thinker. Non-negotiable — the whole point is that thinker ran the operation.
- **asciinema**: Use `--idle-time-limit 2` to collapse long API wait times without looking edited.
- **SSH to fourty4**: If fourty4 is down, reschedule. Do not simulate the SSH step.
- **git log**: Run the actual log from `~/.juno`. Do not construct a fake log or trim it.
- **Retake triggers**: Any typo requiring multiple backspaces; any SSH failure; any moment that looks staged or rehearsed in a way that undermines the "this is real" claim.
- **Pacing**: Segment 5 is the close. If it feels rushed on playback, re-record Segment 5 only.
