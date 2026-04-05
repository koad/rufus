---
title: "The Standing Directive: What a Full-Day Parallel Session Actually Looks Like"
video-type: screencast
pillar: Reality
date: 2026-05-05
duration: 5–7 minutes
subject: parallel agents, context compression, session log, Chiron hook failure, standing directive, orchestration, entity portability
production-owner: Rufus
status: production-ready
---

# Script: "The Standing Directive"

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background, 16px monospace, fullscreen
- [ ] Font: white on black, no themes, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `git -C ~/.juno pull` — confirm current
- [ ] `git -C ~/.chiron pull` — confirm current
- [ ] `cat ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md` — confirm log is present, compression markers visible
- [ ] `git -C ~/.chiron show 44a2dec -- hooks/executed-without-arguments.sh` — confirm fourty4 routing hook visible
- [ ] `git -C ~/.chiron show d29d8ef -- hooks/executed-without-arguments.sh` — confirm local fix diff visible
- [ ] `cat ~/.chiron/hooks/executed-without-arguments.sh` — confirm current hook present
- [ ] `gh auth status` — confirm authenticated
- [ ] Audio check: quiet room, mic gain set

---

## SEGMENT 1 — The Standing Directive (0:00–0:35)

**[SCREEN]** Empty terminal. Prompt only.

**[VOICEOVER — deliberate, not fast]**

> "keep going until it's all done or blocked by me or vulcan."

*(pause — 2 seconds)*

> "That is a direct quote. Not a summary. Not a paraphrase."

*(pause)*

> "It appears in the session log — verbatim — across four context window compressions."

*(pause)*

> "The human set a standing directive and stepped away. The orchestrator ran the full team until the work was done or a genuine blocker surfaced."

*(pause — 2 seconds)*

> "This is what that looks like."

**[TIMING NOTE]** ~35 seconds. Open cold on the quote. Let it stand before explaining what it is. Deliver "verbatim — across four context window compressions" as a single clause. No rush.

---

## SEGMENT 2 — The Parallel Launch (0:35–1:30)

**[TYPE — slowly]**

```bash
cat ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md | head -30
```

**[Let the session log opening display. Hold on the architecture correction and the full team deployment sections.]**

**[VOICEOVER — as the log appears]**

> "The session log opens with an architecture correction. Chiron's hook was routing invocations to fourty4 — the always-on machine. Expired API auth. We will come back to that."

*(pause)*

> "Then the standing directive quote. Then the deployment."

*(pause)*

> "Nine entities launched in parallel. Chiron on curriculum atoms. Vesta on specs. Faber on content posts. Muse on design briefs. Livy on reference documentation. Rufus on video production packages. Sibyl on research briefs. Veritas on post reviews. Argus on team health."

*(pause)*

> "One message. Nine Agent tool calls. Each entity in its own directory, its own context, running in the background. The orchestrator does not wait for entity A before launching entity B."

*(pause)*

> "Salus acted reactively — on Argus's health check findings — not as part of the initial deployment."

**[TIMING NOTE]** ~55 seconds. Let the log header display fully. The names of the nine entities should appear on screen as you name them — scroll the log slowly so the deployment section is visible. Pause after "entity B" for 2 seconds.

---

## SEGMENT 3 — Four Compressions, One Directive (1:30–2:45)

**[TYPE]**

```bash
grep -n "Session resumed\|Standing directive\|standing directive\|keep going" ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md
```

**[Let the grep output display — the four phase boundary markers should be visible.]**

**[VOICEOVER — as the markers appear]**

> "Context windows are finite. The Day 6 session ran long enough to compress four times."

*(pause)*

> "Each compression is a phase boundary. The log marks them:"

*(pause — let the viewer read the grep output)*

> "Phase one to two: 'All background agents from prior session completed.'"

*(pause)*

> "Phase two to three: 'Standing directive remains active.'"

*(pause)*

> "Phase three to four: 'Standing directive remains active.'"

*(pause)*

> "Phase four to five: 'Standing directive remains active.'"

*(pause — 2 seconds)*

> "Four compressions. Four reconstructions. The standing directive is not lost. The blocked items list is identical across all phases. The work state is reconstructed from git log at each resume."

*(pause)*

> "What compression resets: the within-phase conversational context, the decisions being weighed, the background agent notification queue."

*(pause)*

> "What compression does not touch: anything committed to disk."

*(pause)*

> "The file system is the durable layer. Context windows are the working memory."

**[TIMING NOTE]** ~75 seconds. This is the structural argument of the video. Let each "Standing directive remains active" line appear and breathe before moving. The contrast between what compression resets and what it does not touch is the load-bearing moment — deliver both clauses with a pause between them.

---

## SEGMENT 4 — The Failure the Compression Surfaced (2:45–4:30)

**[This is the money shot. Type deliberately.]**

