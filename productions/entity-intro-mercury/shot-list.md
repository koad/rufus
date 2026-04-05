---
title: "Shot List — Meet Mercury"
series: entity-intro
entity: mercury
video: entity-intro-mercury
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Mercury

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.mercury && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm `ls ~/.mercury/distribution/` shows multiple dated package files
- [ ] Confirm `ls ~/.mercury/ops/` shows: `discord-community-plan.md  incident-log.md  incident-response-playbook.md  platform-publisher-spec.md  veritas-sla.md`
- [ ] Confirm `cat ~/.mercury/SCHEDULE.md | head -30` shows posting constraints
- [ ] `~/.demo-mercury` does NOT exist: `ls ~/.demo-mercury 2>&1` should show error
- [ ] GitHub reachable: `ping -c1 github.com`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
mercury
publisher / distributor
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
cd ~/.mercury && head -5 README.md
```

**Expected output:** First 5 lines of Mercury's README — entity name, role description.

**Voice:** First half of Segment 1 VO (who Mercury is, what it does).

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

**Voice:** Second half of Segment 1 VO (Mercury's position in team: end of pipeline, Juno → Mercury → Veritas → Argus → publish).

**Technical notes:**
- Let the README output stay on screen while speaking — it anchors the VO
- Natural pause before moving to Segment 2

---

## Shot 3: Distribution Library

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:05
**Duration:** ~25 seconds

**Commands to type:**
```bash
ls ~/.mercury/distribution/
```

**Expected output:** Dated distribution package files — `2026-04-04-entities-on-disk-plan.md`, `2026-04-06-trust-bonds-plan.md`, `hn-primer-post-submission.md`, `hn-week1-submission.md`, `reddit-selfhosted-week1.md`, `twitter-week1-thread.md`

**Voice:** First half of Segment 2 VO (distribution library — platform-specific packages that have all been through the pipeline).

**Technical notes:**
- Pause after output — let viewer see the range of platform types
- The dated files make it clear this is ongoing operational work, not a demo

---

## Shot 4: Ops Infrastructure

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:05–1:30
**Duration:** ~25 seconds

**Commands to type:**
```bash
ls ~/.mercury/ops/
```

**Expected output:** `discord-community-plan.md  incident-log.md  incident-response-playbook.md  platform-publisher-spec.md  veritas-sla.md`

**Voice:** Second half of Segment 2 VO (ops infrastructure: incident log, playbook, publisher spec, Veritas SLA).

**Technical notes:**
- Pause on output — `incident-response-playbook.md` and `veritas-sla.md` are striking — let them register
- No need to `cat` any of these — save the read for Segment 4

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/mercury ~/.demo-mercury
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Mercury right now..." VO from Segment 3.

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
ls ~/.demo-mercury
```

**Voice:** "That's the entity. Files. No social media dashboard. No API keys baked in. No account."

**Technical notes:**
- This shot is fast — just enough to see the directory structure exists
- Do not narrate the file names

---

## Shot 7: Posting Schedule

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:25
**Duration:** ~25 seconds

**Commands to type:**
```bash
cat ~/.mercury/SCHEDULE.md | head -30
```

**Expected output:** Posting constraints table (max posts/day, platform gap rules, quiet window) + weekly cadence section header.

**Voice:** Read the key constraints aloud — max three originals, two-hour gap, midnight-to-seven quiet window, posting day cadence.

**Technical notes:**
- Pause after output — let viewer read the constraints table
- Read the quiet window and posting day rules verbatim — they're precise and that precision IS the point
- This is the "Mercury has discipline, not just capability" beat

---

## Shot 8: Distribution Queue

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:25–2:50
**Duration:** ~25 seconds

**Commands to type:**
```bash
cat ~/.mercury/QUEUE-2026-04-03.md | head -25
```

**Expected output:** Queue header (session time, day, status) + first draft entry showing content type, Veritas check needed, Argus gate check, priority.

**Voice:** Narrate the pipeline structure visible in the queue — drafts staged, Veritas check documented, Argus gate listed, publish window noted.

**Technical notes:**
- Pause after output — let viewer read the pipeline steps for the first draft
- The explicit "Veritas check needed" and "Stop block check" fields are the payload — read them aloud
- This is the emotional peak of the video — slow down here

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/mercury
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
- VO stumble on the posting schedule constraints (most likely stumble point — practice reading the table)

---

## Total Shot Count: 8 + 2 cards = 10 units
