---
title: "Shot List — What I Would Change: 30 Days Building a Sovereign AI Operation"
video: day-30-what-i-would-change
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "What I Would Change"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines (git log may be long — ensure nothing scrolls off)

### State verification
- [ ] `cd ~/.juno && git pull` — confirm current, note commit count
- [ ] `git log --oneline --since="2026-03-30"` — count commits, verify arc is visible
- [ ] `gh auth status` — confirm GitHub CLI authenticated
- [ ] `gh issue view 52 --repo koad/juno` — dry run, confirm issue loads with the Janus escalation body
- [ ] `cat ~/.juno/trust/bonds/koad-to-juno.md` — confirm readable
- [ ] `cat ~/.koad-io/hooks/executed-without-arguments.sh | head -50` — confirm PRIMER injection lines visible
- [ ] OBS armed at 1920x1080, 60fps, black background capture
- [ ] Mic check

### What to know before recording
Know these facts before the take — you will say them without reading:
- Date of Juno's gestation: 2026-03-30
- Number of trust bond divergences in the field report: 6
- Vulcan's FORCE_LOCAL commit hash: 37c65a0 (you do not need to recite this — just be aware of it)
- The three "what I would build differently" items: PRIMER in gestation template, designed dual memory, first-class portability modes

---

## Shot 1: Empty Terminal

**Segment:** SEGMENT 1 (0:00–0:10)
**Duration:** ~10 seconds

**What the screen shows:**
- Terminal. Prompt only.

**What to say:**
> "Juno was gestated on March 30th. That was 30 days ago. This is not a
> launch post — it was never a launch. Built in public, one committed file
> at a time, with the failures in the record alongside everything else."

**Technical notes:**
- Pause 2–3 seconds after opening before speaking.
- Deliver these lines before touching the keyboard.

---

## Shot 2: The Full Git Log — The Arc

**Segment:** SEGMENT 1 (0:10–0:45)
**Duration:** ~35 seconds (includes scroll time)

**What to type:**
```
cd ~/.juno && git log --oneline --since="2026-03-30"
```

**Expected output:** Full commit log from gestation to present — 30+ commits, ordered newest first. Let it scroll. The visual density is the argument.

**What to say while log scrolls:**
> "The git log is public. Everything named in this video is in that record.
> 30 days of commits. You don't have to take my word for any of it."

**Technical notes:**
- DO NOT cut the scroll. DO NOT speed-ramp. The density of commits is the emotional core.
- If the log is long (50+ commits), let it scroll fully — do not interrupt.
- This is the equivalent of the git log shot in the $200 Laptop video. Same discipline applies: full scroll, no cuts.
- Thumbnail frame candidate: moment when log fills the screen.

---

## Shot 3: PRIMER Injection in the Framework Hook

**Segment:** SEGMENT 2 (0:45–1:30)
**Duration:** ~45 seconds

**What to type:**
```
cat ~/.koad-io/hooks/executed-without-arguments.sh | head -50
```

**Expected output:** The framework hook file. PRIMER injection block (lines ~34–38) should be visible — the section that assembles entity identity, operational state, team structure, active priorities before the model starts.

**What to say:**
> "Three things changed what this operation can do. First: PRIMER injection.
> Five lines of bash in the framework hook — these lines here — that assemble
> entity identity, operational state, team structure, and active priorities
> before the model generates its first token."

*(pause)*

> "That was not in the original gestation template. It got there because
> early sessions produced output that required cleanup."

**Technical notes:**
- Identify the PRIMER lines on-screen verbally ("these lines here") as they appear.
- If PRIMER injection is deeper than `head -50`, adjust to `head -60` or `sed -n '30,45p'` to show the relevant block.

---

## Shot 4: Failure One — FORCE_LOCAL Commit Evidence

**Segment:** SEGMENT 3 (1:30–2:15)
**Duration:** ~45 seconds

**What to type:**
```
git -C ~/.juno log --oneline --all | grep -i "force_local\|hook"
```

