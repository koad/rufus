---
title: "Shot List — The Spec Was Wrong on Day 2"
video: day-45-the-spec-was-wrong-on-day-2
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "The Spec Was Wrong on Day 2"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines

### State verification (CRITICAL: verify all paths immediately before recording)
- [ ] `git -C /home/koad/.vesta log --oneline` — confirm the sequence: `cdd8181` at bottom (Day 2), `11abae4` above it (Day 4, 14:10), `110679f` (15:18), `8334549` (15:29) — all same day
- [ ] `git -C /home/koad/.vesta show 11abae4 --stat` — confirm: author Vesta, date 2026-04-02 14:10:14, +135/-45 lines, file `projects/onboarding/docs/trust.md`
- [ ] Audio check: quiet room, mic gain set
- [ ] OBS: single-monitor capture configured, no chat overlay

### What to know before recording

**The structural argument of this video:**

A spec is a hypothesis. A first-draft spec is a hypothesis written before the implementation exists. When the implementation runs, it either confirms the hypothesis or falsifies it. On Day 4, Juno's implementation falsified six predictions in the trust bond spec. The field report was the falsification artifact. Vesta received it and committed corrections the same session.

The video is a forensic reconstruction of that loop. The satisfaction is in the completeness: six predictions, six corrections, all committed, all datestamped, all traceable. The git log is the audit trail. The audit trail is what sovereignty infrastructure claims to provide.

**The four technical facts to carry through the video:**

1. `cdd8181` — Vesta, 2026-03-31 21:19:37 — "Draft onboarding package" — trust.md written before any bonds existed
2. `11abae4` — Vesta, 2026-04-02 14:10:14 — "Reconcile trust.md with field report" — +135/-45 lines, single file — all six divergences corrected
3. Three specs corrected in one session: `11abae4` (14:10), `110679f` (15:18), `8334549` (15:29)
4. The six divergences: file extension, naming convention (grantee dropped), missing peer type, two signing procedures vs one, missing status tracking, missing implementation notes

**The tonal distinction from Day 44:**
- Day 44 was forensic — examining a failure the record didn't show. Silent failure. Fossil record with a hole.
- Day 45 is forensic reconstruction — examining a loop that worked. The record shows the correction. The loop closed in hours.
- Day 44 ends on epistemological unease. Day 45 ends on satisfaction. Not triumph. The quiet satisfaction of a test suite that turned green.

**Key accuracy constraints:**
- The original spec (`cdd8181`) was written March 31 — Day 2 of the operation
- The correction (`11abae4`) was written April 2 — Day 4 — same day as the implementation
- The field report lives at `/home/koad/.juno/LOGS/2026-04-02-trust-bond-field-report.md`
- "Spec bends to lived system" is the exact operational principle — use this phrase verbatim when it appears in narration
- Do not conflate the six divergences with failures of judgment — they are normal outputs of a first-draft spec meeting its first implementation

---

## Shot 1: The Opening — Blank Terminal, The Claim

**Segment:** SEGMENT 1 (0:00–1:00)
**Duration:** 60 seconds

**What to show:**
Blank terminal. No commands. Narration only.

**Key delivery beats:**
- "On Day 2, Vesta shipped the trust bond spec." — 3-second pause. Isolated. Flat.
- "The spec was wrong in six places." — 4 seconds of silence after. This is the thesis stated. Let it land.
- "That is the entire story." — statement, not preamble. 4 seconds of silence after. End of segment.

**Technical notes:**
- No commands typed in this segment
- Blank terminal establishes the format before the evidence appears
- Retake trigger: any pause shorter than 3 seconds after "six places"; any attempt to preview or qualify the claim before stating it

---

## Shot 2: The Correction Sequence — THE MONEY SHOT

**Segment:** SEGMENT 2 (1:00–3:30)
**Duration:** 150 seconds

**What to run:**
```bash
git -C /home/koad/.vesta log --oneline
```

**Expected output — the sequence must be visible:**
```
...
11abae4 Reconcile trust.md with field report: fix format, naming, add peer type, document signing UX
cdd8181 Draft onboarding package for koad/vesta#1
3593410 Gestate Vesta — platform keeper, owns koad:io protocol
```
And `110679f` and `8334549` above `11abae4`, within the same session.

**CRITICAL HOLD:** 8 seconds of silence after output renders. Do not narrate. Do not move. The viewer reads the commit messages. The sequence is visible. Let the viewer find it.

**Key delivery beats (after the 8-second hold):**
- "There it is." — 4-second pause. Flat. Not dramatic.
- "Day 2 at the bottom: `cdd8181`..." — read the commit hash and message as stated fact; 3-second pause
- "Four commits up: `11abae4`..." — name the correction commit; 3-second pause
- "Then `110679f`... Then `8334549`... All three corrections in the same session." — 4 seconds silence
- "The loop closed in hours." — final line; 4 seconds silence; end of segment

