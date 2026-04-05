---
title: "43 Days, 4 Designs, 1 Principle — Assets"
day: 48
date: 2026-05-18
production-owner: Rufus
status: production-ready
---

# Assets: Day 48 — "43 Days, 4 Designs, 1 Principle"

## Terminal Commands (in order of appearance)

### Segment 1 — The Fossil Record (Opening)

```bash
git -C /home/koad/.juno log --oneline --since=2026-03-30 --until=2026-04-06
```

**Purpose:** The opening visual argument. The full commit density of the first six operating days. The viewer should register: this is not a milestone list. This is the full record of a design being tested, breaking, and correcting.
**Hold:** 15 seconds of silence after the output settles. Do not narrate during the hold. Let the density land before the first word.
**Output requirement:** Roughly 80–100 lines. The exact count varies with current repo state; the density is the argument, not the specific number. Verify before recording.

---

### Segment 2 — Four Failures (Commit Evidence)

```bash
git -C /home/koad/.juno log --oneline --since=2026-03-30 --until=2026-04-06 | grep -E "FORCE_LOCAL|force_local|governance|routing|portable|2c5ff65"
```

**Purpose:** Surface the correction commits from the failure cluster. Not the failures themselves — the commits that followed them. What shows on screen: the places in the log where assumptions became visible and were corrected. The viewer sees the correction commits before hearing the failure descriptions.
**Hold:** 6 seconds. Let the filtered lines render. No narration during the hold.
**Note:** The exact grep pattern may need adjustment based on current log state. The goal is to surface a small cluster of commits that are visibly corrections — governance documents, routing fixes, portability formalizations. Verify the pattern returns meaningful output before recording.

---

### Segment 3 — The Design Arc (Four Commits, in order)

**Design 1 — Initial commit:**
```bash
git -C /home/koad/.juno log --oneline 6ea6978 -1
```
**Hold:** 6 seconds. Renders: "Initial commit: Juno entity gestated"

---

**Design 2 — Hooks override (first correction to the hook layer):**
```bash
git -C /home/koad/.juno log --oneline 290f521 -1
```
**Hold:** 5 seconds. Renders: "Add hooks override — juno loads claude instead of opencode"

---

**Design 2 — PRIMER injection (session bridge formalized):**
```bash
git -C /home/koad/.juno log --oneline 54073c1 -1
```
**Hold:** 6 seconds. Renders: "hooks: inject $CWD/PRIMER.md into prompt when present"

---

**Design 3 — Governance correction (corrections cluster representative):**
```bash
git -C /home/koad/.juno log --oneline 2c5ff65 -1
```
**Hold:** 6 seconds. Renders: "governance: document bond dual-filing protocol — Janus process flag 2026-04-05"

---

**Design 4 — Daemon architecture:**
```bash
git -C /home/koad/.juno log --oneline ccbffad -1
```
**Hold:** 8 seconds. Renders: "memories: document daemon architecture (005)". This is the longest hold of the design arc because Design 4 requires the most reorientation — it is not a running system, it is a committed plan.

---

**Note on the five-commit arc sequence:** `290f521` and `54073c1` together constitute Design 2's emergence. Show both, in order, with narration bridging them. The viewer should see the two-step progression: first the hook was corrected (load claude, not opencode), then the session bridge was added (PRIMER injection). Design 2 is not one commit; it is the architecture that crystallized across several. The two shown here are the inflection points.

---

### Segment 5 — The Fossil Record Is Honest

```bash
git -C /home/koad/.juno log --oneline --since=2026-03-30 --until=2026-04-06 | wc -l
```

**Purpose:** The commit count as a single number. Not explained before it renders. The viewer sees the number and the question of what it means arrives before narration answers it.
**Hold:** 8 seconds. No narration while the number sits on screen.

---

### Segment 7 — The Principle (Closing Terminal Scene)

```bash
echo "If it is not committed, it is not real."
```

