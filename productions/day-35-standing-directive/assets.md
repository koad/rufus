---
title: "Shot List — The Standing Directive"
video: day-35-standing-directive
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "The Standing Directive"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines

### State verification (CRITICAL: pull both entity repos immediately before recording)
- [ ] `git -C ~/.juno pull` — must be run immediately before the session, not the night before
- [ ] `git -C ~/.chiron pull` — same
- [ ] `cat ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md | head -30` — confirm architecture correction section and "keep going" quote visible
- [ ] `grep -n "Session resumed\|Standing directive\|keep going" ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md` — confirm four phase boundary markers present
- [ ] `git -C ~/.chiron log --oneline | grep -i "hook\|local\|fourty"` — confirm both `44a2dec` and `d29d8ef` present
- [ ] `git -C ~/.chiron show 44a2dec -- hooks/executed-without-arguments.sh` — confirm `ENTITY_HOST="fourty4"` and `ssh "$ENTITY_HOST"` visible in diff
- [ ] `git -C ~/.chiron show d29d8ef -- hooks/executed-without-arguments.sh` — confirm comment change and SSH removal visible
- [ ] `cat ~/.chiron/hooks/executed-without-arguments.sh` — confirm current hook shows `# runs locally on thinker`
- [ ] `gh auth status` — confirm GitHub CLI authenticated
- [ ] OBS armed at 1920x1080, 60fps, black background capture
- [ ] Mic check

### What to know before recording

**The standing directive (exact quote, from log line 18):**
> "give her all the runtime she needs — also vesta could use a lot of sessions… keep going until it's all done or blocked by me or vulcan."

**Shortened form used in post title and throughout:**
> "keep going until it's all done or blocked by me or vulcan."

**Phase boundary markers in session log:**
- Phase 1→2: "Session resumed from compressed summary. All background agents from prior session completed."
- Phase 2→3: "Session resumed from context-window summary. Standing directive remains active."
- Phase 3→4: "Standing directive remains: 'keep going until all done or blocked by me or Vulcan.'"
- Phase 4→5: "Session resumed from context-window summary. Standing directive remains active."

**Chiron hook commits:**
- `44a2dec` — April 4, 11:36 AM: "fix: replace copied Juno hook with correct fourty4 routing hook"
  - This is the version that routed to fourty4 via SSH
  - `ENTITY_HOST="fourty4"` + `ssh "$ENTITY_HOST" ...` is the evidence line
- `d29d8ef` — April 5, 1:29 AM: "hooks: run locally on thinker — drop fourty4 SSH dependency"
  - This is the fix
  - Comment changes from "headquartered at fourty4" to "runs locally on thinker"
  - SSH invocation replaced by local `cd "$ENTITY_DIR" && $CLAUDE_BIN ...`

**Memory records committed alongside hook fix:**
- `feedback_entities_are_local.md` — entities are portable, git clone them, Agent tool for invocation
- `feedback_vulcan_wonderland.md` — Vulcan exception: always via GitHub Issues
- `project_hook_architecture.md` updated — local-first pattern, fourty4 HQ removed

**Blocked issue referenced:**
- `koad/juno#44` — fourty4 API auth expired (still open at session time)

**Artifact totals from session log (for Segment 5):**
| Entity | Output | Volume |
|--------|--------|--------|
| Chiron | entity-operations, advanced-trust-bonds, daemon-operations curricula | 146+ atoms |
| Vesta | SPEC-038 through SPEC-054 | 17 specs |
| Faber | Days 10–20 posts, Days 22–33 posts and corrections | 23+ posts |
| Muse | Site and feature design briefs | 6 files |
| Livy | Reference library | 9 docs |
| Rufus | Entity intro packages, Day 31/32 video scripts | 14 items |
| Sibyl | Research briefs including ICM synthesis | 8+ files |
| Veritas | Post fact-checks and approvals | 8 reviews |
| Argus | Team health check + EOD recheck | 2 reports |
| Salus | Remediation acting on Argus findings | 3 fixes |

**Specific commit hashes from session log (for verification offer in Segment 5):**
- `015050f` — Faber, Day 33 committed
- `35249fd` — Iris correction applied to Day 33
- `d8eb1ee` — Day 32 Veritas APPROVED-WITH-NOTES
- `2cb26a4` — Chiron, CURRICULUM-ROADMAP updated
- `99638f1` — Salus/Chiron trust bond remediation

---

## Shot 1: Empty Terminal — Opening Hook

**Segment:** SEGMENT 1 (0:00–0:35)
**Duration:** ~35 seconds

**What the screen shows:**
- Terminal. Prompt only. Nothing else.

**What to type:** Nothing.

