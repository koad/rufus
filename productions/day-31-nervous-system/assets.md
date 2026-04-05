---
title: "Shot List — The Nervous System Problem"
video: day-31-nervous-system
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "The Nervous System Problem"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines

### State verification
- [ ] `cd ~/.juno && git pull` — confirm current
- [ ] `ls ~/.juno/LOGS/` — confirm 2026-04-02-first-parallel-session.md exists
- [ ] `cat ~/.juno/LOGS/2026-04-02-first-parallel-session.md | head -10` — dry run, confirm readable
- [ ] `cat ~/.juno/OPERATIONS.md | head -60` — confirm orchestration section is present
- [ ] `ls ~/.juno/trust/bonds/` — confirm bond files present
- [ ] `cat ~/.juno/trust/bonds/juno-to-vulcan.md | head -30` — confirm readable
- [ ] `gh auth status` — confirm GitHub CLI authenticated
- [ ] `gh issue list --repo koad/juno --state all --limit 10` — dry run, confirm loads
- [ ] OBS armed at 1920x1080, 60fps, black background capture
- [ ] Mic check

### What to know before recording
- Date of first parallel session: 2026-04-02
- Entities in that session: Argus, Janus, Aegis
- Duration to all three returning results: four minutes
- Argus finding: 7 of 11 entities missing `read: allow` in opencode config
- Policy name in OPERATIONS.md: "launch, observe, decide"
- VESTA spec for pre-scripted chain prohibition: VESTA-SPEC-054 §4.4

---

## Shot 1: Empty Terminal — Opening Hook

**Segment:** SEGMENT 1 (0:00–0:30)
**Duration:** ~30 seconds

**What the screen shows:**
- Terminal. Prompt only. Nothing else.

**What to type:** Nothing.

**What to say:**
> "Most multi-agent systems break the same way."
>
> *(pause)* "Agent A calls B. B calls C. C hands off to D. You test each handoff
> — it works. Then B hits a blocker. Not an error. A real result that changes
> what the next step should be."
>
> *(pause)* "The pipeline doesn't know. It passes the output to C anyway. C
> proceeds on bad assumptions. D produces confident garbage."
>
> *(pause)* "The chain executed. The chain was wrong."
>
> *(pause)* "The problem isn't the agents."

**Technical notes:**
- Pause 2–3 seconds after opening terminal before speaking.
- This is the most important segment. Deliver it without rushing.
- No keyboard input until this segment is complete.
- Retake trigger: any verbal stumble in the first four sentences.

---

## Shot 2: OPERATIONS.md — Orchestration Section

**Segment:** SEGMENT 2 (0:30–1:15)
**Duration:** ~45 seconds

**What to type:**
```
cat ~/.juno/OPERATIONS.md | head -60
```

**Expected output:** OPERATIONS.md header and orchestration section, including "launch, observe, decide" language or equivalent.

**What to say:**
> "In the common pattern: LangChain pre-declares a directed graph. AutoGen
> routes messages through a defined topology. CrewAI sequences task handoffs.
> The graph is the product."

*(pause)*

> "koad:io names its pattern: launch, observe, decide. The next step is always
> a decision — never a preordained edge."

**Technical notes:**
- Pause on the output for 2–3 seconds before speaking.
- If the "launch, observe, decide" language is not in the first 60 lines, adjust to `grep -n "launch\|observe\|decide" ~/.juno/OPERATIONS.md | head -10`.

---

## Shot 3: Grep — Policy Language

**Segment:** SEGMENT 2 (1:15–1:45)
**Duration:** ~30 seconds

**What to type:**
```
grep -n "launch.*observe\|observe.*decide\|judgment" ~/.juno/OPERATIONS.md | head -20
```

**Expected output:** Lines referencing the orchestration pattern or judgment loop.

**What to say:**
> "Three things can happen after any agent returns. The agent surfaces a
> blocker that changes what the next step should be. The agent produces a
> result that makes one of the downstream steps unnecessary. The agent fails,
> requiring human judgment before proceeding."

*(pause)*

> "In a pre-scripted chain, none of these outcomes route correctly."

**Technical notes:**
- If grep returns empty: substitute `grep -n "pre-scripted\|chain\|policy" ~/.juno/OPERATIONS.md | head -10`.
- The visual confirmation of the grep result is enough — VO carries the argument.

---

## Shot 4: Trust Bond Directory

