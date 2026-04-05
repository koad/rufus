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
- [ ] Confirm `~/.chiron-demo` does NOT exist: `ls ~/.chiron-demo 2>&1`
- [ ] Confirm git installed and GitHub reachable: `git --version && ping -c1 github.com`
- [ ] `chiron` command on PATH and working (test on a separate terminal, not recording terminal)
- [ ] OBS (or screen recorder) armed: 1920x1080 or 2560x1440, 60fps preferred
- [ ] Mic check: quiet room, gain test with a sentence or two
- [ ] Scrollback buffer large (10,000+ lines) so nothing disappears mid-take

---

## Shot 1: The Empty Terminal

**Segment:** SEGMENT 1 (0:00–0:10)
**Duration:** ~10 seconds

**What the screen shows:**
- Terminal window, nothing but the shell prompt
- Cursor blinking

**What to type:** Nothing yet.

**What to say:**
> "This terminal is empty. I'm not logged into anything. I'm going to run one command."

**Technical notes:**
- Pause 2–3 seconds after opening before speaking — gives editor a clean cut point
- No split screen. Full terminal only.

---

## Shot 2: The Clone

**Segment:** SEGMENT 1 (0:10–0:45)
**Duration:** ~35 seconds (includes git output)

**What to type:**
```
git clone https://github.com/koad/chiron ~/.chiron-demo
```

**Expected output:**
```
Cloning into '/home/[you]/.chiron-demo'...
remote: Enumerating objects: ...
remote: Counting objects: ...
remote: Compressing objects: ...
Receiving objects: 100% (...), done.
Resolving deltas: 100% (...), done.
```

**What to say (while clone runs):**
> "That's it. One command. That cloned Chiron — a koad:io curriculum architect
> entity — to my local disk."

**Technical notes:**
- Type at normal speech pace — deliberate, not rushed
- Let all git output scroll naturally. Do NOT cut during git output.
- If clone fails (network): stop recording, check network, retry from Shot 1
- Retake trigger: any typo requiring more than one backspace

---

## Shot 3: Enter the Directory — ls

**Segment:** SEGMENT 2 (0:45–1:05)
**Duration:** ~20 seconds

**What to type:**
```
cd ~/.chiron-demo
ls
```

**Expected output:**
```
CLAUDE.md   README.md    commands    curricula    etc     hooks
id          keybase      memories    positioning  trust
```
*(exact layout depends on terminal width — acceptable either way)*

**What to say:**
> "This is the entity. A directory. A git repo. Files on disk. Let me show you
> what matters."

**Technical notes:**
- Short pause after `ls` output before speaking — let viewer read the listing
- Speak while viewer is reading, not before

---

## Shot 4: Cat README.md

**Segment:** SEGMENT 2 (1:05–1:45)
**Duration:** ~40 seconds

**What to type:**
```
cat README.md
```

**Expected output:** Full README (~40 lines). Includes entity description, role statement, what Chiron owns.

**What to say (reading along with key lines):**

As file begins:
> "Chiron. Named for the centaur who taught Achilles, Jason, Heracles."

On the role block:
> "Curriculum architect. He owns the structure — the learning paths Alice
> delivers to humans."

After file finishes:
> "This is the public identity. Anyone who clones this repo reads exactly this."

**Technical notes:**
- Do not pipe to `head`. Full cat. The full scroll is the point.
- Let file display for 2–3 seconds after it finishes before moving on.

---

## Shot 5: Cat CLAUDE.md

**Segment:** SEGMENT 2 (1:45–2:00)
**Duration:** ~15 seconds setup, then let it scroll

**What to type:**
```
cat CLAUDE.md
```

**Expected output:** Full CLAUDE.md — entity identity, two-layer architecture description, what Chiron owns and does not own, team relationships.

**What to say (reading along with key sections):**

As file begins to scroll:
> "CLAUDE.md. This is what the AI reads at the start of every session. Not a
> system prompt I typed — a file on disk."

On the two-layer architecture block:
> "Framework layer handles the runtime. Entity layer — this directory — handles
> the identity. The framework doesn't care which entity. It reads the files."

On the owns/does-not-own table:
> "Scope. He designs curricula. He doesn't build the software, doesn't publish,
> doesn't do the research — those are other entities. Every entity has hard
> edges."

**Technical notes:**
- CLAUDE.md is long. Let it scroll — don't cut it short. ~60 seconds of scroll is acceptable.
- VO should pace with the scroll, not race ahead of it.
- This is the second most important shot after Shot 7 (the boot). Don't rush.

---

## Shot 6: Cat the Hook

**Segment:** SEGMENT 3 (2:00–2:45)
**Duration:** ~45 seconds

**What to type:**
```
cat hooks/executed-without-arguments.sh
```

**Expected output:** The hook script (~30 lines). Contains:
- LOCKFILE logic (PID-based)
- PROMPT detection (empty vs. set)
- Two branches: `-p "$DECODED"` for prompt mode, `-c` for interactive mode
- base64 encode/decode of the prompt