**Purpose:** The principle appearing in the terminal. This is not decoration — it is the act of committing made visual. Every other commit in the arc followed this pattern: a decision was made, and then it was recorded. The echo command demonstrates the recording act in its simplest form.
**Hold:** 10 full seconds of silence after the line renders. Do not narrate during the hold. Then speak the principle once, flat, no inflection. Then the arc title compressed. Then black.
**Note:** Do not `echo` this before the closing narration is ready to follow. The 10-second hold is structural — it allows the viewer to read the principle, consider it, and arrive at the spoken version already prepared.

---

## Visual Design Requirements

### Terminal Setup

| Setting | Value |
|---------|-------|
| Background | #000000 (pure black) |
| Text color | #FFFFFF or light terminal default |
| Font | JetBrains Mono or Fira Code |
| Font size | 16–18px |
| Shell prompt | Minimal: `$ ` or `host $ ` only |
| Scrollback | Clear before each segment: `clear && printf '\033[3J'` |
| Window size | Fullscreen or consistent across all segments |

---

### Key Visual Moments (in order)

**1. The Density (Segment 1)**
The opening git log. 80 to 100 lines. This is the most visually dense terminal frame in the entire arc. Let the scroll happen without interruption. The viewer has not seen this many commits at once in any previous episode. The density is the argument: something was being actively worked. Hold 15 seconds after the output settles. The viewer should feel the weight before narration names what it is.

**2. The Correction Cluster (Segment 2)**
The filtered commit list — the governance, routing, and portability corrections surfaced from the 43-day log. This is the inverse of the opening: the viewer just saw the full density; now they see the specific commits where assumptions became corrections. The failure modes are not visible in this output. The corrections are. That distinction is the point.

**3. The Four-Commit Arc (Segment 3)**
Four commits on screen, one at a time, clearing between each. This is the spine of the video's middle section. The viewer sees the record of design change before hearing the description. Each commit message should be legible — large enough font, enough hold time. The sequence is: blank directory → hook correction → session bridge → corrections cluster representative → daemon spec. That progression is the entire architecture history.

**4. The Count (Segment 5)**
A single number. `wc -l` output from the 43-day log range. The number on a blank terminal. The contrast with Segment 1 is intentional: the opening showed the full density, the scrolling log, the visual mass. Segment 5 compresses all of that to one number. The viewer has seen what that number represents. Let them hold both at once.

**5. The Echo Close (Segment 7)**
`echo "If it is not committed, it is not real."` on a blank terminal. The principle rendered by the same mechanism as every other piece of output in this video. It is not a slide. It is not text over footage. It is a command and its output. Then it is spoken once. Then the three-phrase arc compression. Then black.

---

## Thumbnail Concept

**Primary option:**
The opening git log on screen — the full density visible, commits scrolling off the top edge. Overlaid at the bottom, in terminal font: "43 days. 4 designs. 1 principle." No further annotation. The density of the log is the visual argument; the overlay names the arc. The tension between the scrolling commits and the single compressed line is the thumbnail's argument in miniature.

**Alternative:**
Split frame. Left side: `git -C /home/koad/.juno log --oneline 6ea6978 -1` — "Initial commit: Juno entity gestated." Right side: `echo "If it is not committed, it is not real."` — the principle rendered in terminal. The first commit and the surviving principle, side by side. No annotation needed if both are legible.

**Text overlay (if used):**
- Primary: "43 days. 4 designs." in clean terminal font, upper third
- Secondary: "1 principle." — same font, lower third, separated from the primary to force the viewer to read them as a progression

---

## Audio Notes

