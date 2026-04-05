---
title: "Shot List — Meet Livy"
series: entity-intro
entity: livy
video: entity-intro-livy
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Livy

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.livy && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm `ls ~/.livy/docs/reference/` returns 9 files
- [ ] Confirm `wc -l ~/.livy/docs/reference/*.md` shows 2903 total
- [ ] `~/.demo-livy` does NOT exist: `ls ~/.demo-livy 2>&1` should show error
- [ ] GitHub reachable and authenticated: `gh auth status`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
livy
documentation lead
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
cd ~/.livy && head -5 README.md
```

**Expected output:** First 5 lines of Livy's README — entity name, documentation role.

**Voice:** First half of Segment 1 VO (named for Titus Livius, documents everything users and agents need to know).

**Technical notes:**
- Type slowly — let viewer track command and output together
- Pause 2 seconds after output appears before continuing VO

---

## Shot 2: Team Position

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:25–0:40
**Duration:** ~15 seconds

**Screen:** No new typing. Voice only over static output.

**Voice:** Second half of Segment 1 VO (sits between builders and users, Vulcan ships code, Livy explains it, Vesta defines protocol, Livy records it).

---

## Shot 3: Livy Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:00
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.livy/
```

**Expected output:** Entity directory structure — commands, docs, documentation, memories, etc.

**Voice:** First part of Segment 2 VO — commands, documentation library, reference archive; the deliverable is in the docs.

---

## Shot 4: Docs Structure

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:00–1:30
**Duration:** ~30 seconds

**Commands to type:**
```bash
ls ~/.livy/docs/
```

**Expected output:** docs subdirectories including reference/.

**Voice:** Second part of Segment 2 VO — reference library covers every system layer: daemon, entities, framework, gestation, trust bonds.

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/livy ~/.demo-livy
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Livy right now. Her full reference library clones with her."

**Technical notes:**
- Type the clone command slowly and deliberately — read it aloud as you type
- Let clone output scroll in full

---

## Shot 6: ls Demo Directory

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:55–2:00
**Duration:** ~5 seconds

**Commands to type:**
```bash
ls ~/.demo-livy
```

**Voice:** "That's the entity. The docs are in docs/reference/."

---

## Shot 7: Reference Library Contents

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:25
**Duration:** ~25 seconds

**Commands to type:**
```bash
ls ~/.livy/docs/reference/
```

**Expected output (verified 2026-04-05):**
```
daemon-architecture.md
entity-directory-structure-claude-section.md
entity-directory-structure.md
framework-layer.md
gestation-process.md
operations-architecture.md
packages-structure.md
README.md
trust-bond-system.md
```

**Voice:** Segment 4 VO first half — name the nine documents specifically: daemon architecture, entity structure, framework layer, gestation, operations, trust bonds. Close: "Each one a complete treatment of its subject."

**Technical notes:**
- PAUSE after output — 3 full seconds minimum before speaking
- Let the viewer read the file names — they tell the story
- Name at least 5–6 files aloud from what is on screen

---

## Shot 8: Word Count

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:25–2:50
**Duration:** ~25 seconds

**Commands to type:**
```bash
wc -l ~/.livy/docs/reference/*.md
```

**Expected output (verified 2026-04-05):**
```
   259 .../daemon-architecture.md
    61 .../entity-directory-structure-claude-section.md
   424 .../entity-directory-structure.md
   343 .../framework-layer.md
   496 .../gestation-process.md
   422 .../operations-architecture.md
   229 .../packages-structure.md
    18 .../README.md
   651 .../trust-bond-system.md
  2903 total
```

**Voice:** Segment 4 VO second half — read the total aloud: "Two thousand, nine hundred and three lines." Call out trust-bond-system.md at 651 lines. Close: "The documentation is the deliverable. Livy builds it."

**Technical notes:**
- Pause after output — let viewer see the numbers
- The total (2903) is the proof — read it aloud as a number, not digits
- "The documentation is the deliverable. Livy builds it." is the final line — no trailing words

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/livy
koad.sh
```

**Voice:** None.

---

## Retake Triggers

Stop and retake if any of the following occur:
- Background noise audible in voice track
- Typing error that requires visible correction
- `git clone` fails or hangs
- `ls docs/reference/` returns fewer than 9 files (pull first, re-check)
- VO stumble on the closing line ("The documentation is the deliverable. Livy builds it.") — practice it

---

## Total Shot Count: 8 + 2 cards = 10 units
