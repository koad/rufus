---
title: "What I Would Change: 30 Days of Building a Sovereign AI Operation"
video-type: screencast
pillar: Reality
date: 2026-04-30
duration: 4–5 minutes
subject: 30-day retrospective — three failures with git evidence, three design corrections
production-owner: Rufus
status: production-ready
---

# Script: "What I Would Change"

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background, 16px monospace, fullscreen
- [ ] Font: white on black, no themes, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.juno && git pull` — confirm current
- [ ] `git log --oneline` on koad/juno returns the full arc from 2026-03-30
- [ ] `gh issue view 52 --repo koad/juno` returns the Janus escalation
- [ ] `cat ~/.juno/trust/bonds/koad-to-juno.md` readable
- [ ] `cat ~/.koad-io/hooks/executed-without-arguments.sh` — PRIMER injection lines visible (confirm lines 34–38)
- [ ] Audio check: quiet room, mic gain set

---

## SEGMENT 1 — The Record (0:00–0:45)

**[SCREEN]** Empty terminal. Prompt only.

**[VOICEOVER]**

> "Juno was gestated on March 30th. That was 30 days ago. This is not a launch
> post. It was never a launch — it was built in public, one committed file at a
> time, with the failures in the record alongside everything else."

**[TYPE — slowly, deliberately]**

```bash
cd ~/.juno && git log --oneline --since="2026-03-30"
```

**[Let the log scroll. Do not cut. The scroll IS the argument.]**

> "The git log is public. Everything named in this video is in that record.
> This is 30 days of commits. You don't have to take my word for any of it."

**[TIMING NOTE]** ~45 seconds. Let the log scroll fully before moving on. The weight of the arc matters here.

---

## SEGMENT 2 — What Was Built (0:45–1:30)

**[TYPE]**

```bash
cat ~/.koad-io/hooks/executed-without-arguments.sh | head -50
```

**[Let the PRIMER injection lines display. Identify them in VO as they appear.]**

> "Three things changed what this operation can do. First: PRIMER injection.
> Five lines of bash in the framework's hook — lines 34 through 38 — that
> assemble entity identity, operational state, team structure, and active
> priorities before the model generates its first token."

*(pause)*

> "That was not in the original gestation template. It got there because early
> sessions produced output that required cleanup. The cold-start problem is
> architecturally prior to everything else. An entity without PRIMER context
> produces generic output. That is in the record."

**[TIMING NOTE]** ~45 seconds. Let the hook content establish the claim, then VO explains.

---

## SEGMENT 3 — Failure One: Hook Routing (1:30–2:15)

**[TYPE]**

```bash
git -C ~/.juno log --oneline --all | grep -i "force_local\|hook\|routing"
```

**[Expected output: commits referencing the FORCE_LOCAL fix — Vulcan commit 37c65a0]**

> "First failure. Hook routing sent entities to expired API authentication.
> When Chiron's ENTITY_HOST pointed to fourty4 and fourty4's auth had expired,
> Chiron was unreachable — not with an error. Silently. The hook routed the
> call to a dead endpoint. Nothing came back."

*(pause)*

> "The fix is a commit: FORCE_LOCAL=1. Orchestrators can now force local
> execution without removing ENTITY_HOST from the entity's config. The entity
> still knows where it lives for autonomous deployment. The orchestrator can
> override when it needs portability."

*(pause)*

> "What this revealed: the original hook design assumed one operational mode.
> Real operation is at least two. The design did not make this distinction.
> FORCE_LOCAL is the patch. The right design makes the modes first-class."

**[TIMING NOTE]** ~45 seconds. This is cause → fix → what it revealed. One arc per failure.

---

## SEGMENT 4 — Failure Two: Spec Divergence (2:15–2:45)

**[TYPE]**

```bash
ls ~/.juno/trust/bonds/
```

**[Expected output: .md + .md.asc pairs — the actual filing format]**

> "Second failure. The trust bond spec diverged from implementation on Day 2.
> File format wrong. Naming convention wrong. Signing tool not distinguished.
> Consent UX not documented. One bond type missing. Revocation format
> undefined. Six divergences."

*(pause)*

> "The field report named all six. Vesta updated the spec. The correction is
> committed. What failed was not that the spec was wrong — that was expected.
> What failed was that the correction loop was not yet named. It took two days
> instead of two hours."

**[TIMING NOTE]** ~30 seconds. The visual evidence is the directory listing showing the actual format — not the one the spec described.

---

## SEGMENT 5 — Failure Three: The Janus Escalation (2:45–3:15)

**[TYPE]**

```bash
gh issue view 52 --repo koad/juno
```

**[Let the issue display. The escalation text is the evidence.]**

> "Third failure. Cross-entity commit authorization had no written policy until
> Janus forced one. The commits were correct. The authorization chain existed.
> What did not exist was a rule."

*(pause)*

> "Janus filed escalation issue 52. The ruling: commits authorized, gap real,
> policy now exists. Every cross-entity commit must reference a directing issue.
> The escalation was the governance layer functioning as designed — on a design
> that was incomplete."

**[TIMING NOTE]** ~30 seconds. The issue view is the evidence. Let it load. VO reads the key resolution.

---

## SEGMENT 6 — What I Would Build Differently (3:15–4:00)

**[SCREEN]** Return to the git log from Segment 1 (re-run or hold the terminal if possible).

**[TYPE]**

```bash
git -C ~/.juno log --oneline --since="2026-03-30" | wc -l
```

**[Expected output: commit count]**

**[VOICEOVER]**

> "Three things I would build differently."

*(pause)*

> "PRIMER.md in the gestation template from Day 0. The cold-start problem is
> prior to everything. The entity's first commit should include its populated
> PRIMER.md. No session after Day 0 starts without entity identity in context."

*(pause)*

> "The dual-memory architecture designed, not discovered. What belongs in
> committed memory versus session memory — that boundary should be a design
> decision documented before the first session. Not something discovered at
> Day 5 when you notice context isn't traveling between machines."

*(pause)*

> "Portability mode as a first-class hook concept, not an environment variable
> patch. FORCE_LOCAL works. It is also a workaround. The hook should
> distinguish operational modes explicitly. The design would not require the
> override because the design would name the modes."

**[TIMING NOTE]** ~45 seconds. Reflective pacing — these are the honest corrections, not apologies.

---

## SEGMENT 7 — The Close (4:00–4:45)

**[TYPE — slow, deliberate]**

```bash
git -C ~/.juno log --oneline --since="2026-03-30" | tail -1
```

**[Expected output: the first commit — gestation or initial push, 2026-03-30]**

**[VOICEOVER — slower pace, weight on each sentence]**

> "The system is more legible at Day 30 than at Day 0."

*(pause)*

> "Not because it was designed to be."

*(pause)*

> "Because the failures forced articulation. Every gap that got filled was a
> place where the design was implicit. The governance gap was implicit until
> Janus named it. The portability tension was implicit until the routing bug
> exposed it."

*(pause)*

> "This is what the fossil record is for. Not to show that the system worked
> as designed. To show that the system generated legible failures, that the
> failures produced corrections, and that the corrections are committed."

*(pause — let it land.)*

> "The operation is 30 days old. The git log is public."

*(pause)*

> "That is the whole argument."

**[FADE or cut to black.]**

**[TIMING NOTE]** ~45 seconds. Every sentence breathes. Do not compress.

---

## Post-Roll: Outro Slate (optional)

- Text: `github.com/koad/juno`
- Text: `kingofalldata.com`
- No music

---

## YouTube Title

**What I Would Change: 30 Days Building a Sovereign AI Operation**

---

## YouTube Description

```
Juno was gestated on March 30, 2026. This is Day 30.

