---
title: "Shot List — I Cloned a koad:io Entity"
video: 2026-04-05-clone-walkthrough
production-owner: Rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: "I Cloned a koad:io Entity"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg, white text
- [ ] Font: JetBrains Mono (or Fira Code / Hack) at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `~$` only. No git decorations, no powerline
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] Confirm `~/.sibyl-demo` does NOT exist: `ls ~/.sibyl-demo 2>&1`
- [ ] Confirm git installed and GitHub reachable: `git --version && ping -c1 github.com`
- [ ] `sibyl` command on PATH and working (test on separate terminal)
- [ ] OBS (or screen recorder) armed: resolution 1920x1080 or 2560x1440, 60fps preferred
- [ ] Mic check: quiet room, gain test with a sentence or two
- [ ] Scrollback buffer: large (10,000+ lines) so nothing disappears mid-take

---

## Shot 1: The Empty Terminal

**Segment:** SEGMENT 1 (0:00–0:10)
**Duration:** ~10 seconds

**What camera/screen shows:**
- Terminal window, nothing but the shell prompt
- Cursor blinking

**What to type:** Nothing yet
**What to say:**
> "This terminal is empty. I'm not logged into anything. I'm going to run one command."

**Technical notes:**
- Pause 2–3 seconds after opening before speaking — gives editor a clean cut point
- No split screen here. Full terminal only.

---

## Shot 2: The Clone

**Segment:** SEGMENT 1 (0:10–0:45)
**Duration:** ~35 seconds (includes clone output)

**What to type:**
```
git clone https://github.com/koad/sibyl ~/.sibyl-demo
```

**Expected output:**
```
Cloning into '/Users/[you]/.sibyl-demo'...
remote: Enumerating objects: ...
remote: Counting objects: ...
remote: Compressing objects: ...
Receiving objects: 100% (...), done.
Resolving deltas: 100% (...), done.
```

**What to say (while clone runs):**
> "That's it. One command. That cloned Sibyl — a koad:io research entity — to my local disk."

**Technical notes:**
- Type at normal speech pace — deliberate, not rushed
- Let all output scroll naturally. Do NOT cut during git output.
- If clone fails (network hiccup): stop recording, clear terminal, retry
- Retake trigger: any typo requiring more than one backspace

---

## Shot 3: Enter the Directory — ls

**Segment:** SEGMENT 2 (0:45–1:05)
**Duration:** ~20 seconds

**What to type:**
```
cd ~/.sibyl-demo
ls
```

**Expected output:**
```
CLAUDE.md       GOVERNANCE.md  KOAD_IO_VERSION  MEMORY.md      README.md  features  identity  memories     research
commands        documentation  hooks             passenger.json  trust
```
*(exact layout depends on terminal width — acceptable either way)*

**What to say:**
> "This is the entity. A directory. A git repo. Files on disk. Let me show you what matters."

**Technical notes:**
- Short pause after `ls` output before speaking — let viewer read the listing
- Speak while viewer is reading, not before

---

## Shot 4: Memories Directory

**Segment:** SEGMENT 2 (1:05–1:25)
**Duration:** ~20 seconds

**What to type:**
```
ls memories/
```

**Expected output:**
```
001-identity.md  002-operational-preferences.md  003-team-invocation.md  004-home-machine.md  005-peer-ring-model.md
```

**What to say:**
> "Sibyl's memory. She reads these every time she boots. She knows who she is, what her role is, who she works with. Not in a cloud database — in these files."

**Technical notes:**
- Linger on this output for 2–3 seconds before moving on

---

## Shot 5: Hooks Directory

**Segment:** SEGMENT 2 (1:25–1:40)
**Duration:** ~15 seconds

**What to type:**
```
ls hooks/
```

**Expected output:**
```
executed-without-arguments.md  executed-without-arguments.sh
```

**What to say:**
> "Hooks. This script fires when you run `sibyl` with no arguments — routes you into an interactive session or single-prompt mode."

---

## Shot 6: Identity Directory

**Segment:** SEGMENT 2 (1:40–1:55)
**Duration:** ~15 seconds

**What to type:**
```
ls identity/
```

**What to say:**
> "Cryptographic identity. Sibyl has her own keys — Ed25519, ECDSA. Not tied to your account. Her own sovereign identity."

---

## Shot 7: Trust Directory

**Segment:** SEGMENT 2 (1:55–2:15)
**Duration:** ~20 seconds

**What to type:**
```
ls trust/
```

**What to say:**
> "Trust bonds. GPG-signed authorization files. Who can Sibyl act for, and with what scope. Governance on disk — no admin panel, no dashboard."

**Technical notes:**
- End of the directory tour. Brief natural pause before moving to memory cat.

---

## Shot 8: Cat the Identity Memory

**Segment:** SEGMENT 3 (2:30–4:00)
**Duration:** ~90 seconds — this is the emotional center

**What to type:**
```
cat memories/001-identity.md
```

**Expected output:** Full content of 001-identity.md (known — approximately 50–60 lines)

**What to say (reading along, pacing with the scroll):**

As file begins to show:
> "This is what she reads first."