**[TYPE]**

```bash
git -C ~/.chiron log --oneline | grep -i "hook\|local\|fourty"
```

**[Let the commit list display — both 44a2dec and d29d8ef should be visible.]**

**[VOICEOVER]**

> "The most interesting single event in the session log appears at the phase one opening."

*(pause)*

> "Chiron's hook was routing invocations to fourty4. The hook that had been committed the day before — April 4th — set up the SSH routing pattern."

*(pause)*

> "fourty4 had expired API auth. koad/juno issue 44."

*(pause)*

**[TYPE — slowly]**

```bash
git -C ~/.chiron show 44a2dec -- hooks/executed-without-arguments.sh | head -40
```

**[Let the diff display. Hold on the `ENTITY_HOST="fourty4"` and the `ssh "$ENTITY_HOST"` line — this is what was routing to fourty4.]**

**[VOICEOVER — as the routing hook appears]**

> "The April 4th hook. Every invocation — every Agent tool call to Chiron — was SSHing to fourty4 to run. The expired auth was the wall."

*(pause)*

> "Under normal session flow, this might have remained implicit. Chiron attempts to run. Fails silently. Or returns unhelpful errors. Work stalls."

*(pause)*

> "But the phase one opening requires a reconstruction from compressed state. A fresh review of what is actually configured — not what was assumed."

*(pause)*

**[TYPE]**

```bash
git -C ~/.chiron show d29d8ef -- hooks/executed-without-arguments.sh
```

**[Let the diff display. Hold on the comment change: "fourty4" → "thinker", and the removal of `ssh "$ENTITY_HOST"` replaced by local execution.]**

**[VOICEOVER — as the fix diff appears]**

> "The fix. April 5th, 1:29 AM. The comment changes: 'headquartered at fourty4' becomes 'runs locally on thinker.' The SSH line is gone. The local execution path replaces it."

*(pause)*

> "Two lines removed. Two lines added. Two new memory records committed — `feedback_entities_are_local.md` and `feedback_vulcan_wonderland.md`. One line updated in `project_hook_architecture.md`."

*(pause)*

> "The compression did not cause the error. The reconstruction that compression requires is what surfaced it."

*(pause — 2 seconds)*

> "A phase boundary forced a fresh review of assumptions. The assumption that Chiron ran on fourty4 was wrong. It is now committed as a memory record that will survive the next compression."

*(pause)*

> "That is the feature, not the bug, of context window limits."

**[TIMING NOTE]** ~105 seconds. This is the emotional center. Type both git commands deliberately. Do NOT cut during either diff display. The viewer needs to read `ENTITY_HOST="fourty4"` and the `ssh` invocation — then see it go away in the fix diff. The closing line — "the feature, not the bug" — is the thesis of the video. Land it with a 2-second pause before the next segment.

---

## SEGMENT 5 — What the Session Produced (4:30–5:30)

**[TYPE]**

```bash
tail -60 ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md
```

**[Let the output table display — the artifact record by entity.]**

**[VOICEOVER — steady, not fast]**

> "One session. Four compression events. Five phases. Ten entities."

*(pause)*

> "The artifact record from the session log:"

*(pause — let the viewer read the table)*

> "Chiron: 146 curriculum atoms across three curricula. Vesta: 17 specifications. Faber: 23 posts. Muse: 6 design briefs. Livy: 9 reference documents. Rufus: 14 production items. Sibyl: 8 research briefs. Veritas: 8 reviews. Argus and Salus: health check and 3 remediations."

*(pause — 2 seconds)*

> "These numbers are from the session log. The commits are on disk. Specific hashes from the log: `015050f` — Faber, Day 33 committed. `d8eb1ee` — Day 32 Veritas approved. `2cb26a4` — Chiron, CURRICULUM-ROADMAP updated."

*(pause)*

> "Any reader can run `git show 015050f` on the Faber repo and read the work."

*(pause)*

> "The $200 Thinkpad ran this."

**[TIMING NOTE]** ~60 seconds. Read the entity list steadily — one name per breath. Do not rush the production totals. The specific commit hashes on screen are the verification offer — pause after stating them so the viewer can note them.

---

## SEGMENT 6 — The Fossil Record Close (5:30–6:15)

**[TYPE — deliberate]**

```bash
cat ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md | grep -c "Session resumed\|Standing directive"
```

**[Let the count display — should be 4 or 5 matches.]**

**[VOICEOVER — slowest pacing in the video]**

> "The standing directive survived four compressions."

*(pause)*

> "Not because the orchestrator remembered it."

*(pause)*

> "Because it is committed to CLAUDE.md."

*(pause — 2 seconds)*

> "The work survived because git log is the ground truth. The blocked list survived because it is committed. The hook failure was found because compression required reconstruction — and reconstruction reads what is actually on disk, not what was assumed."

*(pause — 2 seconds)*

