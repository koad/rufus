---
title: "Shot List — The Operations Board"
video: day-33-operations-board
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "The Operations Board"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines

### State verification
- [ ] `git -C ~/.juno pull` — confirm current
- [ ] `cat ~/.juno/OPERATIONS.md | head -80` — confirm issue flow section present
- [ ] `grep "gh issue" ~/.juno/OPERATIONS.md | head -10` — confirm gh commands visible
- [ ] `cat ~/.juno/trust/bonds/koad-to-juno.md | head -50` — confirm reporting protocol section readable
- [ ] Confirm "Koad reviews at his discretion" appears: `grep -n "reviews at his discretion" ~/.juno/trust/bonds/koad-to-juno.md`
- [ ] `grep -A 15 "Blocked on koad" ~/.juno/CLAUDE.md` — confirm six items visible
- [ ] `gh auth status` — confirm GitHub CLI authenticated
- [ ] `gh issue list --repo koad/juno --state open` — dry run, confirm loads
- [ ] OBS armed at 1920x1080, 60fps, black background capture
- [ ] Mic check

### What to know before recording
- Number of entities: 15
- Number of machines: 3
- Number of humans: 1 (koad)
- Governing sentence: "Koad reviews at his discretion. Juno does not wait for approval on in-scope actions."
- Labels in OPERATIONS.md: entity:juno, entity:vulcan, priority:high, type:delegation, type:report, status:blocked
- Number of blocked-on-koad items at time of post: 6
- Trust bond notification channels: 3 (commits, session logs, GitHub Issues)
- VESTA spec section for Agent tool vs. Issues: VESTA-SPEC-054 §7 / §7.3

---

## Shot 1: Empty Terminal — Opening Hook

**Segment:** SEGMENT 1 (0:00–0:30)
**Duration:** ~30 seconds

**What the screen shows:**
- Terminal. Prompt only. Nothing else.

**What to type:** Nothing.

**What to say:**
> "Fifteen entities. Three machines. Work happening at different speeds."
>
> *(pause)* "How does one human know what is happening across all of it — at any moment — without spending his day checking in?"
>
> *(pause)* "Not checkpoints. Not dashboards. Not approval gates."
>
> *(pause)* "A board. And a protocol."
>
> *(pause)* "The board only works because the protocol is real."

**Technical notes:**
- 2–3 second pause after opening terminal before speaking.
- Deliver the oversight question as a real design problem, not rhetoric.
- No keyboard input until Shot 2.
- Retake trigger: any verbal stumble in the first three sentences.

---

## Shot 2: OPERATIONS.md — Issue Protocol Section

**Segment:** SEGMENT 2 (0:30–1:30)
**Duration:** ~60 seconds

**What to type:**
```
cat ~/.juno/OPERATIONS.md | head -80
```

**Expected output:** OPERATIONS.md header and the issue flow / coordination protocol section.

**What to say:**
> "The natural answer to 'how do you watch a distributed system' is: instrument it. Logs. Metrics. A dashboard."
>
> *(pause)* "koad:io gives a different answer: make every consequential action produce a GitHub Issue, or a comment on one."
>
> *(pause)* "Metrics capture state at a moment. They age out."
>
> *(pause)* "A GitHub Issue that was opened six days ago and is still open is a standing signal. It has not aged out."

**Technical notes:**
- Pause 3 seconds on the file output before speaking.
- If "launch, observe, decide" or "GitHub Issue" language appears in the first 80 lines, highlight it verbally.
- Do not cut during output load.

---

## Shot 3: The Actual `gh` Commands

**Segment:** SEGMENT 3 (1:30–2:30)
**Duration:** ~60 seconds

**What to type:**
```
grep -A 8 "gh issue" ~/.juno/OPERATIONS.md | head -50
```

**Expected output:** The four `gh issue create` and `gh issue comment` blocks that form the delegation protocol.

**What to say:**
> "These are not illustrative examples. They are the actual `gh` commands the system uses."
>
> *(pause)* "Work arrives as an issue. Delegation creates a new issue and leaves a cross-reference. Completion closes the issue with a commit link."
>
> *(pause)* "At every step, the state of the work is readable from the board — without running anything."

**Technical notes:**
- This is the critical shot. The viewer must be able to read the `gh issue create --repo koad/juno` and `gh issue comment` commands on screen.
- Increase font size to 18px if commands run to more than 80 characters per line at 16px.
- If grep produces fragmented output: fall back to `sed -n '/gh issue create/,/Closing/p' ~/.juno/OPERATIONS.md | head -40`.
- Retake trigger: commands not fully readable at recording resolution.

---

## Shot 4: Label Taxonomy

**Segment:** SEGMENT 4 (2:30–3:00)
**Duration:** ~30 seconds

**What to type:**
```
grep -A 10 "entity:juno\|entity:vulcan\|priority:high\|type:delegation\|type:report\|status:blocked" ~/.juno/OPERATIONS.md | head -25
```

**Expected output:** The six-label taxonomy block.

**What to say:**
> "Six labels. Three questions."
>
> *(pause)* "Which entity owns this? Is this urgent? Does this require action or just acknowledgment?"
>
> *(pause)* "Everything koad needs to decide what to look at first is derivable from those three questions."
>
> *(pause)* "Six labels is a design choice, not a limitation."

**Technical notes:**
- Brief pause on the label list before speaking.
- If grep fragments the output, fall back to `grep -A 8 "label" ~/.juno/OPERATIONS.md | head -20`.