**What to say:**
> "keep going until it's all done or blocked by me or vulcan."
>
> *(pause — 2 seconds)* "That is a direct quote. Not a summary. Not a paraphrase."
>
> *(pause)* "It appears in the session log — verbatim — across four context window compressions."
>
> *(pause)* "The human set a standing directive and stepped away. The orchestrator ran the full team until the work was done or a genuine blocker surfaced."
>
> *(pause — 2 seconds)* "This is what that looks like."

**Technical notes:**
- Open cold. No commands until Shot 2.
- Deliver the quote as an unattributed opening statement — the viewer will not know its source yet. That's intentional.
- Retake trigger: any verbal stumble on the opening quote.

---

## Shot 2: Session Log Header — Architecture Correction and Parallel Deployment

**Segment:** SEGMENT 2 (0:35–1:30)
**Duration:** ~55 seconds

**What to type:**
```
cat ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md | head -30
```

**Expected output:** Session log header through the "Full team parallel deployment" section — the architecture correction, the standing directive quote, and the nine-entity deployment pattern.

**What to say:**
> "The session log opens with an architecture correction. Chiron's hook was routing invocations to fourty4 — the always-on machine. Expired API auth. We will come back to that."
>
> *(pause)* "Then the standing directive quote. Then the deployment."
>
> *(pause)* "Nine entities launched in parallel. Chiron on curriculum atoms. Vesta on specs. Faber on content posts. Muse on design briefs. Livy on reference documentation. Rufus on video production packages. Sibyl on research briefs. Veritas on post reviews. Argus on team health."
>
> *(pause)* "One message. Nine Agent tool calls. Each entity in its own directory, its own context, running in the background."
>
> *(pause)* "Salus acted reactively — not as part of the initial deployment."

**Technical notes:**
- Scroll slowly so the nine entity names are visible as you name them.
- Hold on the standing directive quote in the log before naming the entities.
- DO NOT CUT the scroll.

---

## Shot 3: Phase Boundary Grep — Four Compressions

**Segment:** SEGMENT 3 (1:30–2:45)
**Duration:** ~75 seconds

**What to type:**
```
grep -n "Session resumed\|Standing directive\|standing directive\|keep going" ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md
```

**Expected output:** Four to five matches — the phase boundary markers showing "Standing directive remains active" repeating across different line numbers.

**What to say:**
> "Context windows are finite. The Day 6 session ran long enough to compress four times."
>
> *(pause)* "Each compression is a phase boundary. The log marks them:"
>
> *(pause — let viewer read the output)*
>
> "Phase one to two: 'All background agents from prior session completed.'"
>
> *(pause)* "Phase two to three: 'Standing directive remains active.'"
>
> *(pause)* "Phase three to four: 'Standing directive remains active.'"
>
> *(pause)* "Phase four to five: 'Standing directive remains active.'"
>
> *(pause — 2 seconds)*
>
> "Four compressions. Four reconstructions. The standing directive is not lost."
>
> *(pause)* "What compression resets: the within-phase conversational context, the decisions being weighed, the background agent notification queue."
>
> *(pause)* "What compression does not touch: anything committed to disk."
>
> *(pause)* "The file system is the durable layer. Context windows are the working memory."

**Technical notes:**
- Hold the grep output for 5 seconds before speaking. Let the viewer see the repetition pattern in the line numbers.
- The contrast between "What compression resets" and "What compression does not touch" is structural — deliver each clause with a full pause between them.
- Retake trigger: grep output does not show the four markers clearly.

---

## Shot 4: Hook Commit Log — The Setup

**Segment:** SEGMENT 4 (2:45–4:30)
**Duration:** ~105 seconds — MONEY SHOT

**What to type:**
```
git -C ~/.chiron log --oneline | grep -i "hook\|local\|fourty"
```

**Expected output:** Both commits visible — `44a2dec fix: replace copied Juno hook with correct fourty4 routing hook` and `d29d8ef hooks: run locally on thinker — drop fourty4 SSH dependency`.

**What to say:**
> "The most interesting single event in the session log appears at the phase one opening."
>
> *(pause)* "Chiron's hook was routing invocations to fourty4. The hook committed April 4th set up the SSH routing pattern."
>
> *(pause)* "fourty4 had expired API auth. koad/juno issue 44."

**Technical notes:**
- Hold the commit list for 3 seconds before speaking.
- Both hashes must be readable at recording resolution.

---

## Shot 5: The fourty4 Routing Hook (44a2dec) — CRITICAL VISUAL

**Segment:** SEGMENT 4 continued (3:10–3:40)
**Duration:** ~30 seconds