**Segment:** SEGMENT 3 (1:45–2:15)
**Duration:** ~30 seconds

**What to type:**
```
ls ~/.juno/trust/bonds/
```

**Expected output:** Bond files — `.md` and `.md.asc` pairs.

**What to say:**
> "There is a second reason direct wiring breaks here. Sovereignty."

*(pause)*

> "Each entity has its own git history, its own GPG keys, its own Linux user
> account. Every action must be cryptographically traceable to the entity
> that took it."

*(pause)*

> "If Juno calls Vulcan's API directly, no trust bond covers that call. The
> authorization chain dissolves."

**Technical notes:**
- Pause on the directory listing for 2–3 seconds before speaking.
- The listing is visual confirmation that bonds are real, committed artifacts.

---

## Shot 5: Juno-to-Vulcan Bond

**Segment:** SEGMENT 3 (2:15–2:45)
**Duration:** ~30 seconds

**What to type:**
```
cat ~/.juno/trust/bonds/juno-to-vulcan.md | head -30
```

**Expected output:** Bond header, scope, authorized actions, NOT AUTHORIZED items.

**What to say:**
> "If Vulcan's output is consumed programmatically without a commit, there is
> no ground truth for what Vulcan produced. The file on disk is the record.
> The commit is the attestation. Remove the commit step and you've removed
> the evidence."

*(pause)*

> "An API call has no issue reference. An API response has no commit. The
> attribution chain that makes governance functional cannot be maintained in a
> directly wired system."

**Technical notes:**
- Let the bond header display for 3 seconds before speaking.
- The NOT AUTHORIZED section is particularly useful visual evidence if it appears in the first 30 lines — identify it verbally.

---

## Shot 6: First Parallel Session Log

**Segment:** SEGMENT 4 (2:45–3:20)
**Duration:** ~35 seconds

**What to type:**
```
cat ~/.juno/LOGS/2026-04-02-first-parallel-session.md | head -60
```

**Expected output:** Session log from April 2 — entity names, findings, verdicts.

**What to say:**
> "April 2nd, 2026. Three entities ran simultaneously for the first time:
> Argus, Janus, and Aegis. Not because a pipeline triggered them. Because
> three independent tasks surfaced — all overdue, all non-overlapping."

*(pause)*

> "Four minutes later, all three returned results. Argus found real gaps:
> seven of eleven entities were missing read permissions in their opencode
> config. Janus declared the team clean. Aegis issued a DRIFTING verdict."

**Technical notes:**
- DO NOT cut the scroll. Let the log display fully.
- The log is primary evidence — it is the "showing, not telling" moment.
- If the log file does not exist: STOP. Check `ls ~/.juno/LOGS/`. Use `git -C ~/.juno log --oneline --since="2026-04-02" --until="2026-04-03"` as fallback evidence. Note the substitution in the recording.

---

## Shot 7: Repair Loop — Git Evidence

**Segment:** SEGMENT 4 (3:20–3:45)
**Duration:** ~25 seconds

**What to type:**
```
git -C ~/.juno log --oneline | grep -i "argus\|salus\|parallel" | head -10
```

**Expected output:** Commits referencing the repair loop or entities involved.

**What to say:**
> "The Argus findings triggered a repair loop. Juno read the output, determined
> it warranted a Salus remediation pass, invoked Salus. Salus applied the fixes."

*(pause)*

> "No pipeline orchestrated this. Juno observed the output and made the next
> decision."

*(pause)*

> "The primary verification mechanism is the git log. Agent output is
> conversational — it does not necessarily reflect the committed result.
> The commits are ground truth."

**Technical notes:**
- If grep returns empty: substitute `git -C ~/.juno log --oneline --since="2026-04-02" --until="2026-04-03"` to show the day's commits.
- The git evidence confirms the work happened — not just that it was discussed.

---

## Shot 8: GitHub Issue List

**Segment:** SEGMENT 5 (3:45–4:15)
**Duration:** ~30 seconds

**What to type:**
```
gh issue list --repo koad/juno --state all --limit 10
```

**Expected output:** Open and closed issues — visible evidence of cross-session coordination.

**What to say:**
> "The Agent tool and GitHub Issues are not competing approaches. They operate
> at different scopes."

*(pause)*

> "The Agent tool handles session-scoped work. GitHub Issues handle work that
> spans sessions — involves Vulcan, requires a shared reference point for
> blocked human actions, needs to remain visible on the operations board."

*(pause)*

