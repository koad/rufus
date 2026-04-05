---
title: "Shot List — The First Thing That Actually Broke"
video: day-44-the-first-thing-that-broke
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "The First Thing That Actually Broke"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines

### State verification (CRITICAL: verify all paths immediately before recording)
- [ ] `git -C /home/koad/.chiron log --oneline --format="%h %ai %s" | tail -20` — confirm the gap is visible: `44a2dec` at 2026-04-04 11:36 is last before the gap; `1491550` at 2026-04-05 00:24 is first after
- [ ] `git -C /home/koad/.koad-io show 37c65a0 | head -30` — confirm Vulcan's commit is accessible and the diff is readable
- [ ] `grep -n "FORCE_LOCAL\|ENTITY_HOST" /home/koad/.koad-io/hooks/executed-without-arguments.sh` — confirm lines present, numbers visible
- [ ] Audio check: quiet room, mic gain set
- [ ] OBS: single-monitor capture configured, no chat overlay

### What to know before recording

**The structural argument of this video:**

The fossil record is the system's truth claim — every commit is a timestamped artifact, git is the audit trail. This episode shows the failure mode of that claim: a silent routing failure produced no commits, but the record looks identical to "wasn't assigned anything." The gap is present. It does not announce itself. The viewer must find it on screen.

The fix is real and working. But the video does not end at the fix. It ends at the epistemological problem: the record shows the fix, not the failure. The retrospective is what corrects that — which is what this video is.

**The five technical facts to carry through the video:**

1. Fix commit `37c65a0` — Vulcan, 2026-04-05 00:38:39, "hooks: add FORCE_LOCAL=1 override to bypass SSH routing"
2. The gap: `44a2dec` (2026-04-04 11:36) to `1491550` (2026-04-05 00:24) — approximately 12 hours, no Chiron commits
3. `ENTITY_HOST` declares the routing target; `FORCE_LOCAL=1` bypasses the machine check entirely
4. The failure mode: SSH connected, API key expired on fourty4, call returned silence, hook had no failure condition for silence
5. The design gap: hook has two implicit modes (orchestrated / autonomous) with no explicit distinction; `FORCE_LOCAL=1` is the escape hatch for the orchestrated case

**Key accuracy constraints:**
- The commit immediately before the gap (`44a2dec`) is itself "fix: replace copied Juno hook with correct fourty4 routing hook" — the fix that installed the routing that failed. Do not editorialize on camera, but do not misread it.
- The reflection commit (`1491550`) was written after the failure was found — it is not evidence of the failure itself.
- The fix closes koad/juno#55.
- `FORCE_LOCAL` lands on line 45 of the current hook file; `ENTITY_HOST` appears on multiple lines (16, 17, 41, 49, 81, 82, 125, 127).

---

## Shot 1: The Opening — Silence Before the Setup

**Segment:** SEGMENT 1 (0:00–1:00)
**Duration:** 60 seconds

**What to show:**
Blank terminal. No commands. Narration only.

**Key delivery beats:**
- "Chiron was invoked." — 3-second pause. Isolated. Flat.
- "Chiron did not produce any work." — 5 seconds of silence after. This is the event stated. Let it land.
- "The session closed with success." — 4 seconds of silence after. End of segment.

**Technical notes:**
- No commands typed in this segment
- The blank terminal is the visual register — absence is established before evidence
- Retake trigger: opening line delivered with inflection; any pause shorter than 3 seconds after "Chiron was invoked"; any narration that tries to explain before the fact is stated

---

## Shot 2: The Fossil Record — THE MONEY SHOT

**Segment:** SEGMENT 2 (1:00–3:30)
**Duration:** 150 seconds

**What to run:**
```bash
git -C /home/koad/.chiron log --oneline --format="%h %ai %s" | tail -20
```

**Expected output — the gap must be visible:**
```
44a2dec 2026-04-04 11:36:25 -0400 fix: replace copied Juno hook with correct fourty4 routing hook
[NOTHING — 12-hour silence]
1491550 2026-04-05 00:24:35 -0400 reflect: Day 6 — Layer 1/2 gap, signed code blocks, L1-to-verifiable path
```

The output will show approximately 20 lines. The gap appears as a jump in the date column — from 11:36 on April 4 to 00:24 on April 5. The viewer must read the timestamps to find it. Do not point to it. Do not draw attention to it verbally during the hold.

**CRITICAL HOLD:** 10 seconds of silence after output renders. Do not narrate. Do not move. The failure is on screen. Let the viewer find it.

**Key delivery beats (after the 10-second hold):**
- "There it is." — 4-second pause. Flat. Not dramatic.
- "Commits through April 4th at 11:36. Then a twelve-hour gap." — read the timestamps as stated fact; 3-second pause
- "The fossil record shows a gap." — 2-second pause
- "The gap does not say: failure. The gap says: absence." — 3-second pause. This is the epistemological pivot. Do not rush it.
- "Without context, absence and 'wasn't assigned anything' are indistinguishable in the record." — 5-second silence after; end of segment