On the Core Principles block (`Signal over noise...`):
> "Signal over noise. The hard part is knowing what to ignore. Research is input, not output."

On the Trust Chain block:
> "Her place in the team: under Juno, delivering to Mercury. Clear scope. She doesn't publish, doesn't decide — she researches."

After file finishes scrolling:
> "This is a Markdown file. You can edit it. Fork this repo, change her identity, give her a different role. The framework doesn't care. It reads the files."

**Technical notes:**
- **This is the most important shot.** Do not rush the scroll.
- If the file is long, let it scroll — don't pipe to `head`. Full file is the point.
- Optional: add a slow manual scroll-pause after the file displays, to let viewer absorb
- If voiceover feels rushed: pause the cat output is not possible — consider a second take with slower, more deliberate delivery

---

## Shot 9: First Prompt — Who Are You?

**Segment:** SEGMENT 4 (4:00–5:00)
**Duration:** ~60 seconds (includes entity boot and response)

**What to type:**
```
PROMPT='who are you?' sibyl
```

**What to say while waiting for response:**
> "Prompt-driven mode. Sibyl reads her memory, loads her identity, executes the question, returns output."

**When response appears — highlight these points in VO:**
- Entity names herself
- States her role accurately (research, intelligence)
- Mentions her trust chain or team position
- Output format matches what 001-identity.md promised

**What to say after response:**
> "She knows she's Sibyl. She knows her role. That's not a system prompt I typed — that's her memory, on disk, loaded at boot."

**Technical notes:**
- Response time depends on model/hardware — accept natural latency, don't cut
- If Sibyl fails to boot: stop, diagnose in a separate terminal, retry when resolved
- Retake trigger: entity gives generic response not grounded in her memory

---

## Shot 10: Optional Second Prompt

**Segment:** SEGMENT 4 (5:00–5:30)
**Duration:** ~30 seconds

**Include if:** First demo is clean and total runtime is under 5:30.

**What to type:**
```
PROMPT='what are your research responsibilities?' sibyl
```

**What to say while waiting:**
> "Let's give her a scope question."

**When response appears:**
> "Market landscape, competitive analysis, audience intelligence, technical deep-dives. Every brief ends in an actionable recommendation. She's not just summarizing — she's prescribing."

---

## Shot 11: The Close — pwd

**Segment:** SEGMENT 5 (5:45–6:30)
**Duration:** ~45 seconds

**What to type:**
```
pwd
```

**Expected output:**
```
/Users/[you]/.sibyl-demo
```

**What to say — slow down here, let each sentence land:**
> "That's it."

*(pause)*

> "This runs on your disk. No cloud account. No vendor. No subscription."

*(pause)*

> "You cloned a repo. You got an entity — with memory, identity, a role, a team."

*(pause)*

> "Run it. Fork it. Extend it. Verify every claim by reading the files."

*(pause)*

> "That's koad:io. Not vaporware. Files on disk."

*(pause)*

> "Link in the description. Clone it yourself."

**Technical notes:**
- **Slowest pacing in the video.** Do not rush.
- Each sentence = one breath. Pause between sentences is intentional — not dead air.
- Editor: do NOT cut these pauses. They are part of the tone.

---

## Shot 12: Fade / Cut to Black

**Duration:** 2–3 seconds

- No music needed
- No end screen animation
- Simple cut to black or 1-second fade
- Optional: hold on the terminal with the `pwd` output for 1 extra second before fade

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| After Shot 1 | Clean cut — no gap needed |
| During Shot 2 (git clone) | Do NOT cut git output. Full scroll must show. |
| Shot 8 (cat memories) | Do NOT speed up. This is the core. |
| Shot 9 (PROMPT=...) | Accept natural latency. Do not cut waiting time to < 3s. |
| Shot 11 (close) | Do NOT cut pauses between sentences. Intentional. |

**Cuts to remove:**
- Any backspace or typo correction (retake if > 1 backspace)
- Any pause > 8 seconds outside of intentional beats
- Any window/focus switch

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp except: short segments of `ls` commands may be trimmed by up to 30% if there is excessive dead air between command and VO

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `git clone` fails (network) | Kill recording. Check network. Retry from Shot 1. |
| `sibyl` command not found | Kill recording. Fix PATH/install. Do not patch on camera. |
| Sibyl gives generic/broken response | Kill recording. Check Sibyl config. Retry Shot 9 from that segment (or full retake if flow is broken). |
| flowbie unavailable | Record from thinker. Same instructions apply. |
| Take goes > 8 minutes | Trim Shot 10 (optional prompt) and/or tighten Shot 2 VO. |

---

## Final Deliverables from This Session

- [ ] Raw recording: `2026-04-05-clone-raw.mp4` (unedited, full take)
- [ ] Edited cut: `2026-04-05-clone-final.mp4` (5–8 min, trimmed per notes above)
- [ ] Thumbnail: `2026-04-05-clone-thumb.png` (1280x720, see script.md for concept)
- [ ] Captions: auto-generated + manually reviewed
- [ ] Upload-ready: title, description, tags from script.md applied before hand-off to Mercury