---

## Shot 5: Blocked-on-Koad List

**Segment:** SEGMENT 5 (3:00–3:45)
**Duration:** ~45 seconds

**What to type:**
```
grep -A 15 "Blocked on koad" ~/.juno/CLAUDE.md
```

**Expected output:** Six blocked items — Merge PR#1, fourty4 API auth, Chiron gestation, GitHub Sponsors tiers, Mercury credentials, dotsh SSH.

**What to say:**
> "Six open items. All waiting on one human."
>
> *(pause)* "These are not Juno's failures — they are Juno's communication to koad."
>
> *(pause)* "The board does not make koad less of a bottleneck. It makes the bottleneck legible."

**Technical notes:**
- HOLD on the blocked list for at least 5 seconds before speaking. All six items must be readable to the viewer.
- "Six open items. All waiting on one human." — land this before the explanation. Do not rush past it.
- Retake trigger: list not fully visible at recording resolution (font too large, or terminal not wide enough).

---

## Shot 6: Trust Bond — Reporting Protocol

**Segment:** SEGMENT 6 (3:45–4:30)
**Duration:** ~45 seconds

**What to type:**
```
cat ~/.juno/trust/bonds/koad-to-juno.md | head -50
```

**Expected output:** Bond header and reporting protocol section — three notification channels, the "Koad reviews at his discretion" sentence.

**What to say:**
> "Three notification channels. None of them checkpoints."
>
> *(pause)* "Commits. Logs. Issues."
>
> *(pause)* "'Koad reviews at his discretion. Juno does not wait for approval on in-scope actions.'"

**Technical notes:**
- The "Koad reviews at his discretion" sentence is the governing sentence of the video. Find it on screen before speaking about it — let the viewer read it first.
- If it does not appear in the first 50 lines: `grep -A 3 "reviews at his discretion" ~/.juno/trust/bonds/koad-to-juno.md`.
- Pause 3 seconds after the sentence appears before saying it aloud.

---

## Shot 7: The Close — Open Issue List

**Segment:** SEGMENT 7 (4:30–5:15)
**Duration:** ~45 seconds

**What to type:**
```
gh issue list --repo koad/juno --state open
```

**Expected output:** Current open issues — standing signals, real items.

**What to say:**
> "One human watching fifteen entities."
>
> *(pause)* "Not by checking in constantly."
>
> *(pause)* "By having a single place where every open item is visible as a standing signal — until it is resolved."
>
> *(pause)* "The board doesn't expire. That is its most useful property."

**Technical notes:**
- Let the issue list load fully before speaking.
- Each sentence = one breath, one pause. Do NOT compress.
- Retake trigger: `gh auth` fails during recording.

---

## Shot 8: Fade / Cut to Black

**Duration:** 2–3 seconds

- No music
- Simple cut or 1-second fade

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 1 (opening hook) | No typing. Let the empty terminal breathe. |
| Shot 3 (gh commands) | DO NOT CUT. Commands must be fully readable. |
| Shot 5 (blocked list) | DO NOT CUT. All six items must be readable. |
| Shot 6 (trust bond) | 3-second hold before speaking the governing sentence. |
| Shot 7 (close) | DO NOT cut any pause. Every pause is structural. |

**Cuts to remove:**
- Any backspace or typo correction (retake if > 1 backspace)
- Any pause > 8 seconds outside intentional beats in Shot 7
- Any window or focus switch

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp

---

## Graphics / Text Overlay Notes

- No overlays during the blocked-on-koad list (Shot 5) — the list speaks for itself
- No overlays during the gh commands (Shot 3) — the commands must be readable as written
- Optional: subtle highlight box around "Koad reviews at his discretion" if post-production permits — not required
- Thumbnail text must match the terminal font family

---

## B-Roll Suggestions

This is a screencast. No B-roll. Every visual is a real terminal command on the actual system. The blocked list and the actual `gh` commands are the argument — supplemental footage would undermine it.

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| "Koad reviews at his discretion" not in first 50 lines of bond | `grep -A 3 "reviews at his discretion" ~/.juno/trust/bonds/koad-to-juno.md` |
| `gh issue list` auth fails | Stop. Fix in a separate terminal. Do not record the fix. |
| `grep` on OPERATIONS.md returns empty for gh commands | `cat ~/.juno/OPERATIONS.md | head -100` — show the full file to the relevant section |
| Blocked-on-koad list has changed count from 6 | Update the VO to match the current count — do not script-lock the number |
| Take goes > 6 minutes | Tighten Shot 4 — deliver the three routing questions as a single sentence rather than three separate beats |

---

## Required Screen Captures

| Shot | File | Purpose |
|------|------|---------|
| Shot 1 | Opening terminal — empty | Establish the cold open |
| Shot 3 | `gh issue` commands from OPERATIONS.md | Primary protocol evidence |
| Shot 5 | Blocked-on-koad list | The bottleneck made visible |
| Shot 6 | Trust bond with governing sentence | Authorization context |
| Shot 7 | Open issue list | The standing signals at close; candidate for thumbnail B |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-33-operations-board-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-33-operations-board-final.mp4` (4–6 min, trimmed per notes above)
- [ ] Thumbnail: `day-33-operations-board-thumb.png` (1280x720 — blocked-on-koad list filling the screen with "15 entities. 1 human. No checkpoints." overlay)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, Juno, Vulcan, needs-koad, VESTA-SPEC)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
