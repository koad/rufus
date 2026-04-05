---
title: "Shot List — Meet Faber"
series: entity-intro
entity: faber
video: entity-intro-faber
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Faber

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username display
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.faber && git pull` done in a SEPARATE terminal before recording
- [ ] Content directory has files: `ls ~/.faber/content/ | wc -l` > 3
- [ ] Target post confirmed: `ls ~/.faber/content/2026-04-05-trust-bonds-arent-policy.md`
  - If not present: note fallback file — `ls ~/.faber/content/ | tail -1`
- [ ] EDITORIAL.md exists: `ls ~/.faber/EDITORIAL.md`
- [ ] `~/.demo-faber` does NOT exist: `ls ~/.demo-faber 2>&1`
- [ ] GitHub reachable: `ping -c1 github.com`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, test sentence

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
faber
content strategist
koad:io ecosystem
```

**Voice:** None.

---

## Shot 1: Identity Read

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:05–0:20
**Duration:** ~15 seconds

**Commands to type:**
```bash
cd ~/.faber && head -5 README.md
```

**Expected output:** Entity name, role, repo, description line.

**Voice:** First half of Segment 1 VO — what Faber is, what the Reality Pillar is, that it's field notes not marketing.

---

## Shot 2: Team Position

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:20–0:40
**Duration:** ~20 seconds

**Screen:** Static output. No new typing.

**Voice:** Second half of Segment 1 VO — Sibyl → Faber → Mercury pipeline, Veritas role, what Faber synthesizes.

---

## Shot 3: Directory Overview

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–0:55
**Duration:** ~15 seconds

**Commands to type:**
```bash
ls ~/.faber/
```

**Expected output:** `content/  content-calendar/  EDITORIAL.md  AUDIENCE_SEGMENTS.md  CALENDAR.md` etc.

**Voice:** First half of Segment 2 VO — this is a strategist's working environment, not a prompt file.

**Technical notes:**
- Pause after output — let viewer see the directory names
- `AUDIENCE_SEGMENTS.md` and `EDITORIAL.md` are differentiating details — let them register visually

---

## Shot 4: Editorial Policy

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:55–1:30
**Duration:** ~35 seconds

**Commands to type:**
```bash
head -5 ~/.faber/EDITORIAL.md
```

**Expected output:** Top of editorial policy document — title, stated purpose, voice rules.

**Voice:** Second half of Segment 2 VO — voice defined, rules for shipping, what Reality Pillar accomplishes, posts as dated committed markdown.

**Technical notes:**
- If head-5 is sparse (just frontmatter), use `head -10`
- Read the document title or stated purpose aloud — it anchors Faber's strategic positioning
- Pause after output before moving to clone

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/faber ~/.demo-faber
```

**Expected output:** Standard git clone progress.

**Voice:** Clone VO — editorial policy, audience profiles, calendar, posts all in git, all yours.

**Technical notes:**
- Type URL slowly, read it aloud
- Let git output scroll

---

## Shot 6: ls Demo Directory

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:55–2:00
**Duration:** ~5 seconds

**Commands to type:**
```bash
ls ~/.demo-faber
```

**Voice:** "Files. No content management system. No subscription."

---

## Shot 7: Posts Directory

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:20
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.faber/content/
```

**Expected output:** List of dated markdown files — one per post. Ideally 8+ files visible.

**Voice:** "Every post Faber has written. Date-named. All committed. You can see the series building in real time."

**Technical notes:**
- This is the visual proof of accumulated output — let it sit on screen for 3+ seconds
- If list is long and wraps, that's ideal — more files = more evidence of real work
- Do not read the file names aloud — let viewer absorb them

---

## Shot 8: Post Header Read

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:20–2:50
**Duration:** ~30 seconds

**Commands to type (primary):**
```bash
cat ~/.faber/content/2026-04-05-trust-bonds-arent-policy.md | head -20
```

**Commands to type (fallback — most recent post):**
```bash
cat ~/.faber/content/$(ls ~/.faber/content/ | tail -1) | head -20
```

**Expected output:** YAML frontmatter (title, status, pillar, description, priority) + first 2–3 lines of post body.

**Voice:** Read the title aloud. State the status, pillar. Read the description field if present. Close: "Content as infrastructure. Every post a commit."

**Technical notes:**
- Pause 3 seconds after output appears — let viewer read before VO continues
- The `description:` YAML field, if present, is the most important line to read aloud
- If output goes past 20 lines, that's fine — let it scroll
- Do not read the entire post body — this is a header read, not a content review

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/faber
koad.sh
```

**Voice:** None.

---

## Retake Triggers

- Background noise in voice track
- Visible typing correction
- `git clone` fails or hangs
- Post file not found (use fallback command instead of retaking)
- VO stumble on "synthesizes research briefs from Sibyl" — practice this phrase before recording
- Output so sparse it doesn't support the described structure (investigate before retaking)

---

## Total Shot Count: 8 + 2 cards = 10 units
