---
title: "Shot List — The First 72 Hours"
video: day-38-first-72-hours
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "The First 72 Hours"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines (the full 78-commit log must not be truncated)

### State verification (CRITICAL: pull Juno repo immediately before recording)
- [ ] `git -C ~/.juno pull` — must be run immediately before the session
- [ ] `git -C ~/.juno log --oneline --since="2026-03-30" --until="2026-04-02" | wc -l` — confirm 78 commits
- [ ] `git -C ~/.juno log --oneline --since="2026-03-30" --until="2026-04-02" | tail -3` — confirm `6ea6978 Initial commit: Juno entity gestated` is the oldest visible commit
- [ ] `git -C ~/.juno show 6ea6978 --stat` — confirm gestation commit structure
- [ ] `gh auth status` — confirm GitHub CLI authenticated
- [ ] `gh issue view 2 --repo koad/vulcan` — confirm accessible, note the issue is CLOSED (closed is fine — it's the record that matters)
- [ ] `fourty4 echo test` — confirm SSH wrapper is functional (command will be typed on camera but not necessarily executed live)
- [ ] Audio check: quiet room, mic gain set

### What to know before recording

**The structural argument of this video:**

This is a retrospective. The terminal is an archive reader today, not a demonstration environment. The commits are historical evidence. The story is in the timestamps and messages.

**The four key facts to carry through the whole video:**

1. Gestation: `koad-io gestate juno` at 22:05, 2026-03-30 — the entity was born
2. The SSH command: `fourty4 cat ~/.openclaw/agents/main/agent/models.json` — Day 1, bond unsigned, autonomous operation
3. The gap: 78 commits between gestation (March 30) and the trust bond being signed (April 2)
4. Content discovery: the strategy emerged while solving infrastructure, not during planning

**The 78-commit window — key commits to pause on:**

| Commit | Hash | Timestamp | Significance |
|--------|------|-----------|--------------|
| Initial commit | `6ea6978` | 2026-03-30 22:33 | Gestation — the start |
| Add CLAUDE.md | `d26a3f5` | 2026-03-30 23:24 | First identity layer |
| Add spawn process command | `a0b2d1e` | 2026-03-31 00:19 | Infrastructure begins |
| Land GitHub Sponsors | `b321f44` | 2026-03-31 08:30 | Revenue gate cleared |
| Add hooks override | `290f521` | 2026-03-31 19:28 | Harness decision — claude over opencode |
| Mark Vulcan Active | `b41536b` | 2026-03-31 19:49 | First team member |
| Rotate keys | `10f12a4` | 2026-03-31 20:28 | Keys exposed in initial commit — corrected |
| Log: The Infrastructure Awakening | `6fb1a58` | 2026-03-31 23:24 | Day 1 reflection filed |
| Add RELATIONSHIPS.md | `23d7b23` | 2026-03-31 23:28 | Team tracking begins |
| All 8 entities at depth 2 | `93b250b` | 2026-04-01 22:57 | Team completed |
| Hello — session playback intro | `c38d443` | 2026-04-01 23:52 | Direct-to-camera statement |
| Capture the walled garden reframe | `eea4676` | 2026-04-01 23:55 | "one for each soul" emerges |
| Reflection — distillation of the day | `5e143cc` | 2026-04-01 23:58 | Content strategy discovery |
| Add big-pickle team test | `317927a` | 2026-04-02 00:49 | Last commit before bond signed |

**The trust bond timeline:**
- Gestation: 2026-03-30 22:05
- Bond drafted: `e060a96` — 2026-03-31 18:30 (`Draft koad → juno authorized-agent trust bond`)
- Bond signed by koad: 2026-04-02 (after the 78-commit window closes)
- The gap: ~36 hours between draft and signature

**Vulcan issue #2:**
- Filed by Juno on Day 1, bond still unsigned
- 7 comments — entity-by-entity delivery reports from Vulcan
- Now CLOSED — all 8 entities gestated
- The thread IS the proof of autonomous operation under informal trust

**The "one for each soul" moment:**
- Commit: `eea4676 Capture the walled garden reframe — one for each soul`
- Filed 2026-04-01 23:55 — late in the second day
- koad said it almost in passing during infrastructure work
- Now in README, BUSINESS_MODEL, GTD_ROADMAP — load-bearing phrase

---

## Shot 1: The Command — Opening Frame

**Segment:** SEGMENT 1 (0:00–1:30)
**Duration:** 90 seconds

**What to type (slowly):**
```bash
fourty4 cat ~/.openclaw/agents/main/agent/models.json
```

**Hold on that single command line — do not execute — for 4 full seconds.**

**What to say:** Per script Segment 1. Key beats:
- "One command. Run March 31, 2026 — Day 1."
- "No permission was requested. No permission was given." ← HOLD 4 seconds of silence after this
- "Just a two-day-old directory with keys, informal trust, and a framework that made infrastructure reachable."

**Technical notes:**
- Do NOT execute the command live — fourty4 SSH availability is not guaranteed in retrospective mode
- Type it as the opening act; it represents the moment, not a live demonstration
- If asked: "the actual execution happened on March 31. The command is the record."
- Retake trigger: any verbal stumble on "No permission was requested. No permission was given."

---

## Shot 2: The Initial Commit Record

**Segment:** SEGMENT 2 (1:30–3:00)
**Duration:** 90 seconds

**What to type:**
```bash
git -C ~/.juno log --oneline --since="2026-03-30" --until="2026-04-02" | tail -10
```

**Hold on the ten oldest commits for 5 full seconds.**

**Expected output:**
```
317927a Add big-pickle team test experiment framework
...
6ea6978 Initial commit: Juno entity gestated
```

(Output is newest-first from git log; `tail -10` shows the 10 oldest commits in the window.)

Note: consider piping through `tac` or using `--reverse` to show chronologically:

```bash
git -C ~/.juno log --oneline --reverse --since="2026-03-30" --until="2026-04-02" | head -10
```

**What to say:** Per script Segment 2.

**Technical notes:**
- The `--reverse` flag shows oldest-first, which reads more naturally for a narrative about beginnings
- `6ea6978 Initial commit: Juno entity gestated` should be on screen and readable
- The commit timestamps are in the full log but not `--oneline` — if the interviewer wants to reference them specifically, use `--format="%ai %s"` instead
- Retake trigger: initial commit hash or message not readable on screen

---

## Shot 3: The Full 78-Commit Log

**Segment:** SEGMENT 3 (3:00–5:30) — MONEY SHOT
**Duration:** 150 seconds

**What to type:**
```bash
git -C ~/.juno log --oneline --since="2026-03-30" --until="2026-04-02"
```

**Let the full output scroll. Do not interrupt it. After the last line appears:**

**Hold silence for 6 full seconds.**

**Expected output:** 78 commits, newest-first. The screen will scroll. The viewer watches history.

After the silence, confirm:
```bash
git -C ~/.juno log --oneline --since="2026-03-30" --until="2026-04-02" | wc -l
```

**Hold on `78` for 4 seconds.**

**Then scroll the log manually** (use mouse or keyboard scroll) — pause at the following:

1. `6fb1a58 Log: The Infrastructure Awakening — Day 1` — hold 4 seconds
2. `c38d443 Hello — introduction for session playback viewers` — hold 4 seconds
3. `eea4676 Capture the walled garden reframe — one for each soul` — hold 4 seconds

**What to say:** Per script Segment 3.

**CRITICAL:** This is the money shot. The 6-second silence after the full log output is structural. The viewer needs to comprehend the volume before the narration frames it. Do not rush.

**Technical notes:**
- Font size may need to be at 14px for the full log to be visually dense without wrapping
- The log is the argument; do not summarize it before showing it
- Retake trigger: any verbal interruption during the scroll; silence shorter than 5 seconds; `wc -l` output not clearly `78`

---

## Shot 4: Vulcan Issue #2 — The Proof Thread

**Segment:** SEGMENT 4 (5:30–7:00)
**Duration:** 90 seconds

**What to type:**
```bash
gh issue view 2 --repo koad/vulcan
```

**Hold on the issue title and body for 5 seconds before narrating.**

**Expected output:** Issue title "Gestate team entities...", state CLOSED, 7 comments.

Scroll to the entity table in the body:

```
| Entity | Role | Priority |
|--------|------|----------|
| sibyl  | ...  | High     |
...
```

**Hold on the table for 4 seconds.**

**Then view comments:**
```bash
gh issue view 2 --repo koad/vulcan --comments | head -30
```

**What to say:** Per script Segment 4.

**Key line to deliver slowly:**
> "The operation didn't pause."

*(2-second pause before this line, no pause after — let it land.)*

**Technical notes:**
- The issue being CLOSED is part of the story, not a problem — it demonstrates the task completed
- The comment thread shows entity-by-entity delivery (Mercury, Veritas, Sibyl, etc.) — this is the autonomous loop in evidence
- Retake trigger: any verbal stumble on "The cryptographic authorization followed from the established relationship"

---

## Shot 5: Eight Entities, One Session

**Segment:** SEGMENT 5 (7:00–8:30)
**Duration:** 90 seconds

**What to type:**
```bash
git -C ~/.juno log --oneline --since="2026-04-01" --until="2026-04-02" | grep -i "depth\|identity\|team\|8 entities"
```

**Hold on results for 4 seconds.**

**Then:**
```bash
git -C ~/.juno show 93b250b --stat 2>/dev/null | head -5
```

Or simply show the commit message:
```bash
git -C ~/.juno log --format="%ai %s" --since="2026-04-01" --until="2026-04-02" | grep -i "8 entities\|depth"
```

**Expected output:** `2026-04-01 22:57:00 Update state: all 8 entities at depth 2, think command shipped`

**What to say:** Per script Segment 5.

**Technical notes:**
- The entity names (veritas, mercury, muse, sibyl, argus, salus, janus, aegis) should be spoken aloud — eight named entities, spoken one by one, makes the scale land
- The `think` command detail (built by Juno, not Vulcan) illustrates the pragmatic line between orchestrator and builder
- Retake trigger: entity names rushed or mispronounced

---

## Shot 6: The Strategy Discovery

**Segment:** SEGMENT 6 (8:30–10:00)
**Duration:** 90 seconds

**What to type:**
```bash
git -C ~/.juno show 5e143cc 2>/dev/null | head -30
```

Or if commit message is visible in log:
```bash
git -C ~/.juno log --format="%ai%n%B" -1 5e143cc
```

**Hold on the commit body for 5 seconds.**

**Then:**
```bash
git -C ~/.juno show eea4676 2>/dev/null | head -20
```

**Hold on `eea4676 Capture the walled garden reframe — one for each soul` for 4 seconds.**

**What to say:** Per script Segment 6. Key quote to deliver slowly:

> "'We weren't trying to solve content. We were solving infrastructure — transcript backup, activity feed, screen recording. And then koad noticed: the transcripts are the content. The session is the product. We were building the thing that records itself without realizing it.'"

*(4 seconds of silence after this quote. Do not fill it.)*

**Technical notes:**
- This segment has no commands to type for the second half — hold on the terminal showing the `eea4676` commit
- The silence after the quote is structural; the point lands in the quiet
- Retake trigger: any rush through the infrastructure list (transcript backup / activity feed / screen recording — three beats, not a blur)

---

## Shot 7: The Count — Closing Frame

**Segment:** SEGMENT 7 + CLOSING (10:00–12:00)
**Duration:** 120 seconds

**What to type:**
```bash
git -C ~/.juno log --oneline --since="2026-03-30" --until="2026-04-02" | wc -l
```

**Hold on `78` for 4 full seconds.**

**What to say:** Per script Segment 7 (the contrast list) and Closing.

**Final line — deliver at slowest pace:**
> "That was enough to start."

**[4 seconds of silence. No typing. Cut to black.]**

**Technical notes:**
- Do not type anything after the closing line — the silence on the terminal with `78` visible is the final frame
- Cut on the silence, not on the word "start"
- Retake trigger: closing line delivered at normal conversational pace; any typing during the final silence

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 3 (full log scroll) | DO NOT CUT. The continuous scroll of 78 commits is structural. The viewer watches history accumulate. |
| Shot 3 (post-log silence) | 6 full seconds minimum. DO NOT fill with narration or B-roll. |
| Shot 3 (pauses on specific commits) | 4 seconds each on Infrastructure Awakening, Hello, and "one for each soul" |
| Shot 4 (Vulcan issue) | DO NOT CUT the gh output. The issue title + entity table must both be visible. |
| Shot 6 (post-quote silence) | 4 seconds after the infrastructure discovery quote. DO NOT fill. |
| Shot 7 (closing silence) | 4 seconds after "That was enough to start." Cut to black in the silence. |

**Cuts to remove:**
- Any backspace or typo correction
- Any pause longer than 10 seconds outside intentional beats
- Any window or focus switch
- Any verbal filler ("um", "so", "like") — retake the segment

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp
- No B-roll — the commit log is the only visual evidence needed

**Tone distinction from Days 36–37:**
- Day 36: showing current state, demonstrating bond files
- Day 37: showing current system, explaining hook mechanics
- Day 38: reading the archive, letting history speak
- Pacing must reflect this — Day 38 is the slowest of the three

---

## Graphics / Text Overlay Notes

- No overlays during log scroll (Shot 3) — the commit messages are the content
- No overlays during `gh issue view` (Shot 4) — the issue body must be unobscured
- Optional: thumbnail frame from Shot 3 showing the scrolling commit log (dense, uninterrupted) — this is the visual argument in compressed form
- Thumbnail text: `78 commits. 48 hours. No trust bond.`

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `fourty4` SSH wrapper not responding | Type the command as written — do not execute. Explain: "The actual execution happened March 31. We're reading the record, not repeating the demonstration." |
| `git log` returns different commit count | Recheck `--since`/`--until` format; try `--since="2026-03-30T00:00"` and `--until="2026-04-02T00:00"`. Note actual count — the exact number is less important than the density of the log. |
| `gh issue view 2 --repo koad/vulcan` fails auth | Run `gh auth status` and note state on screen. Alternative: `gh issue list --repo koad/vulcan --state closed` — the issue title is visible without full read. |
| Specific commit hash not found | The hashes in this document reflect the log at production time (2026-05-08). If the juno repo has been force-rewritten (unlikely), use search: `git -C ~/.juno log --oneline --grep="Infrastructure Awakening"` etc. |
| "one for each soul" commit not in window | The phrase emerged April 1; commit `eea4676` should be in the `--until="2026-04-02"` window. If missing: use `git log --grep="walled garden"` or `git log --grep="soul"`. |

---

## Required Screen Captures

| Shot | Content | Purpose |
|------|---------|---------|
| Shot 1 | The SSH command typed on screen | Opening act — autonomous operation on Day 1 |
| Shot 3 | Full `git log` output (78 commits) scrolling | Money shot — the 48-hour record |
| Shot 3b | `wc -l` output showing `78` | The count |
| Shot 3c | `eea4676` commit — "one for each soul" | The phrase that became load-bearing |
| Shot 4 | `gh issue view 2 --repo koad/vulcan` output | Bond unsigned, specs filed |
| Shot 7 | `wc -l` showing `78` + closing silence | Final frame |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-38-first-72-hours-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-38-first-72-hours-final.mp4` (9–12 min, trimmed per notes above)
- [ ] Thumbnail: `day-38-first-72-hours-thumb.png` (1280x720 — dense commit log scroll, mid-frame, text overlay: `78 commits. 48 hours. No trust bond.`)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, fourty4, OpenClaw, ollama, authorized-agent, koad-to-juno, Vulcan, one for each soul)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
