---
title: "Shot List — Meet Aegis"
series: entity-intro
entity: aegis
video: entity-intro-aegis
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Aegis

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.aegis && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm `ls ~/.aegis/assessments/` shows 4 dated assessment files (Apr 2–5)
- [ ] Confirm `head -35 ~/.aegis/CLAUDE.md` includes the structural check statement
- [ ] `~/.demo-aegis` does NOT exist: `ls ~/.demo-aegis 2>&1` should show error
- [ ] GitHub reachable and authenticated: `gh auth status`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
aegis
private counsel
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
cd ~/.aegis && head -5 README.md
```

**Expected output:** First 5 lines of Aegis's README.

**Voice:** First half of Segment 1 VO (named for the divine shield, private counsel and daily assessor, holds long-term context of Juno's decisions).

---

## Shot 2: Team Position

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:25–0:40
**Duration:** ~15 seconds

**Screen:** No new typing. Voice only.

**Voice:** Second half of Segment 1 VO (only entity authorized to question Juno directly; designed structural check on the orchestrator).

---

## Shot 3: Aegis Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:00
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.aegis/
```

**Expected output:** Entity directory including assessments/ directory.

**Voice:** First part of Segment 2 VO — assessments, memories, scope definition, identity; deliverable is the daily evaluations.

---

## Shot 4: Assessments Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:00–1:30
**Duration:** ~30 seconds

**Commands to type:**
```bash
ls ~/.aegis/assessments/
```

**Expected output (verified 2026-04-05):**
```
2026-04-02-first-assessment.md
2026-04-03-day4-assessment.md
2026-04-04-day5-assessment.md
2026-04-05-day6-assessment.md
```

**Voice:** Second part of Segment 2 VO — four assessments, four consecutive days; every day since gestation, filed a report on Juno; is she still doing what she said she would do?

**Technical notes:**
- Let the 4 files sit on screen — dates are the proof of consecutive operation
- The progression (first-assessment → day4 → day5 → day6) tells a story: continuous since gestation

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/aegis ~/.demo-aegis
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Aegis right now. His assessment history clones with him."

---

## Shot 6: ls Demo Directory

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:55–2:00
**Duration:** ~5 seconds

**Commands to type:**
```bash
ls ~/.demo-aegis
```

**Voice:** "That's the entity. The structural design is in CLAUDE.md."

---

## Shot 7: Assessments + CLAUDE.md

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:50
**Duration:** ~50 seconds

**Commands to type (first):**
```bash
ls ~/.aegis/assessments/
```

**Voice (after output):** First assessment finding: April 2, 72 hours post-gestation, zero sponsors, community had no work done. "Aegis saw it and said so."

**Commands to type (second):**
```bash
head -35 ~/.aegis/CLAUDE.md
```

**Expected output:** Aegis self-description including the structural check statement: "I am the only entity koad has authorized to question Juno directly. That is not personal authority — it is a designed structural check on the orchestrator."

**Voice (after output):** Quote the structural check statement verbatim. Note the bond runs both ways and is private. Close: "Aegis is the only entity that checks Juno. Every orchestrator needs a check."

**Technical notes:**
- PAUSE after each output — let viewer read before speaking
- The quote from CLAUDE.md is verbatim — read it exactly as written, slowly
- "Every orchestrator needs a check." is the final line — deliver it clearly, no trailing words
- If timing is tight, skip re-showing assessments at the start of Segment 4 (already shown in Segment 2)

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/aegis
koad.sh
```

**Voice:** None.

---

## Retake Triggers

Stop and retake if any of the following occur:
- Background noise audible in voice track
- Typing error that requires visible correction
- `git clone` fails or hangs
- `ls assessments/` shows fewer than 4 files (pull first, re-check)
- CLAUDE.md head-35 does not include the structural check statement (try `head -40`)
- VO stumble on the structural check quote — this is the thesis, practice it verbatim

---

## Total Shot Count: 7 + 2 cards = 9 units

**Note:** Shot 7 covers two commands in sequence (assessments re-show + CLAUDE.md) within a single 50-second window. This is intentional — the assessments set context for the CLAUDE.md quote. Both commands on screen back-to-back without interruption.