> "Issues are persistent, timestamped, attributed to authenticated identities,
> and publicly auditable. When work requires a human decision, the issue is
> the artifact that surfaces the need."

**Technical notes:**
- Let the issue list load fully before speaking.
- The list itself is evidence — real issue numbers, real titles, real attribution.
- Retake trigger: `gh auth` fails during recording.

---

## Shot 9: The Close — Recent Commits

**Segment:** SEGMENT 6 (4:15–4:30)
**Duration:** ~15 seconds

**What to type:**
```
git -C ~/.juno log --oneline | head -5
```

**Expected output:** Five recent commits. Let them establish the ongoing record.

**What to say:** Nothing on this shot. Let the commits display for 3 seconds, then begin the close VO.

**Technical notes:**
- This is a visual beat — recent work, ongoing record.
- 3 seconds of silence before VO begins.

---

## Shot 10: Close VO — Over Commit Log

**Segment:** SEGMENT 6 (4:30–5:15)
**Duration:** ~45 seconds

**What the screen shows:** Commit log from Shot 9 (hold the frame).

**What to say — slowest pacing in the video:**

> "Days 22 through 30 described individual entities."

*(pause)*

> "Days 31 onward describe how the team works."

*(pause)*

> "The April 2nd session is the right anchor. Not because it was impressive."

*(pause)*

> "Because it was unremarkable in the right way."

*(pause — 2 seconds)*

> "Three agents. Four minutes. Real findings. One self-initiated repair loop.
> All of it traceable."

*(pause)*

> "No pre-declared graph. No pipeline."

*(pause)*

> "A series of decisions."

*(pause — let it land.)*

**Technical notes:**
- Slowest pacing in the video.
- Each sentence = one breath, one pause.
- Editor: DO NOT cut these pauses. They are structural.

---

## Shot 11: Fade / Cut to Black

**Duration:** 2–3 seconds

- No music
- Simple cut or 1-second fade

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 1 (opening hook) | No typing. Let the empty terminal breathe during VO. |
| Shot 6 (session log) | DO NOT CUT scroll. The full log display is load-bearing. |
| Shot 7 (git evidence) | Brief pause before VO — let results appear. |
| Shot 9 (recent commits) | 3 seconds silence before VO begins. |
| Shot 10 (close) | DO NOT cut any pause. Every pause is structural. |

**Cuts to remove:**
- Any backspace or typo correction (retake if > 1 backspace)
- Any pause > 8 seconds outside intentional beats in Shot 10
- Any window or focus switch

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp

---

## Graphics / Text Overlay Notes

- No overlays during the session log scroll (Shot 6) — let the raw output speak
- Optional: subtle highlight box around "3 agents / 4 minutes / DRIFTING" in the session log if post-production permits — not required
- Thumbnail text ("3 agents. 4 minutes. No pipeline.") should match the terminal font family

---

## B-Roll Suggestions

This is a screencast. No B-roll. Every visual is a real terminal command on the actual system. The authenticity is the argument — supplemental footage would dilute it.

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `~/.juno/LOGS/2026-04-02-first-parallel-session.md` does not exist | Substitute: `git -C ~/.juno log --oneline --since="2026-04-02" --until="2026-04-03"`. Note the substitution aloud. |
| `gh issue list` auth fails | Stop. Fix in a separate terminal. Do not record the fix. |
| `grep` on OPERATIONS.md returns empty | Adjust search terms: `grep -n "chain\|pipeline\|policy" ~/.juno/OPERATIONS.md` |
| Take goes > 6 minutes | Tighten Shot 3 — deliver the three failure-mode items as a single list rather than three separate sentences. |

---

## Required Screen Captures

| Shot | File | Purpose |
|------|------|---------|
| Shot 1 | Opening terminal — empty | Establish the cold open |
| Shot 6 | `cat` of first parallel session log | Primary evidence of the pattern |
| Shot 7 | Git log showing repair commits | Confirmation: work happened, it's in the record |
| Shot 10 | Close VO frame | Candidate for thumbnail B (commits + silence) |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-31-nervous-system-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-31-nervous-system-final.mp4` (4–6 min, trimmed per notes above)
- [ ] Thumbnail: `day-31-nervous-system-thumb.png` (1280x720 — session log filling the screen with "3 agents. 4 minutes. No pipeline." overlay)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, Argus, Janus, Aegis, DRIFTING, VESTA-SPEC)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
