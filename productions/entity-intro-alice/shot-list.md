---
title: "Shot List — Meet Alice"
series: entity-intro
entity: alice
video: entity-intro-alice
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Alice

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.alice && git pull` run in a SEPARATE terminal before recording
- [ ] `cd ~/.chiron && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm `ls ~/.alice/` shows `curriculum/` directory
- [ ] Confirm `ls ~/.chiron/curricula/alice-onboarding/levels/` shows level-00.md through level-12.md (13 files)
- [ ] Confirm `head -10 ~/.chiron/curricula/alice-onboarding/levels/level-00.md` shows front matter (type, curriculum_id, level: 0)
- [ ] `~/.demo-alice` does NOT exist: `ls ~/.demo-alice 2>&1` should show error
- [ ] GitHub reachable and authenticated: `gh auth status`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
alice
learning system
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
cd ~/.alice && head -5 README.md
```

**Expected output:** First 5 lines of Alice's README.

**Voice:** First half of Segment 1 VO (Alice is koad:io's learning system, not part of the operational team, sent to find people who are ready and walk them home).

**Technical notes:**
- Type slowly — let viewer track command and output together
- Pause 2 seconds after output before continuing VO

---

## Shot 2: Team Position

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:25–0:40
**Duration:** ~15 seconds

**Screen:** No new typing. Voice only over static output.

**Voice:** Second half of Segment 1 VO (Chiron designs the learning path, Alice delivers it, thirteen levels, first contact to full sovereignty).

---

## Shot 3: Alice Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:00
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.alice/
```

**Expected output (verified 2026-04-05):**
```
avatar.png  certificates  CLAUDE.md  commands  curriculum
id  memories  opencode  passenger.json  PRIMER.md  README.md  reviews
```

**Voice:** First part of Segment 2 VO — commands, curriculum delivery, identity, memories; key directory is curriculum.

**Technical notes:**
- `curriculum/` is the directory to call out verbally

---

## Shot 4: Curriculum Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:00–1:30
**Duration:** ~30 seconds

**Commands to type:**
```bash
ls ~/.alice/curriculum/
```

**Expected output:** Contents of Alice's curriculum delivery directory.

**Voice:** Second part of Segment 2 VO — the architectural separation: Chiron designs, Alice delivers.

**Technical notes:**
- If directory is empty or minimal, adjust VO to pivot directly to Chiron's curricula
- This shot bridges to the Chiron demo in Segment 4

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/alice ~/.demo-alice
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Alice right now. The delivery system comes with the entity."

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
ls ~/.demo-alice
```

**Voice:** "That's Alice. The curriculum is in Chiron. Let's look at what Chiron built."

---

## Shot 7: Chiron's Alice-Onboarding Levels

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:25
**Duration:** ~25 seconds

**Commands to type:**
```bash
ls ~/.chiron/curricula/alice-onboarding/levels/
```

**Expected output (verified 2026-04-05):**
```
level-00.md  level-01.md  level-02.md  level-03.md  level-04.md
level-05.md  level-06.md  level-07.md  level-08.md  level-09.md
level-10.md  level-11.md  level-12.md
```

**Voice:** Segment 4 VO first half — "Thirteen levels. Level zero through level twelve. Fully authored, not a stub."

**Technical notes:**
- PAUSE after output — 3 full seconds minimum before speaking
- Let viewer count the files — 13 visible = complete series
- "Fully authored, not a stub" is the claim — the Level 0 head in Shot 8 proves it

---

## Shot 8: Level 0 Head

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:25–2:50
**Duration:** ~25 seconds

**Commands to type:**
```bash
head -10 ~/.chiron/curricula/alice-onboarding/levels/level-00.md
```

**Expected output (verified 2026-04-05):**
```
---
type: curriculum-level
curriculum_id: a9f3c2e1-7b4d-4e8a-b5f6-2d1c9e0a3f7b
curriculum_slug: alice-onboarding
level: 0
```

**Voice:** Segment 4 VO second half — "Level zero. Front matter: curriculum ID, curriculum slug, level zero. This is the entry point. The system is ready to receive a new human." Close: "Alice delivers this. Chiron designs it. Together, they are how koad:io teaches itself to the world."

**Technical notes:**
- Read the front matter aloud — curriculum_slug: alice-onboarding, level: 0
- "Alice delivers this. Chiron designs it." is the closing thesis — final line, no trailing words
- The UUID (curriculum_id) signals real authorship — mention it briefly or let it sit visually

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/alice
koad.sh
```

**Voice:** None.

---

## Retake Triggers

Stop and retake if any of the following occur:
- Background noise audible in voice track
- Typing error that requires visible correction
- `git clone` fails or hangs
- `ls levels/` shows fewer than 13 files (pull ~/.chiron first)
- `head -10 level-00.md` shows empty or placeholder content
- VO stumble on the closing thesis ("Alice delivers this. Chiron designs it.") — practice it

---

## Total Shot Count: 8 + 2 cards = 10 units
