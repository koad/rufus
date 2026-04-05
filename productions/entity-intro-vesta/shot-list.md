---
title: "Shot List — Meet Vesta"
series: entity-intro
entity: vesta
video: entity-intro-vesta
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Vesta

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.vesta && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm spec count: `ls ~/.vesta/specs/ | wc -l` should return 45 or more
- [ ] Confirm SPEC-033 exists: `ls ~/.vesta/specs/VESTA-SPEC-033-signed-executable-code-blocks.md`
- [ ] `~/.demo-vesta` does NOT exist: `ls ~/.demo-vesta 2>&1` should show error
- [ ] GitHub reachable: `ping -c1 github.com`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
vesta
protocol keeper
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
cd ~/.vesta && head -5 README.md
```

**Expected output:** First 5 lines of Vesta's README — entity name, role, repo link.

**Voice:** First half of Segment 1 VO (who Vesta is, what she does — specs not features).

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

**Voice:** Second half of Segment 1 VO (Vesta sits above the production chain — the standard everything is measured against).

**Technical notes:**
- Let the README output stay on screen while speaking
- Natural pause before moving to Segment 2

---

## Shot 3: Specs Directory Listing

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:05
**Duration:** ~25 seconds

**Commands to type:**
```bash
ls ~/.vesta/specs/ | head -20
```

**Expected output:** First 20 filenames from the specs directory — a wall of spec names.

**Voice:** First half of Segment 2 VO (naming key specs: trust bonds, hook architecture, daemon, dark passenger, signed code blocks).

**Technical notes:**
- Do not rush through the filenames in voice — name 4–5 interesting ones and let the wall of text speak for the rest
- Pause after output before typing next command

---

## Shot 4: Count

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:05–1:30
**Duration:** ~25 seconds

**Commands to type:**
```bash
ls ~/.vesta/specs/ | wc -l
```

**Expected output:** `45` (or higher)

**Voice:** Second half of Segment 2 VO — "Forty-five specs... the spec is the source of truth."

**Technical notes:**
- PAUSE after the number appears on screen — let it land before speaking
- Deliver "forty-five" in voice while number is visible
- This is the anchor for the whole video — do not rush it

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/vesta ~/.demo-vesta
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Vesta right now..." VO from Segment 3.

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
ls ~/.demo-vesta
```

**Voice:** "That's the entity. Files. The whole governance layer, portable."

**Technical notes:**
- Fast shot — just enough to see directory structure exists
- Do not narrate the file names

---

## Shot 7: Volume Reprise

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:10
**Duration:** ~10 seconds

**Commands to type:**
```bash
ls ~/.vesta/specs/ | wc -l
```

**Expected output:** `45` (or higher)

**Voice:** "Forty-five specs. Let's look at the most recent one."

**Technical notes:**
- This is the setup for the spec read — quick beat, then move
- Same pause-after-number rule as Shot 4

---

## Shot 8: Read VESTA-SPEC-033

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:10–2:50
**Duration:** ~40 seconds

**Commands to type:**
```bash
head -20 ~/.vesta/specs/VESTA-SPEC-033-signed-executable-code-blocks.md
```

**Expected output:** YAML frontmatter: status, id, title, type, version, date, owner, description, related-specs.

**Voice:** Segment 4 VO — read the title, read the description line, call out the related-specs cross-references, close with "That web of references is the governance layer. That's what Vesta is."

**Technical notes:**
- Pause after output — let viewer read the description field independently
- Read the description field verbatim — it is precise and makes the case
- The related-specs section is the emotional close — slow down on those three spec numbers
- If `head -20` cuts off before related-specs, use `head -25`

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/vesta
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
- `wc -l` returns fewer than 45 — confirm git pull was run
- VO stumble on the SPEC-033 description line (practice it — it's dense)

---

## Total Shot Count: 8 + 2 cards = 10 units
