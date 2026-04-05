---
title: "The Spec Was Wrong on Day 2"
video-type: forensic-reconstruction
pillar: Reality
date: 2026-05-15
duration: 8–10 minutes
subject: trust bond spec divergences, field report as falsification artifact, spec-bends-to-lived-system principle, Vesta correction commits
production-owner: Rufus
status: production-ready
---

# Script: "The Spec Was Wrong on Day 2"

## Directorial Note

This is not a failure episode. It is the episode after the failure episode. Day 44 was the story of a silent routing error — a gap in the fossil record, a fix that barely shows. This episode is about a different kind of wrong: a spec that was written before the thing it described existed, then corrected the same day someone built against it.

The tone is forensic reconstruction, then satisfaction. Not triumph. Satisfaction. The loop closed in hours. The correction is in the git log. Six specific predictions were wrong. Six specific corrections were committed. That completeness — the fact that the feedback mechanism worked and the record shows it — is the thing this video is about.

The structural center of this video is the six-item list in the field report. That list is the unit test output. It names the predictions, names the failures, names the correct answers. The viewer should feel the same thing you feel when a test suite goes from red to green: not excitement, not pride, just relief that the system works the way it claims to.

Do not oversell the correction. Do not frame the six divergences as a near-miss or a near-disaster. They were normal. First-draft specs are hypotheses. Hypotheses get falsified. What matters is the mechanism: was the falsification recorded? Was the correction committed? Was the loop closed before the next session started?

In this case: yes, yes, and yes.

The money shot is the git log showing `cdd8181` (Day 2, spec written) and `11abae4` (Day 4, spec corrected, +135/-45) in the same screen. Two commits. Two days. One correction. The viewer should be able to read the commit messages and understand the entire story without narration.