**What to type (deliberately — this is the build-up):**
```
git -C ~/.chiron show 44a2dec -- hooks/executed-without-arguments.sh | head -40
```

**Expected output:** The diff showing `ENTITY_HOST="fourty4"`, `CLAUDE_BIN` pointing to the remote NVM path, and the `ssh "$ENTITY_HOST"` invocation — this is the routing-to-fourty4 evidence.

**What to say (as the diff appears):**
> "The April 4th hook. Every invocation — every Agent tool call to Chiron — was SSHing to fourty4 to run. The expired auth was the wall."
>
> *(pause)* "Under normal session flow, this might have remained implicit. Chiron attempts to run. Fails silently. Work stalls."
>
> *(pause)* "But the phase one opening requires reconstruction from compressed state. A fresh review of what is actually configured — not what was assumed."

**CRITICAL VISUAL:** `ENTITY_HOST="fourty4"` and the `ssh "$ENTITY_HOST"` line must both be readable on screen simultaneously or in immediate succession. This is the first half of the money shot.

**Technical notes:**
- DO NOT CUT. Let the diff display fully.
- If font size makes the SSH line run off-screen: reduce to 14px for Shots 5 and 6 only, then restore.
- Retake trigger: `ENTITY_HOST="fourty4"` or `ssh "$ENTITY_HOST"` not readable.

---

## Shot 6: The Local Fix Diff (d29d8ef) — CRITICAL VISUAL

**Segment:** SEGMENT 4 continued (3:40–4:20)
**Duration:** ~40 seconds

**What to type:**
```
git -C ~/.chiron show d29d8ef -- hooks/executed-without-arguments.sh
```

**Expected output:** The fix diff — comment changes from "headquartered at fourty4" to "runs locally on thinker", removal of `ENTITY_HOST`, removal of `ssh "$ENTITY_HOST"`, addition of local `cd "$ENTITY_DIR" && $CLAUDE_BIN ...`.

**What to say (as the diff appears):**
> "The fix. April 5th, 1:29 AM. The comment changes: 'headquartered at fourty4' becomes 'runs locally on thinker.' The SSH line is gone."
>
> *(pause)* "Two lines removed. Two lines added. Two new memory records committed. One hook updated."
>
> *(pause)* "The compression did not cause the error. The reconstruction that compression requires is what surfaced it."
>
> *(pause — 2 seconds)* "A phase boundary forced a fresh review of assumptions. The assumption that Chiron ran on fourty4 was wrong. It is now committed as a memory record that will survive the next compression."
>
> *(pause)* "That is the feature, not the bug, of context window limits."

**CRITICAL VISUAL:** The comment line change (`-# chiron — headquartered at fourty4.` / `+# chiron — runs locally on thinker.`) and the removal of the `ssh` invocation must both be readable. This is the second half of the money shot — the resolution.

**Technical notes:**
- DO NOT CUT. Both the removed SSH line and the added local execution line must appear on screen.
- "That is the feature, not the bug" is the thesis. Pause 2 seconds before and after.
- Retake trigger: the comment change or the SSH removal not readable. Any cut during the diff scroll.

---

## Shot 7: Session Log Tail — Artifact Record

**Segment:** SEGMENT 5 (4:30–5:30)
**Duration:** ~60 seconds

**What to type:**
```
tail -60 ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md
```

**Expected output:** The final session state section including the entity output table with volumes.

**What to say:**
> "One session. Four compression events. Five phases. Ten entities."
>
> *(pause)* "The artifact record from the session log:"
>
> *(pause — let viewer read the table)*
>
> "Chiron: 146 curriculum atoms across three curricula. Vesta: 17 specifications. Faber: 23 posts. Muse: 6 design briefs. Livy: 9 reference documents. Rufus: 14 production items. Sibyl: 8 research briefs. Veritas: 8 reviews. Argus and Salus: health check and 3 remediations."
>
> *(pause — 2 seconds)*
>
> "Specific commits from the log: `015050f` — Faber, Day 33. `d8eb1ee` — Day 32 Veritas approved. `2cb26a4` — Chiron, CURRICULUM-ROADMAP updated."
>
> *(pause)* "Any reader can run `git show 015050f` on the Faber repo and read the work."
>
> *(pause)* "The $200 Thinkpad ran this."

**Technical notes:**
- If the tail output does not contain the full entity table, adjust to `tail -80`.
- Hold on the table before reading the entity names — let the numbers be visible.
- The commit hashes are a verification offer — pause after stating each one.

---

## Shot 8: Phase Boundary Count — Fossil Record Close

**Segment:** SEGMENT 6 (5:30–6:15)
**Duration:** ~45 seconds

**What to type:**
```
grep -c "Session resumed\|Standing directive" ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md
```

