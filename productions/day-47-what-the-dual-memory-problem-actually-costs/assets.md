---
title: "What the Dual Memory Problem Actually Costs — Assets"
day: 47
date: 2026-05-17
production-owner: Rufus
status: production-ready
---

# Assets: Day 47 — "What the Dual Memory Problem Actually Costs"

## Terminal Commands (in order of appearance)

### Segment 1 — Opening

```bash
cat /home/koad/.juno/PRIMER.md
```

**Purpose:** Opens the PRIMER and reveals the Day 40 staleness. This is the opening visual argument.
**Hold:** 8 seconds on the "Current state" section showing Day 40.
**Output requirement:** Must contain a "Day 40" reference in the current state or queue block. Verify before recording.

---

### Segment 2 — Layer One (the committed record)

```bash
ls /home/koad/.juno/memories/ | wc -l
```

**Purpose:** Shows the scale of the committed memory — 55 files (or whatever the current count is). Establishes that the committed record is substantial, not minimal.
**Hold:** 5 seconds. Let the number sit.

```bash
cat /home/koad/.juno/memories/001-identity.md
```

**Purpose:** Shows the ground truth — who Juno is, what the entity's role is, what survives every session. This is layer one in its most concrete form.
**Hold:** 8 seconds.

```bash
cat /home/koad/.juno/memories/feedback_always_commit.md
```

**Purpose:** Shows the feedback file pattern — a behavioral correction that was explicitly committed as a permanent skill. Illustrates what the committed record is for.
**Hold:** 6 seconds.

---

### Segment 2 — Layer Three (Claude Code memory layer reveal)

```bash
ls ~/.claude/projects/-home-koad--juno/memory/
```

**Purpose:** Reveals the third layer — harness-specific memory that lives outside the entity repo, invisible to any other harness. This reframes the "two-layer" description and shows the full complexity.
**Hold:** 6 seconds. The MEMORY.md file appears. No narration while it renders.
**Note:** This path is the Claude Code projects directory. Confirm it contains MEMORY.md before recording.

---

### Segment 3 — Staleness Demonstrated

```bash
grep -r "Day 40" /home/koad/.juno/PRIMER.md | head -5
```

**Purpose:** The visual proof that divergence is present — not as a system error, not as a warning, just as lines in a file that are factually stale. The output renders cleanly. That is the point.
**Hold:** 8 seconds of silence before narrating. Let the viewer see the lines in context.

---

### Segment 6 — What Closes the Gap

```bash
cat /home/koad/.juno/memories/feedback_dual_memory.md
```

**Purpose:** The documented answer — the dual memory convention, committed as a feedback file, as evidence that the discipline approach is already codified.
**Hold:** 8 seconds.

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

### Key Visual Moments (in order)

**1. The Opening Stale PRIMER (Segment 1)**
The most important visual in the video. `cat /home/koad/.juno/PRIMER.md` renders — the viewer sees a complete, well-formatted file, no errors, no warnings. Navigate to or let it scroll to the current state block. "Day 40" appears. Hold 8 seconds. The visual argument is: this file is fine and it is wrong.

**2. The Memory Count (Segment 2)**
`ls /home/koad/.juno/memories/ | wc -l` — a single number. 55 or similar. Hold 5 seconds. The number tells the viewer: this is not a minimal system. There is substantial committed memory. That makes the divergence more striking, not less.

**3. The Two-Layer Progression (Segment 2)**
Three successive `cat` commands, each cleared between them. The progression is: identity file (layer one ground truth) → feedback file (the correction pattern) → Claude Code memory layer (the hidden third layer). Each one builds the picture. Do not rush between them. Clear screen between each.

**4. The Side-by-Side Gap (Segment 2–3 transition)**
The conceptual "side-by-side" moment is not a diagram — it is the successive terminal frames. `cat 001-identity.md` shows who Juno is. `grep "Day 40" PRIMER.md` shows where Juno thinks it is. The viewer holds both in memory at once. The gap is the space between those two commands.

**5. The Grep Result (Segment 3)**
`grep -r "Day 40" /home/koad/.juno/PRIMER.md | head -5` — the output is clean match lines. No error. No warning. The staleness is invisible to the filesystem. That is the argument. Hold 8 seconds of silence. This is the visual equivalent of the hook that returned success while routing to a dead machine (Day 44). The system shows nothing wrong because nothing is wrong at the file level.