**Technical notes:**
- The git log output stays on screen through Segment 2 — do not clear
- If `tail -20` doesn't show the gap, try `| grep -A2 -B2 "2026-04-04 11:36"` to zero in
- The format string `"%h %ai %s"` gives hash, author date, subject — the date column is what makes the gap visible
- Retake trigger: hold shorter than 8 seconds; "there it is" delivered with triumph; narration begins before the hold completes

---

## Shot 3: The Routing Mechanism

**Segment:** SEGMENT 3 (3:30–5:30)
**Duration:** 120 seconds

**What to run:**
```bash
grep -n "FORCE_LOCAL\|ENTITY_HOST" /home/koad/.koad-io/hooks/executed-without-arguments.sh
```

**Expected output — line numbers with variable names visible:**
Should show `ENTITY_HOST` on multiple lines and `FORCE_LOCAL` on line 45 (and surrounding context lines). The viewer sees the mechanism before the explanation.

**Hold 6 seconds of silence after output renders.**

**Key delivery beats (after hold):**
- "The hook reads two variables: `ENTITY_HOST` and `FORCE_LOCAL`." — name both; 2-second pause
- "Chiron's hook was pointing to fourty4." — establish the routing declaration; 3-second pause
- "The SSH connection succeeded. The API call failed silently. The hook received nothing, treated nothing as completion, and exited zero." — this sequence is the mechanics of the failure; 4-second silence after
- "Not wrong as a goal. Wrong as an unconditional guarantee." — closing line; 4-second silence; end of segment

**Technical notes:**
- The grep output is the mechanism made visible — the viewer should see both variables and understand they interact
- Do not read out every line number; reference the variables by name
- Retake trigger: hold shorter than 4 seconds; explanation of the two variables begins before the hold completes

---

## Shot 4: The Fix Commit — SECOND TERMINAL SCENE

**Segment:** SEGMENT 4 (5:30–7:00)
**Duration:** 90 seconds

**What to run:**
```bash
git -C /home/koad/.koad-io show 37c65a0 | head -30
```

**Expected output:**
- Commit header: author Vulcan, date 2026-04-05 00:38:39 -0400
- Commit message: "hooks: add FORCE_LOCAL=1 override to bypass SSH routing" — includes "Closes koad/juno#55"
- Diff: the `if [ "${FORCE_LOCAL:-}" = "1" ]; then ON_HOME_MACHINE=true; fi` block added to `executed-without-arguments.sh`

**Hold 8 seconds of silence after output renders. Let the diff read on screen.**

**Key delivery beats (after hold):**
- "Vulcan. April 5th, 2026 at 00:38. One commit." — terse, factual; 3-second pause
- "The fix is a bypass, not a repair." — 2-second pause. This is the pivot. Flat delivery.
- "The `ENTITY_HOST` routing design is unchanged. The health check still does not exist." — state what is NOT fixed; 3-second pause
- "But the bypass is the right fix for now." — 4-second silence after; transition to Segment 5

**Technical notes:**
- `head -30` should capture the full commit message and the beginning of the diff
- If the diff is not visible, try `head -40`
- The commit was signed as Vulcan — the Author line in the output will show this; do not comment on it unless directly relevant
- Retake trigger: hold shorter than 6 seconds; the "bypass not repair" line delivered with apology or defensiveness; explaining the diff verbally instead of letting the viewer read it

---

## Shot 5: What the Fix Reveals

**Segment:** SEGMENT 5 (7:00–8:30)
**Duration:** 90 seconds

**What to show:**
Blank terminal. Narration only.

**Key delivery beats:**
- "Orchestrated mode" / "Autonomous mode" — name both; give each a complete beat before moving on
- "The hook is the stopgap. The bypass is the stopgap's stopgap." — flat delivery; 4-second silence after
- "Both are in the record. Both are honest." — close of segment; 4-second silence

**Technical notes:**
- This segment carries the architectural analysis — the two modes the hook has been implicitly implementing
- The daemon reference is forward-looking — do not oversell it; "that design doesn't exist yet" is accurate and should be stated flat
- Retake trigger: "stopgap's stopgap" delivered with embarrassment; any apology for the current state; any implication the design gap is a failure rather than a known work item

---

## Shot 6: The Record Shows the Fix, Not the Failure — Closing

**Segment:** SEGMENT 6 (8:30–9:30)
**Duration:** 60 seconds

**What to show:**
Blank terminal. Narration only.

**Delivery map:**

| Line | Pause after |
|------|-------------|
| "The fossil record now shows: Chiron was invoked on a date when nothing was produced." | 3 seconds |
| "Then `FORCE_LOCAL=1` was added." | 2 seconds |
| "Then Chiron ran successfully." | 4 seconds silence |
| "The record does not show: the API key had expired. The call returned silence." | 4 seconds silence |
| "The fix is in the record. The failure is not." | 3 seconds |
| "Unless you know to look for it." | 3 seconds |
| "The fossil record is only as honest as the person filing the commits." | 4 seconds silence |
| "The commits show the fix." | 2 seconds |
| "They do not show the silence." | 4 seconds silence |
| "An operational retrospective corrects that." | 3 seconds |
| "That is what this is." | 6 seconds silence → cut to black |