**Expected output:** Commits referencing the hook routing fix — Vulcan's FORCE_LOCAL=1 commit (37c65a0) or related entries.

**What to say:**
> "First failure. Hook routing sent entities to expired API authentication.
> When Chiron's ENTITY_HOST pointed to fourty4 and fourty4's auth had expired,
> Chiron was unreachable — not with an error. Silently. Nothing came back."

*(pause)*

> "The fix is a commit: FORCE_LOCAL=1. Orchestrators override host routing
> without removing ENTITY_HOST from the entity's config. The entity still
> knows where it lives. The orchestrator overrides when it needs portability."

*(pause)*

> "What this revealed: the original hook design assumed one operational mode.
> Real operation is at least two. FORCE_LOCAL is the patch. The right design
> makes the modes first-class."

**Technical notes:**
- If grep returns no results: try `git -C ~/.juno log --oneline --all | head -30` to confirm commits are present, then search manually. The FORCE_LOCAL fix may live in koad/vulcan rather than koad/juno — adjust accordingly.
- Fallback: `git -C ~/.koad-io log --oneline | head -20` and name the relevant commit.

---

## Shot 5: Failure Two — Trust Bond Directory (Actual Format)

**Segment:** SEGMENT 4 (2:15–2:45)
**Duration:** ~30 seconds

**What to type:**
```
ls ~/.juno/trust/bonds/
```

**Expected output:** The `.md` and `.md.asc` pairs — the actual filing format (not `.signed`, not `<grantor>-<type>`).

**What to say:**
> "Second failure. The trust bond spec diverged from implementation on Day 2.
> File format wrong. Naming convention wrong. Signing tool not distinguished.
> Consent UX not documented. One bond type missing. Revocation format
> undefined. Six divergences."

*(pause)*

> "The field report named all six. Vesta updated the spec. What failed was
> not that the spec was wrong — that was expected. What failed was that the
> correction loop had no name yet. Two days instead of two hours."

**Technical notes:**
- The visual evidence is the actual format on screen — `.md` and `.md.asc` pairs.
- Pause on the listing for 2–3 seconds before speaking. Let the viewer see the format.

---

## Shot 6: Failure Three — Janus Escalation Issue 52

**Segment:** SEGMENT 5 (2:45–3:15)
**Duration:** ~30 seconds

**What to type:**
```
gh issue view 52 --repo koad/juno
```

**Expected output:** The Janus escalation issue — body text describing the cross-entity commit authorization question, resolution that commits were authorized, policy outcome.

**What to say:**
> "Third failure. Cross-entity commit authorization had no written policy
> until Janus forced one. The commits were correct. The authorization chain
> existed. What did not exist was a rule."

*(pause)*

> "Issue 52. The ruling: commits authorized, gap real, policy now exists.
> Every cross-entity commit must reference a directing issue."

*(pause)*

> "The escalation was the governance layer functioning as designed — on a
> design that was incomplete."

**Technical notes:**
- Let the issue text load fully before speaking.
- If the issue body is long, let it scroll — do not cut.
- Retake trigger: wrong issue loads, or `gh auth` fails during recording.

---

## Shot 7: The Commit Count Punctuation Beat

**Segment:** SEGMENT 6 (3:15–3:20)
**Duration:** ~5 seconds

**What to type:**
```
git -C ~/.juno log --oneline --since="2026-03-30" | wc -l
```

**Expected output:** A number. That number is the count of commits in 30 days.

**What to say:** Nothing. Let the number land. Then begin the "three things I would build differently" VO.

**Technical notes:**
- This is a punctuation beat — brief visual, no VO on top of it.
- 2–3 seconds of silence after the number appears before speaking.

---

## Shot 8: The Three Corrections (No Typing — VO Only)

**Segment:** SEGMENT 6 (3:20–4:00)
**Duration:** ~40 seconds

**What the screen shows:** Commit count output from Shot 7 (hold the frame — no new commands).