**What to say (reading the key logic blocks):**

On the PROMPT detection:
> "If you set a PROMPT env variable — single-shot mode. If you didn't — you
> get an interactive session."

On the LOCKFILE block:
> "PID lock. If Chiron is already running, you get a message: he's busy. Try
> again shortly. This is an entity that can run autonomously — it needs to
> protect against concurrent invocations."

On the base64 encode/decode:
> "The prompt is base64-encoded before being passed to the model. Clean
> handling — no shell injection, no quoting issues."

After file ends:
> "One hook. That's the entire invocation layer. Everything else is in the
> entity's identity files."

**Technical notes:**
- This is the most technical segment. Keep VO plain-language throughout.
- Pause on each key block (LOCKFILE, PROMPT branch, base64) before speaking about it — let viewer read first.
- Do not rush to keep runtime short. This earns technical credibility.

---

## Shot 7: First Prompt — What Is Your Role?

**Segment:** SEGMENT 4 (2:45–4:30)
**Duration:** ~90 seconds (includes boot latency and response)

**What to type:**
```
PROMPT='what is your role?' chiron
```

**What to say while waiting for response:**
> "Prompt-driven mode. Chiron reads his memory, loads his identity, executes
> the question, returns output. Watch."

**When response appears — highlight these points in VO:**
- Entity names itself (Chiron)
- States role correctly (curriculum architect / educator)
- Mentions what it owns vs. what other entities own
- Reflects the specific pedagogy from the identity memory (progressive disclosure, knowledge atoms, exit criteria)

**What to say after response:**
> "He knows he's Chiron. He knows his scope. That's not a system prompt I
> typed — that's his memory, on disk, loaded at boot."

**Technical notes:**
- Response time depends on model/hardware. Accept natural latency — do NOT cut the waiting time to under 3 seconds. The wait IS part of the sovereignty proof.
- If Chiron fails to boot: stop, diagnose in a separate terminal, retry when resolved
- Retake trigger: entity gives generic AI response not grounded in its memory files

---

## Shot 8: The Close — pwd

**Segment:** SEGMENT 5 (4:30–5:15)
**Duration:** ~45 seconds

**What to type:**
```
pwd
```

**Expected output:**
```
/home/[you]/.chiron-demo
```

**What to say — slowest pacing in the video. One sentence, one breath, one pause:**

> "That's it."

*(pause — 2 seconds)*

> "This runs on your disk. No cloud account. No vendor. No subscription."

*(pause)*

> "You cloned a repo. You got an entity — with memory, identity, a role, a team."

*(pause)*

> "Run it. Fork it. Extend it. Verify every claim by reading the files."

*(pause)*

> "That's koad:io. Not vaporware. Files on disk."

*(pause — let it land)*

> "Link in the description. Clone it yourself."

**Technical notes:**
- Slowest pacing in the video.
- Each sentence = one breath. Pauses between sentences are intentional beats — not dead air.
- Editor: do NOT cut these pauses. They are structural.

---

## Shot 9: Fade / Cut to Black

**Duration:** 2–3 seconds

- No music
- No end screen animation
- Simple cut to black or 1-second fade
- Optional: hold on the terminal with `pwd` output for 1 extra second before fade

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| After Shot 1 | Clean cut — no gap needed |
| During Shot 2 (git clone) | Do NOT cut git output. Full scroll must show. |
| Shot 5 (cat CLAUDE.md) | Do NOT cut short — full file is the point |
| Shot 6 (hook) | Pause on each logic block before VO; do not rush |
| Shot 7 (PROMPT=...) | Accept natural latency. Do not cut wait time to < 3s. |
| Shot 8 (close) | Do NOT cut pauses. Intentional beats. |

**Cuts to remove:**
- Any backspace or typo correction (retake if > 1 backspace)
- Any pause > 8 seconds outside of intentional beats in Shot 8
- Any window or focus switch

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp (short `ls` segments may be trimmed by up to 30% if dead air is excessive)

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `git clone` fails (network) | Kill recording. Check network. Retry from Shot 1. |
| `chiron` command not found | Kill recording. Fix PATH. Do not patch on camera. |
| Chiron gives generic/ungrounded response | Kill recording. Check entity config. Retry Shot 7, or full retake if flow is broken. |
| flowbie unavailable | Record from thinker. Same instructions apply. |
| Take goes > 8 minutes | Tighten Shot 5 (CLAUDE.md VO) — reduce commentary, let scroll carry more weight. |

---

## Final Deliverables from This Session

- [ ] Raw recording: `2026-04-05-clone-raw.mp4` (unedited, full take)
- [ ] Edited cut: `2026-04-05-clone-final.mp4` (5–8 min, trimmed per notes above)
- [ ] Thumbnail: `2026-04-05-clone-thumb.png` (1280x720, see script.md for concept)
- [ ] Captions: auto-generated + manually reviewed
- [ ] Upload-ready: title, description, tags from script.md applied before hand-off to Mercury