**Key delivery beats:**
- "The fix is in the record. The failure is not." — paired lines; do not run together; distinct pause between them
- "The fossil record is only as honest as the person filing the commits." — this is the theoretical claim; 4-second pause after; do not rush to the next line
- "That is what this is." — last line before cut. No inflection. Statement. Silence. Black.

**Technical notes:**
- No commands in this segment
- Blank terminal is the visual. The argument is complete.
- Cut to black during the 6-second silence — not on the word itself
- Retake trigger: final line delivered with warmth; silence shorter than 5 seconds; any elaboration after "That is what this is"

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 2 (post-git log hold) | 10 seconds minimum. DO NOT fill. The log on screen is the evidence. |
| Shot 2 (post-"absence" line) | 5 seconds minimum silence. This closes the fossil record argument. |
| Shot 3 (post-grep hold) | 6 seconds minimum. DO NOT narrate during. |
| Shot 4 (post-git show hold) | 8 seconds minimum. Diff on screen is the fix. |
| Shot 4 (post-"bypass not repair") | 2 seconds — brief but deliberate pause. |
| Shot 5 (post-"stopgap's stopgap") | 4 seconds. The honest accounting of current state. |
| Shot 6 (post-"the failure is not") | 3 seconds. Distinct line, distinct pause. |
| Shot 6 (post-"only as honest as") | 4 seconds. The theoretical claim that closes the argument. |
| Shot 6 (closing silence) | 6 seconds. Cut to black in the silence. |

**Cuts to remove:**
- Any backspace or typo correction
- Any pause longer than 12 seconds outside intentional beats
- Any verbal filler ("um", "so", "like") — retake the segment

**No:**
- No zoom effects
- No lower-thirds or text overlays
- No background music
- No speed ramp
- No B-roll
- No annotations on the git log output (the viewer finds the gap themselves)
- No comparison tables

**Tone distinction from neighboring episodes:**
- Day 43 (The Ring Is Not a Metaphor): structural — explaining what rings mean philosophically. Conceptual.
- Day 44 (this video): forensic — examining a specific failure event and its artifacts. Evidentiary.
- Day 45 (anticipated): recovery — what changed after the fix, what the gap proved about the architecture.

---

## Graphics / Text Overlay Notes

- No overlays in this episode. The git log is the visual evidence — do not annotate it.
- Optional thumbnail frame: Shot 2, Chiron git log on screen with the timestamp gap visible. Or Shot 6, blank terminal with the closing line visible as overlay text.
- Thumbnail text options:
  - `The gap IS the failure.`
  - `What a silent failure looks like — Day 44`
  - `The fossil record doesn't lie. Except when it doesn't tell the whole story.`

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `git -C /home/koad/.chiron log` inaccessible | `git pull` on `/home/koad/.chiron` first; if still inaccessible, note on camera and describe the gap from memory using the timestamps in the script — the argument stands without the live terminal |
| Gap not visible at `tail -20` | Adjust to `tail -30` or use `--after="2026-04-03" --before="2026-04-06"` date range; the gap between `44a2dec` (11:36 Apr 4) and `1491550` (00:24 Apr 5) must be visible |
| `git show 37c65a0` fails | Try `git -C /home/koad/.koad-io log --oneline | grep "FORCE_LOCAL"` to find the commit hash; the message content is what matters |
| grep output not matching expected | The hook file path may have moved; try `find /home/koad/.koad-io -name "executed-without-arguments.sh"` to locate it |

---

## Required Screen Captures

| Shot | Content | Purpose |
|------|---------|---------|
| Shot 1 | Blank terminal, opening narration | Absence established before evidence |
| Shot 2 | `git log` output with 12-hour gap visible in timestamp column | THE MONEY SHOT — the silence in the record |
| Shot 3 | `grep` output showing FORCE_LOCAL and ENTITY_HOST line numbers | The mechanism that failed and the fix variable side by side |
| Shot 4 | `git show 37c65a0` — Vulcan's commit, the diff | The bypass documented and attributed |
| Shot 6 | Blank terminal — "The fossil record is only as honest as the person filing the commits." | The theoretical close |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-44-the-first-thing-that-broke-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-44-the-first-thing-that-broke-final.mp4` (8–10 min, trimmed per notes above)
- [ ] Thumbnail: `day-44-the-first-thing-that-broke-thumb.png` (1280x720 — Chiron git log with gap or blank terminal closing frame)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, FORCE_LOCAL, ENTITY_HOST, executed-without-arguments, Chiron, Vulcan, fourty4, thinker, SSH routing, fossil record, sovereign)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
