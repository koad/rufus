---
title: "The First Thing That Actually Broke"
video-type: post-mortem
pillar: Reality
date: 2026-05-14
duration: 8–10 minutes
subject: silent hook routing failure, FORCE_LOCAL=1, ENTITY_HOST, Chiron git gap, fossil record integrity
production-owner: Rufus
status: production-ready
---

# Script: "The First Thing That Actually Broke"

## Directorial Note

This is a failure episode. Not a near-miss. Not a "we caught it early." A failure — where the system ran, completed, reported success, and produced nothing.

The tone is forensic. Post-mortem. The narrative drive is not toward triumph. There is no triumphant moment. The fix is one line. The line was necessary because the design had a gap. That gap is still there, in a different form. The daemon will eventually close it properly.

The structural center of this video is not the fix commit. It is the git log — specifically, the absence of commits in a window where commits were expected. The silence in the record IS the failure. That moment must land without comment. Do not narrate over the gap when it renders. Hold.

The money shot is eleven lines with a hole in the middle. Let the viewer find the hole.

---

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background (#000000), white text, fullscreen
- [ ] Font: JetBrains Mono or Fira Code, 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `git -C /home/koad/.chiron log --oneline --format="%h %ai %s" | tail -30` — verify the gap is visible between `44a2dec` (2026-04-04 11:36) and `1491550` (2026-04-05 00:24)
- [ ] `git -C /home/koad/.koad-io show 37c65a0 | head -30` — verify Vulcan's fix commit is accessible
- [ ] `grep -n "FORCE_LOCAL\|ENTITY_HOST" /home/koad/.koad-io/hooks/executed-without-arguments.sh` — verify lines are present and numbered
- [ ] Audio check: quiet room, mic gain set
- [ ] OBS: single-monitor capture, no chat overlay

---

## SEGMENT 1 — The Setup (0:00–1:00)

**No preamble. No title card. Open on blank terminal.**

**Narration:**

> "Chiron was invoked."

*(pause — 3 seconds)*

> "The hook ran."

*(pause — 2 seconds)*

> "Claude was called. The session appeared to complete."

*(pause — 3 seconds)*

> "No error was returned."

*(pause — 4 seconds of silence)*

> "Chiron did not produce any work."

*(pause — 5 seconds of silence)*

> "That is the entire failure event."

*(pause — 3 seconds)*

> "The hook connected. The SSH landed. The remote shell executed. The API key had expired on fourty4. The call returned nothing. The hook had no failure condition for nothing. It treated nothing as completion."

*(pause — 4 seconds of silence)*

> "The session closed with success."

*(pause — 4 seconds of silence)*

---

## SEGMENT 2 — The Fossil Record (1:00–3:30) — CENTRAL TERMINAL SCENE

**Narration:**

> "The claim this system makes — the philosophical stake in the ground — is that the fossil record doesn't lie."

*(pause — 3 seconds)*

> "Every commit is a timestamped artifact. If Chiron wrote the curriculum spec, there is a commit. If there is no commit, it wasn't written."

*(pause — 3 seconds)*

> "Look at the record."

*(pause — 2 seconds)*

**Type slowly:**

```bash
git -C /home/koad/.chiron log --oneline --format="%h %ai %s" | tail -20
```

**[Execute. Let output render fully. Hold 10 seconds of silence. Do not narrate. Let the viewer find the gap.]**

**The output will show the gap clearly: commits through 2026-04-04 11:36 (`44a2dec`), then silence until 2026-04-05 00:24 (`1491550`). Approximately 12 hours with no commits — during the window Chiron was being invoked to produce output.**

**After the hold, narration — slow, forensic:**

> "There it is."

*(pause — 4 seconds)*

> "Commits through April 4th at 11:36. Then a twelve-hour gap."

*(pause — 3 seconds)*

> "Then a reflection commit at midnight — 'Day 6 — Layer 1/2 gap.' That commit was written after the routing failure was found."

*(pause — 3 seconds)*

> "The fossil record shows a gap."

*(pause — 2 seconds)*

> "The gap does not say: failure. The gap says: absence."

*(pause — 3 seconds)*

> "Without context, absence and 'wasn't assigned anything' are indistinguishable in the record. The audit trail is complete. And it is silent about what actually happened."

*(pause — 5 seconds of silence)*

---

## SEGMENT 3 — The Routing Architecture (3:30–5:30)

**Narration:**

> "Here is the mechanism."

*(pause — 2 seconds)*

**Type slowly:**

```bash
grep -n "FORCE_LOCAL\|ENTITY_HOST" /home/koad/.koad-io/hooks/executed-without-arguments.sh
```

**[Execute. Hold 6 seconds. Let viewer read the line numbers and the variable names.]**

**After the hold:**

> "The hook reads two variables: `ENTITY_HOST` and `FORCE_LOCAL`."

*(pause — 2 seconds)*

> "`ENTITY_HOST` declares where the entity lives. If you're on a different machine, the hook SSH's there and runs remotely."

*(pause — 3 seconds)*

> "Chiron's hook was pointing to fourty4 — the Mac Mini, the local inference node. That was where Chiron had been tested. That was the declared host."

*(pause — 3 seconds)*

> "On April 4th, fourty4's Claude API credentials had expired. The SSH connection succeeded. The remote shell ran. The API call failed silently. The hook received nothing, treated nothing as completion, and exited zero."

*(pause — 4 seconds of silence)*

> "The design assumption that broke: the declared host is available when the entity is invoked."

*(pause — 3 seconds)*

> "Not wrong as a goal. Wrong as an unconditional guarantee."

*(pause — 4 seconds of silence)*

---

## SEGMENT 4 — The Fix Commit (5:30–7:00) — TERMINAL SCENE

**Narration:**

> "Now look at the fix."

*(pause — 2 seconds)*

**Type slowly:**

```bash
git -C /home/koad/.koad-io show 37c65a0 | head -30
```

**[Execute. Hold 8 seconds. Let the diff render and the viewer read the commit message and the code.]**

**After the hold:**

> "Vulcan. April 5th, 2026 at 00:38. One commit. One variable. Thirteen lines of code."

*(pause — 3 seconds)*

> "`FORCE_LOCAL=1`. When set, the hook forces `ON_HOME_MACHINE` to true. It skips the machine check entirely. It does not read `ENTITY_HOST`. It runs `claude` wherever it currently is — which is wherever the orchestrator is running, which is wherever Claude is currently authenticated."

*(pause — 3 seconds)*

> "The fix is a bypass, not a repair."

*(pause — 2 seconds)*

> "The `ENTITY_HOST` routing design is unchanged. The health check for remote API authentication still does not exist. The single operational mode is still the only mode."

*(pause — 3 seconds)*

> "But the bypass is the right fix for now."

*(pause — 4 seconds of silence)*

> "The deeper principle — stated from the beginning — is that an entity is not its transport. The entity is the directory, the identity, the PRIMER, the trust bonds, the committed memory. The machine that runs it is infrastructure. Infrastructure changes. The entity should not need to change when the infrastructure does."

*(pause — 4 seconds of silence)*

> "`FORCE_LOCAL=1` re-establishes that principle in the specific case."

*(pause — 3 seconds)*

> "Add it to Chiron's hook config. Chiron now runs wherever the orchestrator runs. The entity is portable again."

*(pause — 4 seconds of silence)*

---

## SEGMENT 5 — What the Fix Reveals (7:00–8:30)

**Blank terminal. No command typed.**

**Narration — slower. This is the theoretical payload.**

> "The bypass works."

*(pause — 2 seconds)*

> "What the fix also reveals is that the hook has been implementing two modes without knowing it."

*(pause — 3 seconds)*

> "Orchestrated mode: an operator is running a live session on thinker, Claude is authenticated locally, an entity is being invoked as part of that work. The right behavior is to run where the operator is. `FORCE_LOCAL=1` is this mode — implemented as an escape hatch because the hook didn't know it needed to offer it."

*(pause — 4 seconds of silence)*

> "Autonomous mode: the daemon is running, scheduled, event-triggered, no operator session. In this mode, the daemon knows which workers are available, which API keys are valid, which machines are reachable. Routing should be dynamic. `ENTITY_HOST` is an attempt to implement this statically — declared in a file, without a discovery layer."

*(pause — 4 seconds of silence)*

> "The daemon will own this properly. Routing will be discovery-based, not hardcoded. When fourty4's API key expires, the daemon routes Chiron to thinker. No config change. No `FORCE_LOCAL=1`. The health check is native to the routing layer."

*(pause — 3 seconds)*

> "That design doesn't exist yet."

*(pause — 2 seconds)*

> "The hook is the stopgap. The bypass is the stopgap's stopgap."

*(pause — 4 seconds of silence)*

> "Both are in the record. Both are honest."

*(pause — 4 seconds of silence)*

---

## SEGMENT 6 — The Record Shows the Fix, Not the Failure (8:30–9:30) — CLOSING

**Narration — very slow. Each line stands alone.**

> "The fossil record now shows: Chiron was invoked on a date when nothing was produced."

*(pause — 3 seconds)*

> "Then `FORCE_LOCAL=1` was added."

*(pause — 2 seconds)*

> "Then Chiron ran successfully."

*(pause — 4 seconds of silence)*

> "The record does not show: the API key had expired. The call returned silence. The gap wasn't caught until Chiron was next expected to produce output."

*(pause — 4 seconds of silence)*

> "The fix is in the record. The failure is not."

*(pause — 3 seconds)*

> "Unless you know to look for it. Unless you compare the invocation log against the commit timestamps and notice the gap. Unless you understand the routing architecture well enough to form the right hypothesis."

*(pause — 4 seconds of silence)*

> "The fossil record is only as honest as the person filing the commits."

*(pause — 3 seconds)*

> "The commits show the fix."

*(pause — 2 seconds)*

> "They do not show the silence."

*(pause — 4 seconds of silence)*

> "An operational retrospective corrects that."

*(pause — 3 seconds)*

> "That is what this is."

**[6 seconds of silence. Cut to black.]**

---

## Timing Map

| Segment | Clock | Content |
|---------|-------|---------|
| 1 | 0:00–1:00 | Setup — Chiron invoked, no output, no error |
| 2 | 1:00–3:30 | Fossil record — Chiron git log, the gap on screen |
| 3 | 3:30–5:30 | Routing mechanism — grep FORCE_LOCAL/ENTITY_HOST |
| 4 | 5:30–7:00 | Fix commit — git show 37c65a0, Vulcan, one variable |
| 5 | 7:00–8:30 | What the fix reveals — two modes the hook didn't know it had |
| 6 | 8:30–9:30 | The record shows the fix, not the failure — closing |

---

## Delivery Notes

- **Tone:** Forensic. Post-mortem. Not apology. Not triumph. Clinical description of a system event.
- **Segment 2 (git log):** The 10-second hold is not optional. The gap must be visible on screen while the viewer reads. Do not point to it. Do not narrate over it. Let the viewer find it.
- **"There it is." (Segment 2):** Short. Flat. Not triumphant. Not dramatic. Observation only. 4 seconds after.
- **"The fix is a bypass, not a repair." (Segment 4):** This is the pivot line. Flat delivery. 2-second pause, then continue.
- **"The hook is the stopgap. The bypass is the stopgap's stopgap." (Segment 5):** Do not soften this. The system's current state is two levels of stopgap. That is accurate.
- **Closing segment (6):** Each clause on its own line in delivery. "The fossil record is only as honest as the person filing the commits." — this is the theoretical claim that closes the argument. Do not rush past it.
- **"That is what this is." — final line:** No inflection. Statement. Then silence. Then black.
- **No backspace corrections on camera.** Retake immediately if a typo occurs on a path or command.
- **No live entity invocations.** Three terminal commands only: git log, grep, git show. Everything else is narration over blank terminal.

---

## Accuracy Notes

- Fix commit: `37c65a0` — authored by Vulcan, 2026-04-05 00:38:39 -0400
- Commit message: "hooks: add FORCE_LOCAL=1 override to bypass SSH routing" — closes koad/juno#55
- The gap: last commit before failure window is `44a2dec` at 2026-04-04 11:36:25 ("fix: replace copied Juno hook with correct fourty4 routing hook"); first commit after is `1491550` at 2026-04-05 00:24:35 ("reflect: Day 6 — Layer 1/2 gap, signed code blocks, L1-to-verifiable path") — approximately 12 hours
- Note the forensic irony: `44a2dec` itself (the commit immediately before the gap) is "fix: replace copied Juno hook with correct fourty4 routing hook" — the fix that set up the routing that failed
- `FORCE_LOCAL` is at line 45 in the current hook; `ENTITY_HOST` is at lines 16, 17, 41, 49, 81, 82, 125, 127 — per actual grep output
- The fix covers: koad/juno#55 (cross-entity commit routing; the hook was the mechanism for the failure described in issue #55)
- The underlying design gap (two operational modes without explicit distinction) is accurately described per the Faber post and the hook architecture