**Expected output:** A count — 4 or 5 matches.

**What to say (slowest pacing in the video):**
> "The standing directive survived four compressions."
>
> *(pause)* "Not because the orchestrator remembered it."
>
> *(pause)* "Because it is committed to CLAUDE.md."
>
> *(pause — 2 seconds)*
>
> "The work survived because git log is the ground truth. The blocked list survived because it is committed. The hook failure was found because compression required reconstruction — and reconstruction reads what is actually on disk, not what was assumed."
>
> *(pause — 2 seconds)*
>
> "The orchestrator's reasoning — what to launch next, what to defer, what constitutes a genuine blocker — that did not survive compression intact."
>
> *(pause)* "The standing directive survived. The work survived. The decisions that connected them are archaeological inference, not primary source."
>
> *(pause)* "The fossil record is almost complete. Not quite."
>
> *(pause — 2 seconds)*

**Technical notes:**
- Each sentence = one breath, one pause. DO NOT compress.
- "The fossil record is almost complete. Not quite." is the close. Deliver it as two sentences, not one. Pause between them.
- Retake trigger: any verbal rush through the last three lines. Any stumble on "archaeological inference."

---

## Shot 9: Fade / Cut to Black

**Duration:** 2–3 seconds

- No music
- Simple cut or 1-second fade

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 1 (opening) | No typing. Empty terminal. Quote delivered cold. |
| Shot 3 (phase boundaries) | DO NOT CUT grep output. The repetition pattern is the visual argument. |
| Shot 5 (44a2dec diff) | DO NOT CUT. `ENTITY_HOST="fourty4"` must be readable. |
| Shot 6 (d29d8ef diff) | DO NOT CUT. Comment change and SSH removal must both appear. |
| Shot 7 (artifact table) | Hold on the table before reading names. |
| Shot 8 (fossil record) | DO NOT compress any pause. Each sentence is structural. |

**Cuts to remove:**
- Any backspace or typo correction (retake if > 1 backspace, especially on commit hashes)
- Any pause > 8 seconds outside intentional beats in Shot 8
- Any window or focus switch

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp

---

## Graphics / Text Overlay Notes

- No overlays during any diff display (Shots 5, 6) — the diff output is the argument
- Optional: subtle highlight on the `ENTITY_HOST="fourty4"` line in Shot 5 if post-production permits — not required, the `+`/`-` markers are stark enough
- Thumbnail text must match the terminal font family

---

## B-Roll Suggestions

This is a screencast. No B-roll. The session log, the diffs, and the commit record are the argument. Supplemental footage would dilute the authenticity.

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `44a2dec` not in `git -C ~/.chiron log` after pull | Run `git log --all --oneline \| grep fourty`. If on detached branch: `git checkout main && git pull`. Do not record without this diff. |
| `d29d8ef` not present | Same resolution as above. STOP if neither fix commit is findable — file an issue on koad/chiron before recording. |
| Phase boundary grep returns fewer than 4 matches | Check that you are looking at the correct file path. Confirm `~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md` exists with full content after git pull. |
| Session log tail does not show entity table | Increase to `tail -100`. If table is absent from file, note the absence on screen and read the totals from memory — but confirm totals against the session log before recording. |
| Diff not readable at recording resolution | Reduce to 14px for Shots 5 and 6 only. Both `ENTITY_HOST="fourty4"` and `# chiron — runs locally on thinker.` must be legible. |
| Take goes > 7 minutes | Tighten Segment 5 — deliver the entity totals as four lines (Chiron/Vesta, Faber/Muse, the rest combined) rather than per-entity. Do not tighten Segment 4 or Segment 6. |

---

## Required Screen Captures

| Shot | File | Purpose |
|------|------|---------|
| Shot 1 | Opening terminal — empty | Cold open; standing directive delivered cold |
| Shot 3 | Phase boundary grep output | Structural argument visual; repetition pattern |
| Shot 5 | 44a2dec diff — `ENTITY_HOST="fourty4"` | First half of money shot |
| Shot 6 | d29d8ef diff — SSH removal / local execution | Second half of money shot; thumbnail source |
| Shot 7 | Session log tail — entity artifact table | Verification offer visual |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-35-standing-directive-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-35-standing-directive-final.mp4` (5–7 min, trimmed per notes above)
- [ ] Thumbnail: `day-35-standing-directive-thumb.png` (1280x720 — grep output showing "Standing directive remains active" repeated, with "9 agents. 4 compressions. 1 instruction." overlay)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, Chiron, Veritas, Vesta, Faber, Sibyl, fourty4, thinker, CLAUDE.md, CURRICULUM-ROADMAP)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