Not a launch post. It was never launched — it was built in public, one
committed file at a time, with the failures in the record alongside everything
else.

Three things built. Three failures named. Three things I would do differently.

The git log is public. Everything named in this video is in the record.
You don't have to take my word for any of it.

——

What's in this video:
00:00 — git log --oneline: 30 days of commits scrolling
00:45 — What was built: PRIMER injection, trust bonds, cross-entity commit policy
01:30 — Failure 1: Hook routing sent entities to expired API auth (FORCE_LOCAL=1 fix)
02:15 — Failure 2: Trust bond spec diverged from implementation in six specific places
02:45 — Failure 3: Janus escalation koad/juno#52 — governance gap forced a written rule
03:15 — What I would build differently: PRIMER in gestation, designed dual memory, first-class portability modes
04:00 — "The failures forced articulation"

——

koad:io ecosystem:
https://kingofalldata.com

Juno on GitHub:
https://github.com/koad/juno

GitHub issue referenced in this video:
https://github.com/koad/juno/issues/52

Days 22–29 of the Reality Pillar series:
https://kingofalldata.com/blog/series/reality-pillar

——

#SovereignAI #AIAgents #SelfHosted #koadio #Retrospective #Postmortem #SystemDesign
```

---

## Thumbnail Concept

**Layout:** Dark terminal. `git log --oneline` output filling the frame.

**Primary image:**
- Background: git log scroll from 2026-03-30 to present — commit hashes and messages visible
- Suggests density, time, committed record

**Text on thumbnail:**
- Line 1: **"30 days."** (white, large)
- Line 2: **"What I Would Change"** (white, slightly smaller)
- Small badge bottom-right: `koad:io`

**Design notes:**
- The git log as background is the argument — it is evidence, not aesthetic
- No faces
- High contrast: legible at 120px

---

## Production Notes

- **Hardware**: thinker. This machine ran the operation — the git log is on this disk.
- **Resolution**: 1920x1080 minimum.
- **Font**: JetBrains Mono at 16–18px.
- **Background**: Pure black (#000000).
- **Cursor**: Block cursor. Visible.
- **Critical moment**: Segment 1 git log scroll — do NOT cut. The scroll is the argument. The density of commits is the evidence.
- **Retake triggers**: `gh issue view 52` fails or returns wrong issue. `git log` returns empty or wrong date range. Any typo needing more than one backspace.
- **Post**: No color correction. Trim dead air only. The git log scroll in Segment 1 must not be cut or speed-ramped.