---

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background (#000000), white text, fullscreen
- [ ] Font: JetBrains Mono or Fira Code, 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `git -C /home/koad/.vesta log --oneline` — verify the correction sequence is present: `cdd8181` (Day 2), `11abae4` (Day 4, 14:10), `110679f` (Day 4, 15:18), `8334549` (Day 4, 15:29)
- [ ] `git -C /home/koad/.vesta show 11abae4 --stat` — verify: 180 lines changed, 135 insertions, 45 deletions, single file `trust.md`
- [ ] Audio check: quiet room, mic gain set
- [ ] OBS: single-monitor capture, no chat overlay

---

## SEGMENT 1 — The Claim (0:00–1:00)

**No preamble. No title card. Open on blank terminal.**

**Narration:**

> "On Day 2, Vesta shipped the trust bond spec."

*(pause — 3 seconds)*

> "On Day 4, Juno implemented 11 bonds against it."

*(pause — 2 seconds)*

> "The spec was wrong in six places."

*(pause — 4 seconds of silence)*

> "Juno found all six during implementation, wrote a field report, and Vesta issued the corrections the same session."

*(pause — 3 seconds)*

> "That is the entire story. The rest of this video is the evidence."

*(pause — 4 seconds of silence)*

---

## SEGMENT 2 — The Correction Sequence (1:00–3:30) — CENTRAL TERMINAL SCENE

**Narration:**

> "The claim this operation makes about specs is exactly what you'd expect from any engineering team: write the spec first, then build against it, then fix the spec when building reveals gaps."

*(pause — 3 seconds)*

> "What this operation does differently is file the corrections the same session and commit them with explicit attribution. The spec was wrong on these specific points. The correction is this specific commit. The evidence is in the record."

*(pause — 3 seconds)*

> "Look at the record."

*(pause — 2 seconds)*

**Type slowly:**

```bash
git -C /home/koad/.vesta log --oneline
```

**[Execute. Let output render fully. Hold 8 seconds of silence. Do not narrate. Let the viewer locate the sequence.]**

**The output will show the full commit history. The relevant sequence is visible near the bottom: `cdd8181` (Day 2, spec written), then `11abae4` just above it (Day 4, the correction), then `110679f` and `8334549` above that (two more corrections, same session). Three specs corrected in one session. One git log.**

**After the hold, narration — slow, forensic:**

> "There it is."

*(pause — 4 seconds)*

> "Day 2 at the bottom: `cdd8181` — 'Draft onboarding package.' That's the trust bond spec, written March 31st before a single bond existed."

*(pause — 3 seconds)*

> "Four commits up: `11abae4` — 'Reconcile trust.md with field report: fix format, naming, add peer type, document signing UX.' That's April 2nd. That's Day 4."

*(pause — 3 seconds)*

> "Then `110679f` — 'fix: three bugs in team.md.' Then `8334549` — 'fix: commands.md.' All three corrections in the same session. All three committed before the session ended."

*(pause — 4 seconds of silence)*

> "The loop closed in hours."

*(pause — 4 seconds of silence)*

---

## SEGMENT 3 — The Six Divergences (3:30–5:45) — FIELD REPORT TERMINAL SCENE

**Narration:**

> "The mechanism that closed the loop is a field report. Not a design review. Not a retrospective written weeks later. A document committed to Juno's log directory the same day as the implementation, explicitly structured as: here is what was actually done, here is what the draft spec says, here is where they differ."

*(pause — 3 seconds)*

> "The document reads like a unit test reporting failures. That framing is not incidental. It is what the document is."

*(pause — 2 seconds)*

**Type slowly:**

```bash
git -C /home/koad/.vesta show 11abae4 --stat
```

**[Execute. Hold 6 seconds. Let the commit message and file stats render. Viewer reads: +135/-45, single file, trust.md.]**

**After the hold:**

> "One file. One hundred and thirty-five lines added. Forty-five removed."

*(pause — 3 seconds)*

> "The commit message names the corrections explicitly: fix format, fix naming, add peer type, document signing UX."

*(pause — 3 seconds)*

> "Those are four of the six divergences. Here is what each one actually was."

*(pause — 2 seconds)*

**Narration — slower. Each item is a distinct beat.**

> "First: file extension. The spec described bond files as `<grantor>-<type>.signed`. Clearsign produces `.asc`. The extension `.signed` does not exist as a GPG output format. The actual files are `<grantor>-to-<grantee>.md` and `<grantor>-to-<grantee>.md.asc`."

*(pause — 3 seconds)*

> "Second: naming convention. The spec's pattern buries the grantee. `juno-authorized-builder` tells you what Juno can grant. `juno-to-vulcan` tells you who the parties are. When you have 11 bonds and you're looking up by relationship, you need the grantee in the filename. The spec dropped it."

*(pause — 3 seconds)*

> "Third: the peer bond type. The spec defined six bond types. Of the 11 bonds signed on Day 4, eight of them required a type not in the spec. The entire depth-1 team — eight entities — is bonded as `peer`. The most common type in the system was absent."

*(pause — 4 seconds of silence)*

> "Fourth: two signing procedures, not one. Human grantors use Keybase — which pops a GUI passphrase dialog. That dialog IS the consent gesture. AI entity grantors use GPG with no passphrase. The spec described one procedure. The two procedures embody two different security models."

*(pause — 3 seconds)*

> "Five and six: status tracking and implementation notes. The spec had no mechanism for tracking whether a bond was active or revoked. And it had no section for future spec authors — no record of what the implementation actually revealed. Both added in `11abae4`."

*(pause — 4 seconds of silence)*

> "Six predictions. Six corrections. All in one commit. All in one session."

*(pause — 4 seconds of silence)*

---

## SEGMENT 4 — Why the Spec Was Wrong (5:45–7:15)

**Blank terminal. No command typed.**

**Narration — analytical. This is the theoretical payload.**

> "The spec was not wrong because Vesta made errors."

*(pause — 3 seconds)*

> "The spec was wrong because it was written before the implementation existed to falsify it. That is the normal starting condition for a first-draft spec. You write the hypothesis. Then someone builds against it. Then the building reports back."

*(pause — 4 seconds of silence)*

> "The peer bond type was missing not because Vesta overlooked it — it was missing because the team structure didn't exist yet as a concrete set of relationships to name. The gap was only visible once Juno tried to file 11 actual bonds and discovered that 8 of them required a type that hadn't been defined."

*(pause — 3 seconds)*

> "The naming convention failed not because the logic was wrong — it failed because the lookup pattern only becomes obvious once you have 11 bonds and need to find a specific one. You can't design for a use case that hasn't happened yet."

*(pause — 4 seconds of silence)*

> "The design principle that emerged from this: when spec and lived system disagree, the lived system is the source of truth."

*(pause — 3 seconds)*

> "Spec bends to lived system. Not the other way."

*(pause — 4 seconds of silence)*

> "The standard approach inverts this. Spec defines truth. Implementation deviates. Implementation gets fixed to match the spec. That approach fails here because the spec was written before any bonds existed. The implementation is the evidence about what actually works."

*(pause — 3 seconds)*

> "If Juno had conformed to the spec rather than documenting divergence, the trust bond system would have `.signed` files no GPG tool produces, a naming scheme that loses the grantee at filing time, and eight bonds with an undefined type. Correct on paper. Broken on disk."

*(pause — 4 seconds of silence)*

---

## SEGMENT 5 — The Loop Requirement (7:15–8:30)

**Blank terminal. Narration — slower. This is the honest accounting.**

> "The loop worked in this case because Juno and Vesta were actively collaborating in real time."

*(pause — 3 seconds)*

> "The mechanism was informal: a committed log file and direct conversation, same session. No ticket system. No async review cycle. Juno discovered the divergences, wrote the field report, Vesta received it and issued the corrections before the session ended."

*(pause — 4 seconds of silence)*

> "That informality is a constraint worth naming."

*(pause — 2 seconds)*

> "The loop worked because both entities treated it as a priority. It would not survive a less active implementation phase."

*(pause — 3 seconds)*

> "The still-open question: what does the spec-to-implementation feedback loop look like when implementer and spec author are operating asynchronously? Vulcan builds. Vesta maintains specs. Two entities with no shared session, coordinating through GitHub Issues and committed artifacts. The field report convention exists. The commit-and-cite protocol exists. The bounded-timeframe guarantee does not."

*(pause — 4 seconds of silence)*

> "The six divergences in the trust bond spec are not proof that the spec-writing process is broken."

*(pause — 2 seconds)*

> "They are proof that a first-draft spec is a hypothesis and that hypotheses require operational evidence to correct."

*(pause — 3 seconds)*

> "The evidence mechanism that worked on Day 4 was informal. The correction was immediate."

*(pause — 4 seconds of silence)*

> "Making that pattern reliable at scale — across entities that don't share sessions, on specs that cover systems not yet built — is the design problem that Day 4 raised."

*(pause — 3 seconds)*

> "And did not fully solve."

*(pause — 4 seconds of silence)*

---

## SEGMENT 6 — The Record (8:30–9:30) — CLOSING

**Narration — very slow. Each line stands alone.**

> "The trust bond spec was wrong from Day 2 until Day 4."

*(pause — 3 seconds)*

> "Written on a Tuesday. Corrected the following Thursday."

*(pause — 2 seconds)*

> "Within the same session as the implementation that revealed the errors."

*(pause — 4 seconds of silence)*

> "The git log is the audit trail."

*(pause — 2 seconds)*

> "`cdd8181` — spec written, Day 2. Field report filed. `11abae4` — spec corrected, Day 4. Time elapsed: two days, one session."

*(pause — 4 seconds of silence)*

> "The correction is committed. The trust bonds are canonical. The spec that Vesta maintains now reflects what the implementation actually does, because the implementation ran and reported back."

*(pause — 3 seconds)*

> "The loop is the mechanism."

*(pause — 2 seconds)*

> "The mechanism is the infrastructure."

*(pause — 4 seconds of silence)*

> "That is what `11abae4` is."

**[6 seconds of silence. Cut to black.]**

---

## Timing Map

| Segment | Clock | Content |
|---------|-------|---------|
| 1 | 0:00–1:00 | The claim — Day 2 spec, Day 4 implementation, six divergences, same-session correction |
| 2 | 1:00–3:30 | Correction sequence — vesta git log, cdd8181 → 11abae4 visible, three corrections in one session |
| 3 | 3:30–5:45 | The six divergences — git show 11abae4 --stat, field report framing, each item named |
| 4 | 5:45–7:15 | Why the spec was wrong — spec as hypothesis, spec bends to lived system, correct-on-paper vs broken-on-disk |
| 5 | 7:15–8:30 | The loop requirement — informal mechanism, two-day timeline, async gap still open |
| 6 | 8:30–9:30 | The record — cdd8181 to 11abae4, the loop is the mechanism, the mechanism is the infrastructure |

---

## Delivery Notes

- **Tone:** Forensic reconstruction, then satisfaction. Not triumph. Not apology. The satisfaction is the same feeling you get when a test suite turns green: relief that the system works.
- **Segment 2 (git log):** The 8-second hold is not optional. The correction sequence must be visible on screen while the viewer reads. Do not point to the commits. Do not narrate over them. The viewer finds the sequence.
- **"There it is." (Segment 2):** Flat. Not triumphant. Observation only. 4 seconds after.
- **Six divergences (Segment 3):** Each item is a distinct beat. Do not run them together. The list is the unit test output — present it like a test reporter: concise, attributed, factual.
- **"Spec bends to lived system." (Segment 4):** This is the pivot line. Slow. Flat. Let it stand alone.
- **"Correct on paper. Broken on disk." (Segment 4):** These are paired. Pause between them. Each gets its own beat.
- **"And did not fully solve." (Segment 5):** Do not soften this. The loop works informally. That is accurate. That is the honest state.
- **Closing segment (6):** Each clause on its own line in delivery. "`cdd8181`... `11abae4`..." — read the hashes as dates in the record, not as technical minutiae.
- **"The loop is the mechanism. The mechanism is the infrastructure." (Segment 6):** Paired. Do not rush. This is the theoretical claim that closes the argument.
- **"That is what `11abae4` is." — final line:** No inflection. Statement. Then silence. Then black.
- **No backspace corrections on camera.** Retake immediately if a typo occurs on a path or command.
- **No live entity invocations.** Two terminal commands only: `git log --oneline`, `git show 11abae4 --stat`. Everything else is narration over blank terminal.

---

## Accuracy Notes

- `cdd8181` — authored by Vesta, 2026-03-31 21:19:37 -0400, "Draft onboarding package for koad/vesta#1" (this is the commit that included the original trust.md)
- `11abae4` — authored by Vesta, 2026-04-02 14:10:14 -0400, "Reconcile trust.md with field report: fix format, naming, add peer type, document signing UX"
  - File: `projects/onboarding/docs/trust.md`, 180 lines total, +135/-45
  - The commit message body names all corrections explicitly
- `110679f` — 2026-04-02 15:18:19, "fix: three bugs in team.md — Juno feedback"
- `8334549` — 2026-04-02 15:29:55, "fix: commands.md — reconcile two-rule discovery, document both subcommand patterns"
- All three corrections in the same session (14:10, 15:18, 15:29)
- The field report: `/home/koad/.juno/LOGS/2026-04-02-trust-bond-field-report.md` — filed same session as the implementation
- The six divergences (from the field report and Faber post): file extension (.signed → .md + .md.asc), naming convention (grantor-type → grantor-to-grantee), missing peer bond type, two signing procedures (Keybase for humans, GPG for AI), missing status tracking, missing implementation notes section
- "Spec bends to lived system" — this exact phrase is the operational principle that emerged from the Day 4 session; use it verbatim
