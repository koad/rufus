---
title: "Shot List — Meet Janus"
series: entity-intro
entity: janus
video: entity-intro-janus
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Janus

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.janus && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm `head -30 ~/.janus/CLAUDE.md` shows "What I Watch" section with named repos and signal types
- [ ] Confirm `ls ~/.janus/watchers/` shows `github-feeds.sh`
- [ ] Confirm `ls ~/.janus/watches/` shows dated watch log files
- [ ] Confirm `head -20 ~/.janus/watches/2026-04-02-afternoon-stream.md` shows expected observation structure
- [ ] `~/.demo-janus` does NOT exist: `ls ~/.demo-janus 2>&1` should show error
- [ ] GitHub reachable: `ping -c1 github.com`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
janus
stream watcher
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
cd ~/.janus && head -5 README.md
```

**Expected output:** First 5 lines of Janus's README — entity name, stream watcher role, two-faced god reference.

**Voice:** First half of Segment 1 VO (who Janus is, named for the Roman god, monitors atom feeds).

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

**Voice:** Second half of Segment 1 VO (thirteen repos, six signal types, "Janus alerts. Janus doesn't fix.").

**Technical notes:**
- Let the README output stay on screen while speaking — it anchors the VO
- The "alerts. doesn't fix." line needs a pause between the two sentences — it's the identity beat
- Natural pause before moving to Segment 2

---

## Shot 3: Directory Overview

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:05
**Duration:** ~25 seconds

**Commands to type:**
```bash
ls ~/.janus/
```

**Expected output:** Full directory listing including `watches`, `watchers`, `reports`, `protocols`, `briefs`, `state`

**Voice:** First half of Segment 2 VO (watch logs, reports, watchers, protocols — operational record on disk).

**Technical notes:**
- Pause after output — point out `watches` and `watchers` by mentioning them in VO
- The directory structure communicates the operational depth before any files are read

---

## Shot 4: Watchers

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:05–1:30
**Duration:** ~25 seconds

**Commands to type:**
```bash
ls ~/.janus/watchers/
```

**Expected output:** `github-feeds.sh`

**Voice:** Second half of Segment 2 VO (github-feeds.sh reads atom feeds for every entity repo — no dashboard, no external service, a shell script and a directory of files).

**Technical notes:**
- Pause on output — even a single file proves the pattern
- "No dashboard. No external service." is the sovereignty beat — deliver it cleanly

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/janus ~/.demo-janus
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Janus right now..." VO from Segment 3.

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
ls ~/.demo-janus
```

**Voice:** "That's the entity. Files. No monitoring service. No SaaS dashboard. No account."

**Technical notes:**
- This shot is fast — just enough to see the directory structure exists
- Do not narrate the file names

---

## Shot 7: CLAUDE.md Surveillance Scope

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:30
**Duration:** ~30 seconds

**Commands to type:**
```bash
head -30 ~/.janus/CLAUDE.md
```

**Expected output:** CLAUDE.md header through "What I Watch" section — named repos list, signal type list (commit patterns, issue activity, PR activity, trust bond activity, pipeline breaks, role drift).

**Voice:** Read the key elements — thirteen named repos, six signal types, then note the intervention protocol and what Janus does NOT file issues for. "The filter has two sides."

**Technical notes:**
- Pause after output — let viewer read the signal type list
- The "Do not file issues for" section is as important as the "What I Watch" section — mention both
- If `head -30` doesn't reach the "Do not file" section, note it verbally ("and importantly, Janus has a defined list of things it doesn't escalate")

---

## Shot 8: Watch Log

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:30–2:50
**Duration:** ~20 seconds

**Commands to type:**
```bash
head -20 ~/.janus/watches/2026-04-02-afternoon-stream.md
```

**Expected output:** YAML frontmatter (date range, watcher: Janus, status: observed) + summary section showing "41 commits across 5 entity repos in a 6-hour window".

**Voice:** Narrate the observation format — date range, watcher, status, commit volume. Close with "This is what the surveillance looks like when it runs clean — no anomalies, just the record."

**Technical notes:**
- Pause after output — let viewer read the structured observation data
- "Status: observed" with no escalation is itself a data point — note it
- This is the closing proof beat — keep the VO calm and declarative

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/janus
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
- `head -30 CLAUDE.md` doesn't reach the "What I Watch" section (use `head -40` instead — adjust VO accordingly)
- VO stumble on the "Janus alerts. Janus doesn't fix." line (practice the pause between the two sentences)

---

## Total Shot Count: 8 + 2 cards = 10 units