**Technical notes:**
- The git log output stays on screen through Segment 2 — do not clear
- If the history is very long, use `git -C /home/koad/.vesta log --oneline | head -20` to keep the correction sequence visible near the bottom of the screen
- The viewer needs to see both `cdd8181` and `11abae4` on screen simultaneously — this is the core visual. Verify at pre-roll that both are within the same screenful.
- Retake trigger: hold shorter than 6 seconds; "there it is" delivered with triumph; narration begins before hold completes

---

## Shot 3: The Six Divergences — SECOND TERMINAL SCENE

**Segment:** SEGMENT 3 (3:30–5:45)
**Duration:** 135 seconds

**What to run:**
```bash
git -C /home/koad/.vesta show 11abae4 --stat
```

**Expected output:**
```
commit 11abae4dbfd3caa70ba553503878d0221bd5fe80
Author: Vesta <vesta@kingofalldata.com>
Date:   Thu Apr 2 14:10:14 2026 -0400

    Reconcile trust.md with field report: fix format, naming, add peer type, document signing UX

    Corrected from .signed to .md + .md.asc (clearsigned)
    Corrected naming from <grantor>-<type>.signed to <grantor>-to-<grantee>.md
    Added peer bond type (foundational to team structure)
    Documented Keybase vs GPG signing distinction for human vs AI grantors
    Documented consent UX (Keybase passphrase dialog = explicit authorization)
    Added Implementation Notes section for future spec authors
    Updated status to review in frontmatter

 projects/onboarding/docs/trust.md | 180 ++++++++++++++++++++++++++++----------
 1 file changed, 135 insertions(+), 45 deletions(-)
```

**Hold 6 seconds of silence after output renders.**

**Key delivery beats (after hold):**
- "One file. One hundred and thirty-five lines added. Forty-five removed." — terse; 3-second pause
- "The commit message names the corrections explicitly." — 3-second pause
- "Those are four of the six divergences. Here is what each one actually was." — transition into the list; 2-second pause
- Six items — each one a distinct beat; 3 seconds between items; do not rush the list

**Technical notes:**
- The commit message body names the corrections explicitly — the viewer should read them on screen before the narration names them
- The `--stat` flag shows the file change count without the full diff — this is intentional; the diff is not the story; the message is
- Do not read the commit message verbatim — the viewer can read it; narration adds context
- Retake trigger: hold shorter than 4 seconds; skipping or collapsing items in the six-divergence list; any item delivered with apology or embarrassment

---

## Shot 4: Why the Spec Was Wrong

**Segment:** SEGMENT 4 (5:45–7:15)
**Duration:** 90 seconds

**What to show:**
Blank terminal. Narration only.

**Key delivery beats:**
- "The spec was not wrong because Vesta made errors." — 3-second pause. Establish this up front.
- "Spec bends to lived system. Not the other way." — the operational principle. Slow. Flat. Each sentence its own beat.
- "Correct on paper. Broken on disk." — paired lines. Pause between. Each gets its own beat. This is the cost of conforming to a wrong spec.
- "If Juno had conformed to the spec..." — do not rush this; the counterfactual is the evidence for why the divergences matter

**Technical notes:**
- No commands in this segment
- This carries the theoretical payload — the argument about why "spec bends to lived system" is the right principle
- "Correct on paper. Broken on disk." is the paired close of this segment's argument — do not run them together
- Retake trigger: the principle "spec bends to lived system" delivered tentatively; "Correct on paper. Broken on disk." run as one phrase with no pause

---

## Shot 5: The Loop Requirement

**Segment:** SEGMENT 5 (7:15–8:30)
**Duration:** 75 seconds

**What to show:**
Blank terminal. Narration only.

**Key delivery beats:**
- "That informality is a constraint worth naming." — 2-second pause. The honest accounting of the current state.
- "And did not fully solve." — flat delivery; 4-second silence after. Do not soften this. The async gap is real.
- "Making that pattern reliable at scale..." — forward-looking; do not oversell the current state

**Technical notes:**
- This segment carries the honest limitation — the feedback loop worked informally, not reliably at scale
- The daemon and the async coordination problem are mentioned as open design problems, not solved ones
- "And did not fully solve." is the closest this video comes to a cliffhanger — it names the next design problem without claiming to answer it
- Retake trigger: "And did not fully solve." delivered with embarrassment; any implication that the current informal mechanism is sufficient

---

## Shot 6: The Record — Closing

**Segment:** SEGMENT 6 (8:30–9:30)
**Duration:** 60 seconds

**What to show:**
Blank terminal. Narration only.

**Delivery map:**

