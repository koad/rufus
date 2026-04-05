---
title: "Shot List — Meet Muse"
series: entity-intro
entity: muse
video: entity-intro-muse
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Muse

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.muse && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm briefs exist: `ls ~/.muse/briefs/ | wc -l` should return 10 or more
- [ ] Confirm alice brief exists: `ls ~/.muse/briefs/alice-ui-design-brief.md`
- [ ] `~/.demo-muse` does NOT exist: `ls ~/.demo-muse 2>&1` should show error
- [ ] GitHub reachable: `ping -c1 github.com`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
muse
visual designer
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
cd ~/.muse && head -5 README.md
```

**Expected output:** First 5 lines of Muse's README — entity name, role, repo link.

**Voice:** First half of Segment 1 VO (who Muse is, design briefs not code, Muse designed it first).

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

**Voice:** Second half of Segment 1 VO (Muse sits between Juno and Vulcan — design before build).

**Technical notes:**
- Let the README output stay on screen while speaking
- Natural pause before moving to Segment 2

---

## Shot 3: Briefs Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:10
**Duration:** ~30 seconds

**Commands to type:**
```bash
ls ~/.muse/briefs/
```

**Expected output:** 20+ filenames — alice-ui-design-brief.md and dated brief files from 2026-04-02 onward.

**Voice:** First half of Segment 2 VO — name 6–7 of the briefs (homepage, entity card, MVP Zone, stream PWA, graduation certificate, trust bond viz, blog layout). Then note the dates.

**Technical notes:**
- Pause after output — let viewer scan the filenames
- Call out specific filenames by name in VO — they are all readable from the output
- The dated filenames are the proof of ongoing cadence — mention this

---

## Shot 4: Briefs Narrative

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:10–1:30
**Duration:** ~20 seconds

**Screen:** No new typing. Voice only over static briefs listing.

**Voice:** Second half of Segment 2 VO — markdown, git, versioned, "when Vulcan builds there's a file saying what it should look like."

**Technical notes:**
- Let the briefs listing remain on screen throughout
- This is the "so what" close for Segment 2 — deliver it with conviction

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/muse ~/.demo-muse
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Muse right now..." VO from Segment 3.

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
ls ~/.demo-muse
```

**Voice:** "That's the entity. The design system is portable."

**Technical notes:**
- Fast shot — just enough to see directory structure exists
- Do not narrate the file names

---

## Shot 7: Briefs Library Reprise

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:15
**Duration:** ~15 seconds

**Commands to type:**
```bash
ls ~/.muse/briefs/
```

**Expected output:** Full briefs listing again.

**Voice:** "The full library. Let's look at the one that's been referenced most — the Alice UI design brief."

**Technical notes:**
- This is the setup shot — the pivot from overview to depth
- Let the output appear, speak the bridge line, then move to the read

---

## Shot 8: Read Alice UI Brief Header

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:15–2:50
**Duration:** ~35 seconds

**Commands to type:**
```bash
head -20 ~/.muse/briefs/alice-ui-design-brief.md
```

**Expected output:** YAML-adjacent markdown header showing Status, Date, Audience, Entity, References, and beginning of Changelog section.

**Voice:** Segment 4 VO — read status line, audience, entity, references. Close with "The UI was designed before it was built."

**Technical notes:**
- Pause after output — let viewer absorb the header fields
- Read the References line aloud — it shows cross-entity coordination (PROJECT-08, design system, vulcan#36, chiron decisions)
- The closing line is the thesis — slow down and deliver it clearly
- If `head -20` cuts before References, use `head -25`

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/muse
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
- Alice UI brief header not visible (wrong file path)
- VO stumble on the References line or the closing thesis line — both are dense

---

## Total Shot Count: 8 + 2 cards = 10 units
