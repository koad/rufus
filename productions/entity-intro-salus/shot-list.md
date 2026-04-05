---
title: "Shot List — Meet Salus"
series: entity-intro
entity: salus
video: entity-intro-salus
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Salus

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.salus && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm `head -35 ~/.salus/CLAUDE.md` shows role description and healing protocol table
- [ ] Confirm `ls ~/.salus/reports/` shows dated heal report files
- [ ] `~/.demo-salus` does NOT exist: `ls ~/.demo-salus 2>&1` should show error
- [ ] GitHub reachable and authenticated: `gh auth status`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
salus
entity health
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
cd ~/.salus && head -5 README.md
```

**Expected output:** First 5 lines of Salus's README.

**Voice:** First half of Segment 1 VO (named for Roman goddess of safety, runs daily health checks on all 12 entities, fixes directly or escalates to Juno).

---

## Shot 2: Team Position

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:25–0:40
**Duration:** ~15 seconds

**Screen:** No new typing. Voice only.

**Voice:** Second half of Segment 1 VO (two sources of truth: Argus's diagnosis and Vesta's protocol; Salus acts on their combined output).

---

## Shot 3: Salus Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:00
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.salus/
```

**Expected output:** Entity directory including reports/ directory.

**Voice:** First part of Segment 2 VO — protocols, memories, heal reports, governance; deliverable is the reports, filed and committed.

---

## Shot 4: Heal Reports

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:00–1:30
**Duration:** ~30 seconds

**Commands to type:**
```bash
ls ~/.salus/reports/
```

**Expected output (verified 2026-04-05):**
```
2026-04-02-heal-team.md
2026-04-03-cascade-environment-verification.md
2026-04-03-github-connectivity.md
2026-04-03.md
2026-04-03-re-audit-vesta-spec-008.md
2026-04-03-vesta-patch-audit.md
2026-04-04.md
post-vesta-specs-20260403.md
vulcan-20260403.md
```

**Voice:** Second part of Segment 2 VO — name the report types: cascade verification, GitHub connectivity, Vesta spec audits, Vulcan-specific checks. "Active incident response, not a cron job."

**Technical notes:**
- Let the report list sit on screen — dates and names tell the story
- Call out at least 4 specific report names to show the variety

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/salus ~/.demo-salus
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Salus right now. Her healing protocol and report history come with her."

---

## Shot 6: ls Demo Directory

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:55–2:00
**Duration:** ~5 seconds

**Commands to type:**
```bash
ls ~/.demo-salus
```

**Voice:** "That's the entity. The healing protocol is in CLAUDE.md."

---

## Shot 7: CLAUDE.md Role Description and Protocol

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:50
**Duration:** ~50 seconds

**Commands to type:**
```bash
head -35 ~/.salus/CLAUDE.md
```

**Expected output:** Salus self-description including "healer of the koad:io ecosystem", two sources of truth (Argus + Vesta), and the healthy entity checklist table.

**Voice:** Segment 4 VO — quote "I am Salus — healer of the koad:io ecosystem." Name the two sources of truth. Read the healthy entity checklist: passenger.json, memories, hooks, comms inbox/outbox, recent git commit, GitHub repo accessible. Close: "When entities drift, Salus corrects them. That is the job."

**Technical notes:**
- PAUSE after output — 4 full seconds minimum before speaking (the table is the proof, let viewer read it)
- Quote the self-description verbatim: "I am Salus — healer of the koad:io ecosystem"
- Read at least 4 items from the healthy entity checklist aloud
- "When entities drift, Salus corrects them." is the final line — deliver clearly, no trailing words

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/salus
koad.sh
```

**Voice:** None.

---

## Retake Triggers

Stop and retake if any of the following occur:
- Background noise audible in voice track
- Typing error that requires visible correction
- `git clone` fails or hangs
- `ls reports/` shows no dated files (pull first, re-check)
- CLAUDE.md head-35 does not show the healthy entity checklist table (may need `head -50`)
- VO stumble on the closing line ("When entities drift, Salus corrects them.") — practice it

---

## Total Shot Count: 7 + 2 cards = 9 units

**Note:** SEGMENT 4 is a single shot (Shot 7) covering both the git log argument and the CLAUDE.md read. The CLAUDE.md output runs long enough to carry the full 50 seconds with VO. If timing is tight, split into two shots: git log first, then CLAUDE.md head.