**What to say:**
> "Three things I would build differently."

*(pause)*

> "PRIMER.md in the gestation template from Day 0. The cold-start problem is
> prior to everything. The entity's first commit should include its populated
> PRIMER.md."

*(pause)*

> "The dual-memory architecture designed, not discovered. The boundary between
> committed memory and session memory should be a design decision made before
> the first session."

*(pause)*

> "Portability mode as a first-class hook concept, not an environment variable
> patch. The design would not require the override because the design would
> name the modes."

**Technical notes:**
- No typing in this segment. VO over the static commit count frame.
- Each correction is one or two sentences. One breath per sentence.

---

## Shot 9: The First Commit — Arc Closure

**Segment:** SEGMENT 7 (4:00–4:10)
**Duration:** ~10 seconds

**What to type:**
```
git -C ~/.juno log --oneline --since="2026-03-30" | tail -1
```

**Expected output:** The first commit in the arc — gestation commit from 2026-03-30.

**What to say:** Nothing yet. Let the first commit appear. One beat of silence. Then begin the close.

**Technical notes:**
- This is a visual callback to Shot 2 (the full arc). Now we see the start point.
- 2–3 seconds of silence after the line appears.

---

## Shot 10: The Close — VO Over First Commit

**Segment:** SEGMENT 7 (4:10–4:45)
**Duration:** ~35 seconds

**What the screen shows:** The first commit from Shot 9 (hold the frame).

**What to say — slowest pacing in the video:**

> "The system is more legible at Day 30 than at Day 0."

*(pause — 2 seconds)*

> "Not because it was designed to be."

*(pause)*

> "Because the failures forced articulation."

*(pause)*

> "This is what the fossil record is for. Not to show that the system worked
> as designed. To show that it generated legible failures, that the failures
> produced corrections, and that the corrections are committed."

*(pause — 2 seconds)*

> "The operation is 30 days old. The git log is public."

*(pause — 2 seconds)*

> "That is the whole argument."

*(pause — let it land.)*

**Technical notes:**
- Slowest pacing in the video.
- Each sentence = one breath. Pauses are structural — not dead air.
- Editor: do NOT cut any of these pauses.
- Fade or cut to black immediately after the last sentence.

---

## Shot 11: Fade / Cut to Black

**Duration:** 2–3 seconds

- No music
- Simple cut or 1-second fade
- Do not hold on any additional text or annotation

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 2 (git log scroll) | DO NOT CUT. DO NOT speed-ramp. The scroll is the argument. |
| Shot 6 (gh issue view) | Let issue body load. Do not cut while loading. |
| Shot 8 (corrections VO) | No typing — static frame. VO only. |
| Shot 9 (first commit) | 2–3 seconds silence before VO begins. |
| Shot 10 (close) | DO NOT cut any pauses. Every pause is structural. |

**Cuts to remove:**
- Any backspace or typo correction (retake if > 1 backspace)
- Any pause > 8 seconds outside of intentional beats in Shot 10
- Any window or focus switch

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp (especially not on the git log in Shot 2)

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `git log` returns empty or wrong date range | Stop. Check `~/.juno` is on the correct repo and is current. |
| `gh issue view 52` fails or loads wrong issue | Stop. Check `gh auth status`. Retry. |
| `gh auth` not working | Stop. Fix auth in a separate terminal. Do not record the fix on-camera. |
| git log scroll is too fast to read | Increase terminal scrollback buffer. Do not retake for this — scroll speed is fine. |
| Take goes > 5 minutes | Tighten Shot 8 — cut one of the three corrections to its shortest form. |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-30-what-i-would-change-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-30-what-i-would-change-final.mp4` (4–5 min, trimmed per notes above)
- [ ] Thumbnail: `day-30-what-i-would-change-thumb.png` (1280x720 — git log fills the screen, Shot 2)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, Janus, PRIMER, FORCE_LOCAL, fourty4)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
