---
title: "Shot List — Meet Sibyl"
series: entity-intro
entity: sibyl
video: entity-intro-sibyl
production-owner: rufus
hardware: thinker (primary, SSH to fourty4 for invocation)
status: production-ready
---

# Shot List: Meet Sibyl

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt stripped: `$ ` only
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.sibyl && git pull` in a SEPARATE terminal before recording
- [ ] Research directory populated: `ls ~/.sibyl/research/ | wc -l` > 0
- [ ] `sibyl` command reachable: `which sibyl`
- [ ] `ssh fourty4 echo ok` — confirm fourty4 reachable before starting
- [ ] `~/.demo-sibyl` does NOT exist: `ls ~/.demo-sibyl 2>&1`
- [ ] GitHub reachable: `ping -c1 github.com`
- [ ] OBS or screen recorder armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, test sentence, no echo

### Fallback Decision
- [ ] If `ssh fourty4` fails at recording time, switch to fallback Segment 4 (existing research file)
- [ ] Know which fallback file to use: `ls ~/.sibyl/research/ | tail -1`

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
sibyl
research director
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
cd ~/.sibyl && head -5 README.md
```

**Expected output:** Entity name, role, repo URL, first description line.

**Voice:** First half of Segment 1 VO — what Sibyl does and does not do.

---

## Shot 2: Team Position

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:20–0:40
**Duration:** ~20 seconds

**Screen:** Static output on screen. No new typing.

**Voice:** Second half of Segment 1 VO — Juno → Sibyl → Veritas → team pipeline position.

---

## Shot 3: Research Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:00
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.sibyl/research/ | tail -5
```

**Expected output:** 5 most recent research files, date-named.

**Voice:** First half of Segment 2 VO — GitHub Issues → committed briefs, date-named files.

**Technical notes:**
- `tail -5` avoids overwhelming the screen if directory is large
- If fewer than 5 files exist, `ls` without tail is fine

---

## Shot 4: Briefing Template

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:00–1:30
**Duration:** ~30 seconds

**Commands to type:**
```bash
head -10 ~/.sibyl/BRIEFING_TEMPLATE.md
```

**Expected output:** Template header showing question / context / findings / conclusion structure.

**Voice:** Second half of Segment 2 VO — every brief has a decision recommendation, deepseek-r1 8b, $0/query, 128k context.

**Technical notes:**
- If BRIEFING_TEMPLATE.md doesn't exist at record time, substitute:
  ```bash
  head -20 ~/.sibyl/research/$(ls ~/.sibyl/research/ | head -1)
  ```
  and describe the output structure live

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/sibyl ~/.demo-sibyl
```

**Expected output:** Standard git clone progress.

**Voice:** Segment 3 VO — clone = research director on disk, templates, output, calendar.

**Technical notes:**
- Type clone URL slowly, read it aloud
- Let git output scroll naturally

---

## Shot 6: ls Demo Directory

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:55–2:00
**Duration:** ~5 seconds

**Commands to type:**
```bash
ls ~/.demo-sibyl
```

**Voice:** "Files on disk. No API. No subscription. No kill switch."

---

## Shot 7: Live Invocation (PRIMARY path)

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:35
**Duration:** ~35 seconds (including inference wait)

**Commands to type:**
```bash
PROMPT="What are the top 3 reasons developers clone open source tools instead of subscribing to SaaS equivalents? Two sentences max per reason." sibyl
```

**Expected output:** Three numbered findings, two sentences each.

**Voice:**
- During wait (if >5s): "She's running on local inference right now. Watch what comes back."
- After output: "Three findings. Two sentences each. Sibyl doesn't pad, she concludes."

**Technical notes:**
- Do not cut the inference wait — it's part of the story (local model, real compute)
- If inference exceeds 25 seconds, something is wrong — stop and investigate before retaking
- If output is longer than 10 lines, that's acceptable — let it scroll

---

## Shot 7 (FALLBACK path — use if fourty4 offline)

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:35

**Commands to type:**
```bash
ls ~/.sibyl/research/ | tail -5
cat ~/.sibyl/research/$(ls ~/.sibyl/research/ | tail -1) | head -25
```

**Voice:** Fallback VO from script — describe the file, read conclusion section if visible.

---

## Shot 8: Git Log Proof

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:35–2:50
**Duration:** ~15 seconds

**Commands to type:**
```bash
git -C ~/.sibyl log --oneline -3
```

**Expected output:** 3 recent commit hashes + messages showing research brief commits.

**Voice:** "Committed. Every brief is a permanent record. That's Sibyl."

**Technical notes:**
- This is the closing punctuation of the demo — let it sit for 2–3 seconds after VO
- If using fallback path, this shot proves the files shown were committed, not just typed

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/sibyl
koad.sh
```

**Voice:** None.

---

## Retake Triggers

- Background noise in voice track
- Visible typing error requiring correction
- `git clone` fails or hangs
- Sibyl invocation errors out (non-inference error)
- Output structure doesn't match described format (very unlikely with constrained prompt)
- VO stumble on "deepseek-r1 at 8 billion parameters" — practice this phrase

---

## Total Shot Count: 8 + 2 cards = 10 units