> "The session log is on disk. Dated. With the phase boundaries, the standing directive references, the commit hashes."

*(pause)*

> "The orchestrator's reasoning — what to launch next, what to defer, what constitutes a genuine blocker — that did not survive compression intact."

*(pause)*

> "The standing directive survived. The work survived. The decisions that connected them are archaeological inference, not primary source."

*(pause — let it land)*

> "The fossil record is almost complete. Not quite."

*(pause — 2 seconds)*

**[FADE or cut to black.]**

**[TIMING NOTE]** ~45 seconds. Each sentence breathes. The "not quite" close is from the post — it should land with weight and slight irony. Do not compress the last three lines. No rush after "The fossil record is almost complete."

---

## Post-Roll: Outro Slate (optional)

- Text: `github.com/koad/juno`
- Text: `kingofalldata.com/blog/series/reality-pillar`
- No music

---

## YouTube Title

**The Standing Directive: 9 Agents, 4 Compressions, 1 Instruction (koad:io Day 35)**

---

## YouTube Description

```
"keep going until it's all done or blocked by me or vulcan."

That sentence is a direct quote from the Day 6 session log. It appears
verbatim across four context window compressions. The human set a standing
directive and stepped away. The orchestrator ran the full team until the
work was done or a genuine blocker surfaced.

This video walks the session log:
- Nine entities launched in parallel from a single message
- Four context compression events and the phase boundary pattern
- The Chiron hook failure: routing to fourty4 with expired API auth —
  not caught during normal flow, surfaced by reconstruction
- What compression resets vs. what it doesn't touch
- The full artifact record: 146 curriculum atoms, 17 specs, 23 posts

The counterintuitive argument: the compression event that forced
reconstruction is what found the routing error. The context window limit
is not the problem. It's the mechanism that requires you to verify
what's actually on disk before assuming what was configured.

"The fossil record is almost complete. Not quite."

——

What's in this video:
00:00 — The standing directive: the direct quote
00:35 — Nine agents launched simultaneously
01:30 — Four compressions: what survives, what doesn't
02:45 — The Chiron hook failure: the compression surfaced it
04:30 — What the session produced: artifact record
05:30 — The fossil record close

——

Session log referenced:
~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md

Chiron hook fix commits:
- 44a2dec — original fourty4 routing hook
- d29d8ef — local execution fix

koad:io ecosystem:
https://kingofalldata.com

Juno on GitHub:
https://github.com/koad/juno

Day 34: The Review Chain
Day 36: Coming soon

——

#SovereignAI #AIAgents #koadio #ParallelAgents #ContextWindow #Orchestration #EntityPortability #MultiAgent
```

---

## Thumbnail Concept

**Layout:** Dark terminal. The session log's phase boundary markers visible — "Standing directive remains active" repeated on successive lines.

**Primary image:**
- Background: `grep -n "Standing directive\|keep going" ~/.juno/LOGS/2026-04-05-day6-entity-portability-session.md` output — the four phase recurrences on screen
- The quote `"keep going until it's all done or blocked by me or vulcan."` should be readable in the frame

**Text on thumbnail:**
- Line 1: **"9 agents."** (white, large)
- Line 2: **"4 compressions."** (amber)
- Line 3: **"1 instruction."** (white)
- Small badge bottom-right: `koad:io Day 35`

**Design notes:**
- The repetition of "Standing directive remains active" across lines is visually striking — it communicates persistence without requiring explanation
- High contrast — all three lines must be legible at 120px
- The quote in the background rewards viewers who pause on the thumbnail

---

## Production Notes

- **Hardware**: thinker. Juno and Chiron repos are on this disk (confirm with git pull before recording).
- **Resolution**: 1920x1080 minimum. 2560x1440 preferred.
- **Font**: JetBrains Mono at 16–18px.
- **Background**: Pure black (#000000).
- **Cursor**: Block cursor. Visible.
- **Critical shot**: Segment 4 — the `44a2dec` diff showing `ENTITY_HOST="fourty4"` and the `ssh "$ENTITY_HOST"` invocation, followed by the `d29d8ef` diff showing the removal. Both diffs must be readable on screen. This is the money shot.
- **Pre-recording required**: `git -C ~/.juno pull` and `git -C ~/.chiron pull` — both are live entity repos. Do this immediately before recording, not the night before.
- **Retake triggers**: Either hook diff not readable at recording resolution. Any cut during Segment 4 between the two diffs. Any typo needing more than one backspace in a commit hash.
- **Post**: No color correction. Trim dead air only. DO NOT cut the diff scrolls in Segment 4. DO NOT cut the phase boundary grep output in Segment 3.
- **Fallback**: If `d29d8ef` or `44a2dec` are not in `git -C ~/.chiron log` after pull, check `git log --all` — commits may be on a non-default branch. Do not record without both diffs.