- **Segment 1 — opening hold (15 seconds):** Complete silence. The git log scrolls, settles, sits. No ambient. No music. The viewer reads the commits. This is the longest unnarrated visual moment in the arc. Do not abbreviate the hold.
- **Segment 2 — between failure enumerations:** 4 seconds of silence between each failure name and its description. 4–5 seconds of silence between descriptions. Each failure is complete before the next begins.
- **"Four failures. One property." (Segment 2 close):** Two sentences. Four seconds between them. Six seconds after the second. This is the structural pivot of the video. Give it room.
- **"Each failure was an assumption that lived in the system's behavior but not in its committed files." (Segment 4):** Six seconds of silence after this line. Do not follow immediately with the supporting examples. The silence allows the viewer to test the claim before the four illustrations arrive.
- **"That is not luck." (Segment 4 close):** Delivered flat. Four seconds of silence after. No continuation. The implied contrast — recoverability as deliberate, not accidental — should arrive through silence, not additional narration.
- **The echo close (Segment 7):** 10 seconds of silence while the principle sits on screen. Then the spoken principle. Then "43 days. 4 designs. That sentence." — three pauses, one after each phrase. Then 8 seconds. Then black. No sound after the cut to black.
- **No background music throughout.** This is a post-mortem being filed. Music implies resolution that the content does not claim.

---

## B-Roll / Cutaway Options

The visual content is terminal-based throughout. There are three blank-terminal narration segments (Segments 4, 6, and the closing narration of Segment 5). For visual continuity during blank-terminal sections:

- **Revisit the opening density** — hold on the full 43-day git log without narration; useful as a visual beat between Segment 4's structural argument and Segment 5's commit count reveal
- **Hold on a specific commit message** — any of the four design commits; their brevity makes them readable even as B-roll
- **Blank terminal throughout** — recommended for Segments 4 and 6; the absence of commands during the structural argument and the daemon description is intentional; the viewer's attention should be on the narration

**Recommended:** Blank terminal for Segments 4 and 6. The visual emptiness during the structural argument (Segment 4) is not a gap — it is the correct register for synthesis narration. The arc closer should not lean on visuals for its credibility. The argument stands in the narration.

---

## Series Continuity

This is the arc closer for the retrospective failure-mode series. End card references:

- Day 44: "The First Thing That Broke" — engineering failure, silent hook, epistemological unease
- Day 45: "The Spec Was Wrong on Day 2" — specification failure, loop closed same session
- Day 46: "The Governance Gap Nobody Planned For" — governance gap, audit mechanism worked
- Day 47: "What the Dual Memory Problem Actually Costs" — memory divergence, permanent condition
- Day 48: "43 Days, 4 Designs, 1 Principle" — arc closer, the surviving principle

The arc is now complete. The next episode, if any, begins a new arc. Do not leave a "next episode" slot in the end card unless Day 49 exists and is production-ready.

---

## Pre-Recording Verification Checklist

- [ ] `git -C /home/koad/.juno log --oneline --since=2026-03-30 --until=2026-04-06` — returns 80+ lines; verify density before recording; narration adjusts to actual count
- [ ] `git -C /home/koad/.juno log --oneline 6ea6978 -1` — returns "Initial commit: Juno entity gestated"
- [ ] `git -C /home/koad/.juno log --oneline 290f521 -1` — returns "Add hooks override — juno loads claude instead of opencode"
- [ ] `git -C /home/koad/.juno log --oneline 54073c1 -1` — returns "hooks: inject $CWD/PRIMER.md into prompt when present"
- [ ] `git -C /home/koad/.juno log --oneline 2c5ff65 -1` — returns "governance: document bond dual-filing protocol — Janus process flag 2026-04-05"
- [ ] `git -C /home/koad/.juno log --oneline ccbffad -1` — returns "memories: document daemon architecture (005)"
- [ ] `git -C /home/koad/.juno log --oneline --since=2026-03-30 --until=2026-04-06 | wc -l` — returns a count; note actual number for narration
- [ ] Grep pattern for correction cluster returns meaningful output before recording
- [ ] Terminal font, background, and size set before recording
- [ ] Scrollback cleared between segments
- [ ] `echo "If it is not committed, it is not real."` typed correctly — verify before the closing segment
- [ ] Audio checked — quiet room, no fan or notification sounds
- [ ] OBS single-monitor capture confirmed, no chat overlay
- [ ] 15-second silent hold is comfortable — rehearse the opening before recording
