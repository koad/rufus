---
title: "Shot List — Meet Chiron"
series: entity-intro
entity: chiron
video: entity-intro-chiron
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Chiron

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.chiron && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm 13 level files exist: `ls ~/.chiron/curricula/alice-onboarding/levels/ | wc -l` should return 13
- [ ] `~/.demo-chiron` does NOT exist: `ls ~/.demo-chiron 2>&1` should show error
- [ ] GitHub reachable: `ping -c1 github.com`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
chiron
curriculum architect
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
cd ~/.chiron && head -5 README.md
```

**Expected output:** First 5 lines of Chiron's README — entity name, role, repo link.

**Voice:** First half of Segment 1 VO (who Chiron is, what he does).

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

**Voice:** Second half of Segment 1 VO (Chiron's position in team: upstream of Alice, receives from Juno).

**Technical notes:**
- Let the README output stay on screen while speaking — it anchors the VO
- Natural pause before moving to Segment 2

---

## Shot 3: Curricula Overview

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:00
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.chiron/curricula/
```

**Expected output:** `advanced-trust-bonds   alice-onboarding   entity-operations   REGISTRY.md`

**Voice:** First half of Segment 2 VO (three curricula, alice-onboarding is primary, 13-level sequence).

**Technical notes:**
- Pause after output — let viewer read the directory names
- If output is single-line, it may need a moment to register visually

---

## Shot 4: Alice Onboarding Structure

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:00–1:30
**Duration:** ~30 seconds

**Commands to type:**
```bash
ls ~/.chiron/curricula/alice-onboarding/
```

**Expected output:** `assessments  DECISIONS.md  graduation-speech.md  levels  REGISTRY.md  SPEC.md`

**Voice:** Second half of Segment 2 VO (levels = markdown, authored by Chiron, committed to git, Chiron builds the map not the app).

**Technical notes:**
- Pause on output — `DECISIONS.md` and `graduation-speech.md` are interesting details, let them register
- No need to `cat` any of these — save the read for Segment 4

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/chiron ~/.demo-chiron
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Chiron right now..." VO from Segment 3.

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
ls ~/.demo-chiron
```

**Voice:** "That's the entity. Files. No service. No API. No account."

**Technical notes:**
- This shot is fast — just enough to see the directory structure exists
- Do not narrate the file names

---

## Shot 7: List Levels

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:20
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.chiron/curricula/alice-onboarding/levels/
```

**Expected output:**
```
level-00.md  level-01.md  level-02.md  level-03.md  level-04.md  level-05.md  level-06.md
level-07.md  level-08.md  level-09.md  level-10.md  level-11.md  level-12.md
```

**Voice:** "Thirteen levels. Level zero through level twelve. Here's level zero — the entry point."

**Technical notes:**
- Pause after output so viewer can count
- 13 files in one ls is the visual anchor for the whole video
- If output wraps across multiple lines, that's fine — let it

---

## Shot 8: Read Level Zero

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:20–2:50
**Duration:** ~30 seconds

**Commands to type:**
```bash
cat ~/.chiron/curricula/alice-onboarding/levels/level-00.md | head -30
```

**Expected output:** YAML frontmatter (type, level, title, learning objective) + first section of Level 0.

**Voice:** Segment 4 VO — describe level 0 title "The First File", read the learning objective aloud, close with "Thirteen levels. All on disk."

**Technical notes:**
- Pause after output — let viewer read the learning objective independently
- Read the learning objective text aloud verbatim — it's well-written and makes the case for itself
- If `head -30` cuts off before the learning objective body, use `head -35`
- This is the emotional peak of the video — slow down here

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/chiron
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
- Wrong directory shown (e.g., showing demo dir instead of live dir)
- VO stumble on the learning objective text (most likely stumble point — practice it)

---

## Total Shot Count: 8 + 2 cards = 10 units
