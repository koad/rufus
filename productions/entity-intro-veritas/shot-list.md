---
title: "Shot List — Meet Veritas"
series: entity-intro
entity: veritas
video: entity-intro-veritas
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Veritas

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.veritas && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm `ls ~/.veritas/reviews/ | wc -l` returns current count (note the number before recording — state it in VO)
- [ ] Confirm `ls ~/.veritas/protocols/` shows at least one protocol file
- [ ] Confirm `head -20 ~/.veritas/reviews/2026-04-04-faber-pipeline-review.md` shows expected verdict structure
- [ ] `~/.demo-veritas` does NOT exist: `ls ~/.demo-veritas 2>&1` should show error
- [ ] GitHub reachable: `ping -c1 github.com`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
veritas
quality and fact-check
koad:io ecosystem
```
Centered, white on black, monospace font matching terminal.

**Voice:** None.

**Production note:** Can be typed live in the recording terminal before clearing, or produced as a static PNG overlay in post. Live preferred — no post work needed.

---

## Shot 1: Identity Read

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:05–0:25
**Duration:** ~20 seconds

**Commands to type:**
```bash
cd ~/.veritas && head -5 README.md
```

**Expected output:** First 5 lines of Veritas's README — entity name, role as fact-checker and verification officer.

**Voice:** First half of Segment 1 VO (who Veritas is, what it does).

**Technical notes:**
- Type slowly — let viewer track command and output together
- Pause 2 seconds after output appears before continuing VO
- If README head-5 is sparse, use `head -10`

---

## Shot 2: Team Position

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:25–0:40
**Duration:** ~15 seconds

**Screen:** No new typing. Voice only over static output.

**Voice:** Second half of Segment 1 VO (Veritas's position: Vulcan ships → Veritas checks; Faber writes → Veritas reviews; Mercury queues → Veritas signs off).

**Technical notes:**
- Let the README output stay on screen while speaking — it anchors the VO
- Natural pause before moving to Segment 2

---

## Shot 3: Directory Overview

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:00
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.veritas/
```

**Expected output:** Full directory listing — `archive  bin  CLAIMS.md  CLAUDE.md  commands  comms  criteria  documentation  etc  features  GOVERNANCE.md  home  id  identity  keybase  KOAD_IO_VERSION  lib  man  media  memories  opencode  opencode.jsonc  passenger.json  PRIMER.md  proc  protocols  README.md  reports  res  reviews  ssl  trust  usr  var`

**Voice:** First half of Segment 2 VO (full stack: protocols, criteria, claims registry, reviews — confidence levels required on every finding).

**Technical notes:**
- Pause after output — highlight `protocols`, `criteria`, `reviews` visually in your eye-line while speaking
- The breadth of the directory shows a real entity infrastructure, not a single-purpose script

---

## Shot 4: Protocols

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:00–1:30
**Duration:** ~30 seconds

**Commands to type:**
```bash
ls ~/.veritas/protocols/
```

**Expected output:** `vulcan-build-review.md` (and any additional protocol files added since production)

**Voice:** Second half of Segment 2 VO (documented protocols for each review type — factual claims, source credibility, scope alignment; every review runs the same checklist).

**Technical notes:**
- Pause on output — even a single protocol file proves the pattern
- "Every review runs the same checklist" is the closing line of this segment — let it land

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/veritas ~/.demo-veritas
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Veritas right now..." VO from Segment 3.

**Technical notes:**
- Type the clone command slowly and deliberately — read it aloud as you type
- Let clone output scroll in full — do not skip or cut here
- After clone completes, brief pause before next command

---

## Shot 6: ls Demo Directory

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:55–2:00
**Duration:** ~5 seconds

**Commands to type:**
```bash
ls ~/.demo-veritas
```

**Voice:** "That's the entity. Files. No external fact-checking service. No API. No human editor."

**Technical notes:**
- This shot is fast — just enough to see the directory structure exists
- Do not narrate the file names

---

## Shot 7: Review Count

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:10
**Duration:** ~10 seconds

**Commands to type:**
```bash
ls ~/.veritas/reviews/ | wc -l
```

**Expected output:** `21` (or current count — use the number you noted in pre-production checklist)

**Voice:** "[Number] reviews on disk. Every one of them is a real review of real team output."

**Technical notes:**
- State the exact number you see — don't guess
- Pause 1 second after output to let the number register

---

## Shot 8: Review Directory Listing

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:10–2:25
**Duration:** ~15 seconds

**Commands to type:**
```bash
ls ~/.veritas/reviews/
```

**Expected output:** All 21 review files — dated, named by subject: `2026-04-02-mercury-milestone-review.md`, `2026-04-03-competitive-claims.md`, `2026-04-04-faber-pipeline-review.md`, etc.

**Voice:** Read a selection of the file names — Mercury, Sibyl, Faber, competitive claims, homepage copy. "Every team function represented."

**Technical notes:**
- Let the output scroll or wrap — the volume is the visual argument
- Read 3–4 specific file names aloud — pick ones from different domains

---

## Shot 9: Read Review Opening

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:25–2:50
**Duration:** ~25 seconds

**Commands to type:**
```bash
head -20 ~/.veritas/reviews/2026-04-04-faber-pipeline-review.md
```

**Expected output:** YAML frontmatter (reviewer, date, files reviewed) + first section showing method statement: "Each claim verified against live filesystem, git history, and GitHub Issues. Repos pulled fresh before reading."

**Voice:** Narrate the structure: reviewer, files reviewed, method — then read the method statement aloud. Close with "That's the protocol. Every review, the same rigor."

**Technical notes:**
- Pause after output — let viewer read the method statement independently
- Read "Each claim verified against live filesystem, git history, and GitHub Issues" verbatim — it's the proof of discipline
- This is the emotional peak of the video — slow down here

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/veritas
koad.sh
```

**Voice:** None.

**Technical notes:**
- Same aesthetic as opening card
- If typed live: type slowly, cursor blinks on last line
- If PNG overlay: fade in over 1 second, hold

---

## Retake Triggers

Stop and retake if any of the following occur:
- Background noise audible in voice track
- Typing error that requires visible correction
- `git clone` fails or hangs
- Review count differs from what was stated in VO (always note the real count before recording)
- VO stumble on the method statement in the review file (most likely stumble point — practice it)

---

## Total Shot Count: 9 + 2 cards = 11 units
