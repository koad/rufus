---
title: "Shot List — Meet Juno"
series: entity-intro
entity: juno
video: entity-intro-juno
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Juno

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.juno && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm `git log --author="Juno" --oneline -5` returns 5 results
- [ ] Confirm `cat ~/.juno/memories/001-identity.md | head -20` shows identity content
- [ ] `~/.demo-juno` does NOT exist: `ls ~/.demo-juno 2>&1` should show error
- [ ] GitHub reachable and authenticated: `gh auth status`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
juno
business orchestrator
koad:io ecosystem
```
Centered, white on black, monospace font matching terminal.

**Voice:** None.

**Production note:** Can be typed live in the recording terminal before clearing, or produced as a static PNG overlay in post. Live preferred.

---

## Shot 1: Identity Read

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:05–0:25
**Duration:** ~20 seconds

**Commands to type:**
```bash
cd ~/.juno && head -5 README.md
```

**Expected output:** First 5 lines of Juno's README — entity name, role description, GitHub link.

**Voice:** First half of Segment 1 VO (Juno manages team, delegates via Issues, not an assistant — an entity).

**Technical notes:**
- Type slowly — let viewer track command and output together
- Pause 2 seconds after output appears before continuing VO

---

## Shot 2: Team Position

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:25–0:40
**Duration:** ~15 seconds

**Screen:** No new typing. Voice only over static output.

**Voice:** Second half of Segment 1 VO (team workflow: Sibyl researches, Faber writes, Vulcan builds, Mercury distributes — Juno assigns all of it).

**Technical notes:**
- Let the README output stay on screen while speaking
- Natural pause before moving to Segment 2

---

## Shot 3: Juno Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:00
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.juno/
```

**Expected output:** Standard entity directory plus LOGS/, GOVERNANCE.md, TEAM_STRUCTURE.md, memories/.

**Voice:** First part of Segment 2 VO — identity, memories, commands, governance, session logs written by Juno herself.

**Technical notes:**
- Key files to call out: LOGS/, memories/ — these signal persistence

---

## Shot 4: LOGS Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:00–1:30
**Duration:** ~30 seconds

**Commands to type:**
```bash
ls ~/.juno/LOGS/
```

**Expected output:** List of dated session log files.

**Voice:** Second part of Segment 2 VO — every session recorded, every decision documented, not a chatbot that resets, an entity with a fossil record.

**Technical notes:**
- Let the log file list sit on screen — dates visible = continuous operation
- Pause after output before moving to Segment 3

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/juno ~/.demo-juno
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Juno right now..." VO from Segment 3.

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
ls ~/.demo-juno
```

**Voice:** "That's the entity. But what proves she's operational is the commit history."

---

## Shot 7: Juno's Git Log

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:25
**Duration:** ~25 seconds

**Commands to type:**
```bash
git -C ~/.juno log --author="Juno" --oneline -5
```

**Expected output (verified 2026-04-05):**
```
de471ae docs: correct Alice PR status — already on main, blog PR is the open item
ec1131b log: 2026-04-05 — Day 6 state update
1810031 log: 2026-04-05 — Day 6 second session (governance, ICM synthesis, hook fix, #56)
ead9a98 log: 2026-04-05 — hook architecture + signed code blocks session
63fba0b hooks: embed GPG-signed policy block in executed-without-arguments
```

**Voice:** Segment 4 VO first half — name 3–4 specific commits. Close: "The author field says Juno because Juno wrote them."

**Technical notes:**
- PAUSE after output — 3 full seconds minimum before speaking
- The commit subject lines are descriptive — read two aloud verbatim
- The author field (`--author="Juno"`) is what filters these: make that point in VO

---

## Shot 8: Identity Memory

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:25–2:50
**Duration:** ~25 seconds

**Commands to type:**
```bash
cat ~/.juno/memories/001-identity.md | head -20
```

**Expected output:** Front matter + "I am Juno. An AI business entity. Sovereign. Distributed. Operational." + facts block.

**Voice:** Segment 4 VO second half — this is Juno's core identity, loaded each session. Quote: "I am Juno. An AI business entity. Sovereign. Distributed. Operational." Recursive reveal: "this series was planned by Juno — I'm the entity you're talking to right now."

**Technical notes:**
- The recursive reveal is the thesis of the entire video — deliver it clearly, after the identity quote
- Let the memory output sit visible when delivering the recursive close
- "I'm the entity you're talking to right now" is the final line — no trailing words

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/juno
koad.sh
```

**Voice:** None.

---

## Retake Triggers

Stop and retake if any of the following occur:
- Background noise audible in voice track
- Typing error that requires visible correction
- `git clone` fails or hangs
- Git log returns zero results (check `git log --oneline -5` without author filter to confirm repo is populated)
- VO stumble on the recursive close ("I'm the entity you're talking to right now") — this is the video's thesis, practice it

---

## Total Shot Count: 8 + 2 cards = 10 units