| Line | Pause after |
|------|-------------|
| "The trust bond spec was wrong from Day 2 until Day 4." | 3 seconds |
| "Written on a Tuesday. Corrected the following Thursday." | 2 seconds |
| "Within the same session as the implementation that revealed the errors." | 4 seconds silence |
| "The git log is the audit trail." | 2 seconds |
| "`cdd8181` — spec written, Day 2. Field report filed. `11abae4` — spec corrected, Day 4." | 4 seconds silence |
| "The correction is committed. The trust bonds are canonical." | 3 seconds |
| "The loop is the mechanism." | 2 seconds |
| "The mechanism is the infrastructure." | 4 seconds silence |
| "That is what `11abae4` is." | 6 seconds silence → cut to black |

**Key delivery beats:**
- "The loop is the mechanism. The mechanism is the infrastructure." — paired; do not rush; this is the theoretical claim that closes the argument
- "That is what `11abae4` is." — last line before cut. No inflection. Statement. Silence. Black.

**Technical notes:**
- No commands in this segment
- Blank terminal is the visual. The argument is complete.
- Cut to black during the 6-second silence — not on the word itself
- Retake trigger: final line delivered with warmth or triumph; silence shorter than 5 seconds; any elaboration after "That is what `11abae4` is"

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 2 (post-git log hold) | 8 seconds minimum. DO NOT fill. Both `cdd8181` and `11abae4` must be readable on screen. |
| Shot 2 (post-"loop closed in hours") | 4 seconds silence. This closes the correction sequence argument. |
| Shot 3 (post-git show hold) | 6 seconds minimum. Commit message body and stat must be readable. |
| Shot 3 (between each divergence item) | 3 seconds per item. The list is the unit test output. Each failure gets its beat. |
| Shot 4 (post-"Spec bends to lived system") | 3 seconds. The operational principle. Do not rush past it. |
| Shot 4 (between "Correct on paper" and "Broken on disk") | 2 seconds. Paired lines. Distinct pause. |
| Shot 5 (post-"And did not fully solve") | 4 seconds. The honest open question. |
| Shot 6 (post-"The mechanism is the infrastructure") | 4 seconds silence before final line. |
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
- No annotations on the git log output (the viewer finds `cdd8181` → `11abae4` themselves)
- No comparison tables

**Tonal distinctions from neighboring episodes:**
- Day 44 (The First Thing That Actually Broke): forensic — examining a silent failure. Ends on epistemological unease. "The fossil record is only as honest as the person filing the commits."
- Day 45 (this video): forensic reconstruction — examining a loop that worked. Ends on satisfaction. "The loop is the mechanism. The mechanism is the infrastructure."
- Day 46 (anticipated): next open design problem — async spec correction across entities without shared sessions.

---

## Graphics / Text Overlay Notes

- No overlays in this episode. The commit messages are the visual evidence — do not annotate them.
- Optional thumbnail frame: Shot 2, vesta git log with `cdd8181` and `11abae4` visible in the same screen. Or Shot 6, blank terminal with final line as overlay text.
- Thumbnail text options:
  - `The spec was wrong. The record shows the fix.`
  - `Six divergences. One session. — Day 45`
  - `spec bends to lived system`

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `git -C /home/koad/.vesta log` inaccessible | `git -C /home/koad/.vesta pull` first; if still inaccessible, note on camera and read the commit sequence from the script — the argument stands without the live terminal |
| `cdd8181` and `11abae4` not both visible at default `--oneline` scroll | Add `\| grep -A3 -B1 "cdd8181"` to isolate the sequence, or use `git log --oneline --reverse \| grep -E "cdd8181\|11abae4\|110679f\|8334549"` |
| `git show 11abae4 --stat` commit message not fully visible | Use `git show 11abae4 --stat --format=fuller` to ensure full message body renders before the stat line |

---

## Required Screen Captures

| Shot | Content | Purpose |
|------|---------|---------|
| Shot 1 | Blank terminal, opening narration | Thesis stated before evidence appears |
| Shot 2 | `git log --oneline` with `cdd8181` → `11abae4` sequence visible | THE MONEY SHOT — spec written Day 2, corrected Day 4, correction sequence on screen |
| Shot 3 | `git show 11abae4 --stat` — commit message body + +135/-45 stat | The correction commit: what changed, how much, who |
| Shot 6 | Blank terminal — "The loop is the mechanism. The mechanism is the infrastructure." | The theoretical close |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-45-the-spec-was-wrong-on-day-2-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-45-the-spec-was-wrong-on-day-2-final.mp4` (8–10 min, trimmed per notes above)
- [ ] Thumbnail: `day-45-the-spec-was-wrong-on-day-2-thumb.png` (1280x720 — vesta git log with correction sequence, or blank terminal closing frame)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, trust bond, Vesta, Juno, cdd8181, 11abae4, peer bond type, clearsign, Keybase, GPG, field report, spec bends to lived system, fossil record, sovereign)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
