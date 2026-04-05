---
title: "Shot List — Meet Argus"
series: entity-intro
entity: argus
video: entity-intro-argus
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Argus

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.argus && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm `git log --author="Argus" --oneline -5` returns 5 results
- [ ] Confirm `head -30 ~/.argus/CLAUDE.md` includes role description and Mercury gate mention
- [ ] `~/.demo-argus` does NOT exist: `ls ~/.demo-argus 2>&1` should show error
- [ ] GitHub reachable and authenticated: `gh auth status`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
argus
diagnostics
koad:io ecosystem
```
Centered, white on black, monospace font matching terminal.

**Voice:** None.

---

## Shot 1: Identity Read

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:05–0:25
**Duration:** ~20 seconds

**Commands to type:**
```bash
cd ~/.argus && head -5 README.md
```

**Expected output:** First 5 lines of Argus's README.

**Voice:** First half of Segment 1 VO (named for the hundred-eyed giant, examines entity directories against koad:io protocol, reports exactly what's wrong).

---

## Shot 2: Team Position

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:25–0:40
**Duration:** ~15 seconds

**Screen:** No new typing. Voice only.

**Voice:** Second half of Segment 1 VO (Argus diagnoses, not fixes; Mercury gate — nothing reaches a platform without his verdict).

---

## Shot 3: Argus Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:00
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.argus/
```

**Expected output:** Entity directory structure including diagnoses/, protocols/, memories/.

**Voice:** First part of Segment 2 VO — diagnoses directory, gate logs, structured reports on healthy and broken.

---

## Shot 4: Diagnoses or Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:00–1:30
**Duration:** ~30 seconds

**Commands to type:**
```bash
ls ~/.argus/diagnoses/ 2>/dev/null || ls ~/.argus/
```

**Expected output:** Diagnostic report files if present, or entity directory listing.

**Voice:** Second part of Segment 2 VO — quality chain: Argus diagnoses, Salus heals, Vesta defines healthy; Argus is the starting point.

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/argus ~/.demo-argus
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Argus right now. His diagnostic protocols and gate rules come with him."

---

## Shot 6: ls Demo Directory

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:55–2:00
**Duration:** ~5 seconds

**Commands to type:**
```bash
ls ~/.demo-argus
```

**Voice:** "That's the entity. The proof of operation is in the git log."

---

## Shot 7: Argus Git Log

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:25
**Duration:** ~25 seconds

**Commands to type:**
```bash
git -C ~/.argus log --author="Argus" --oneline -5
```

**Expected output (verified 2026-04-05):**
```
93cb65d docs: add PRIMER.md — session orientation for arriving agents
66600c7 hooks: inject $CWD/PRIMER.md into prompt when present
61b1caa readme: lead with architecture, remove quote opener
bc1cdab hooks: add PID lock — prevent concurrent task invocations
8479a06 hooks: remove -c from non-interactive path — tasks run fresh, not resuming stale sessions
```

**Voice:** Segment 4 VO first half — PRIMER injection, PID lock, fresh sessions; "infrastructure commits — Argus building the watching infrastructure itself."

**Technical notes:**
- PAUSE after output — 3 full seconds minimum before speaking
- Name the specific commits: PRIMER injection, PID lock, fresh sessions
- The commits are technical — read them clearly, don't rush

---

## Shot 8: CLAUDE.md Role Description

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:25–2:50
**Duration:** ~25 seconds

**Commands to type:**
```bash
head -30 ~/.argus/CLAUDE.md
```

**Expected output:** Argus self-description including "hundred-eyed giant who sees everything and misses nothing" and Mercury gate protocol mention.

**Voice:** Segment 4 VO second half — quote "the hundred-eyed giant who sees everything and misses nothing. That is the job." Name the standing assignment: nothing reaches a platform without his verdict. Close: "Every system needs someone watching it. In this system, that's Argus."

**Technical notes:**
- Let the CLAUDE.md text sit on screen before quoting from it
- The quote is verbatim from the file — read it as written
- "Every system needs someone watching it." is the final line — deliver clearly, no trailing words

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/argus
koad.sh
```

**Voice:** None.

---

## Retake Triggers

Stop and retake if any of the following occur:
- Background noise audible in voice track
- Typing error that requires visible correction
- `git clone` fails or hangs
- Git log returns zero results (check `cd ~/.argus && git log --oneline -5` without author filter)
- CLAUDE.md head does not show the "hundred-eyed giant" quote (pull first, re-check)
- VO stumble on the closing line ("every system needs someone watching it") — practice it

---

## Total Shot Count: 8 + 2 cards = 10 units