**6. The feedback_dual_memory.md Close (Segment 6)**
The final terminal scene. `cat /home/koad/.juno/memories/feedback_dual_memory.md` shows the operational answer — the convention already documented. This is the "discipline" answer made concrete. After the hold, the daemon is described verbally, with no terminal scene (it does not yet exist to show).

---

## Thumbnail Concept

**Primary option:**
Split terminal frame. Left side: `cat /home/koad/.juno/PRIMER.md` rendered, cursor on the line reading "Day 40 — Alice Phase 2A live, blog PR open" (or equivalent). Right side: same terminal, a `date` command output showing 2026-05-17 (Day 47). No annotation text needed — the gap between "Day 40" and the date is the entire argument. The split is horizontal (top/bottom) or vertical (left/right) — vertical preferred as it reads more naturally as a before/after or here/there.

**Alternative:**
Single terminal frame, fullscreen. The `ls /home/koad/.juno/memories/ | wc -l` output showing the count — "55" — large enough to read. Below it, a `grep` result showing "Day 40" in context. The number of committed files against the staleness of the PRIMER is the tension.

**Text overlay (if used):**
- Primary: "Day 40 → Day 47" in clean terminal font, lower third
- Secondary: "What the dual memory problem actually costs" — title treatment, understated

---

## Audio Notes

- **Segment 1:** Quietest segment in the video. The gap between "Day 40" and "Today is Day 47" is entirely silence — no music, no ambient. The room silence is the effect.
- **Segment 5 — "This is not fixable by better tooling":** 6 seconds of silence after this line. Do not fill it. The silence is structural. It gives the viewer time to test the claim before the explanation continues.
- **Closing silence:** "Put it in a commit." → 6 seconds → black. Same treatment as Day 46's closing. No sound after the final line.
- **No background music throughout.** This is a diagnostic video. Music implies emotional distance or resolution that the content does not have.

---

## B-Roll / Cutaway Options

Day 47 has no incident report, no GitHub issue, no commit to point to. The visual content is entirely terminal — file reads and shell commands. There is no B-roll in the traditional sense. If a visual break is needed between narration segments (Segments 4 and 5 are blank-terminal narration), options are:

- Hold on the PRIMER.md "Day 40" section without narration — revisit the opening image
- Hold on the `wc -l` count — revisit the memory file count as context for the "how many corrections were never committed" beat
- No cutaway — blank terminal throughout Segments 4 and 5 is correct; the viewer's attention should be on the narration

**Recommended:** No cutaway. The blank terminal during the failure mode descriptions (Segment 4) and the honest moment (Segment 5) is intentional. The absence of commands is part of the diagnostic register.

---

## Series Continuity

This is episode 4 of the retrospective failure-mode arc. End card should reference:

- Day 44: "The First Thing That Broke" — engineering failure, silent hook
- Day 45: "The Spec Was Wrong on Day 2" — specification failure, loop closed same session
- Day 46: "The Governance Gap Nobody Planned For" — governance gap, audit mechanism worked
- Day 47: "What the Dual Memory Problem Actually Costs" — memory divergence, permanent condition

The arc is now complete. If a Day 48 end card is needed, it does not yet exist. Leave the "next episode" slot blank or cut at Day 47 in the series recap.

---

## Pre-Recording Verification Checklist

- [ ] `cat /home/koad/.juno/PRIMER.md` — contains "Day 40" in current state block
- [ ] `ls /home/koad/.juno/memories/ | wc -l` — returns count in 50s (exact number for narration)
- [ ] `cat /home/koad/.juno/memories/001-identity.md` — readable, complete identity file
- [ ] `cat /home/koad/.juno/memories/feedback_always_commit.md` — readable, correction text visible
- [ ] `cat /home/koad/.juno/memories/feedback_dual_memory.md` — readable, dual memory convention documented
- [ ] `ls ~/.claude/projects/-home-koad--juno/memory/` — returns MEMORY.md
- [ ] `grep -r "Day 40" /home/koad/.juno/PRIMER.md | head -5` — returns match lines (not empty)
- [ ] Terminal font, background, and size set before recording
- [ ] Scrollback cleared
- [ ] Audio checked — quiet room, no fan or notification sounds
- [ ] OBS single-monitor capture confirmed, no chat overlay
