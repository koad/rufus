---
production: "Live Session: Sibyl Does Research"
date: 2026-04-07
content-calendar-ref: REALITY-2026-04-03.md (Monday Apr 7 slot)
runtime-target: 15 min raw → ~8 min at 2x, with select sections at real-time
recording-host: fourty4 (Mac Mini, ollama inference)
output-destination: YouTube full + Twitter 1-min clip
distribution-owner: Mercury
---

# Shot List & Recording Guide
## "Live Session: Sibyl Does Research"

---

## Research Task to Give Sibyl

**Task:** "What are the top three distribution channels for a privacy-first AI infrastructure project targeting self-hosted developers in 2026? For each channel: name, audience size/quality signal, ideal content format, and one concrete posting strategy."

**Why this task:**
- Directly relevant to koad:io's Reality Pillar (shows Sibyl doing real work, not a demo task)
- Output is verifiable — viewers can check the channels Sibyl names
- Involves multi-source synthesis (community data, platform signals, engagement patterns)
- Produces structured, scannable output that reads well on screen
- Can be cross-referenced against the content calendar Sibyl already authored

**How to deliver the task (via Juno handoff format):**
```bash
# Simulate Juno filing a research task to Sibyl's inbox
cat > ~/.sibyl/tasks/incoming/juno-2026-04-07-channels.md << 'EOF'
---
from: juno
to: sibyl
task-id: research-2026-04-07-001
priority: high
requested-by: faber
due: 2026-04-07
---

# Research Task: Distribution Channel Analysis

Faber needs a channel recommendation for the Reality Pillar launch.
Identify the top 3 distribution channels for koad:io targeting
privacy-first, self-hosted developer audiences in 2026.

For each channel provide:
1. Channel name + platform
2. Audience quality signal (engagement rate, technical depth)
3. Ideal content format for koad:io
4. One concrete posting strategy (what to post, when, with what hook)

Output to: ~/.sibyl/research/2026-04-07-channel-analysis.md
Commit when complete.
EOF
echo "Task filed by Juno at $(date)"
```

---

## Terminal Setup

**Machine:** fourty4 (Mac Mini)

**Layout (two-pane split, use tmux or iTerm split):**
- **Left pane (70% width):** Sibyl session — task intake, research execution, output writing
- **Right pane (30% width):** Watch pane — `watch -n2 cat ~/.sibyl/research/2026-04-07-channel-analysis.md` (shows file building in real time as Sibyl writes)

**Before recording — checklist:**
```bash
# 1. Clear terminal history and scrollback
clear && printf '\033[3J'

# 2. Set a clean prompt (no noise, no timestamps cluttering the screen)
export PS1="[sibyl@fourty4] $ "

# 3. Confirm ollama is running with the right model
ollama list          # confirm model present
ollama ps            # confirm nothing stale running

# 4. Confirm Sibyl task directory exists
ls ~/.sibyl/tasks/incoming/
ls ~/.sibyl/research/

# 5. Set font size large enough to read at 1080p after 2x speedup
# iTerm: Cmd+= until body text is ~18pt

# 6. Date proof — leave this visible at top before starting
date && echo "--- Recording starts ---"
```

**Font / theme:** Dark background (black or near-black), light monospace text. No powerline glyphs or status bars that distract from content.

---

## Shot List

### SECTION 1 — Context Set (real-time, ~45 sec raw)
**Goal:** Prove this is live, timestamped, unscripted.

| # | Shot | What to do | Notes |
|---|------|-----------|-------|
| 1.1 | Date stamp | Run `date` in terminal | Hold on screen 3 sec — timestamp proof |
| 1.2 | Entity state | Run `cat ~/.sibyl/memories/001-identity.md \| head -20` | Shows Sibyl has persistent identity, not a blank session |
| 1.3 | Task inbox check | Run `ls ~/.sibyl/tasks/incoming/` (empty first, then file the task) | Shows task arrives during recording |

**Edit note:** Keep at real-time. This 45 sec is the authenticity anchor — do not speed this section up.

---

### SECTION 2 — Juno Files the Task (real-time, ~30 sec raw)
**Goal:** Show cross-entity coordination — Juno → Sibyl handoff is visible.

| # | Shot | What to do | Notes |
|---|------|-----------|-------|
| 2.1 | File the task | Run the `cat >` heredoc command from the task setup above | Viewer sees the YAML brief being written to disk |
| 2.2 | Confirm receipt | `cat ~/.sibyl/tasks/incoming/juno-2026-04-07-channels.md` | Show the full task brief on screen |
| 2.3 | Sibyl reads task | Narrate (or title card): "Sibyl reads the brief" | Transition beat |

**Edit note:** Real-time. Short section — do not cut.

---

### SECTION 3 — Sibyl Executes Research (2x speed, ~6 min raw → 3 min edited)
**Goal:** Show real inference work — not a script, not canned output.

| # | Shot | What to do | Notes |
|---|------|-----------|-------|
| 3.1 | Invoke Sibyl | Run Sibyl with the task as input via ollama | Show the full prompt going in |
| 3.2 | Reasoning stream | Let ollama stream output to terminal | Viewer sees Sibyl thinking — do NOT cut the reasoning tokens |
| 3.3 | Watch pane activates | Right pane `watch` starts showing file content as Sibyl writes | Split-screen moment — left: reasoning; right: output appearing |
| 3.4 | First section written | Hold briefly at real-time when first channel output appears | Pause speedup momentarily (~5 sec) to let viewer read first result |
| 3.5 | Sections 2 and 3 complete | Resume 2x | Show full synthesis completing |
| 3.6 | Sibyl writes summary | Final synthesis paragraph appears | End of inference run |

**Edit note:** Speed up the inference stream at 2x. Add a subtle "2x" indicator in corner (small, unobtrusive). Pause to real-time at 3.4 so the first channel result is readable. If ollama produces verbose reasoning tokens, speed those to 3x but keep structured output sections at 1.5x.

---

### SECTION 4 — Output Review (real-time, ~45 sec raw)
**Goal:** Show the finished research artifact — readable, structured, real.

| # | Shot | What to do | Notes |
|---|------|-----------|-------|
| 4.1 | Open full output | `cat ~/.sibyl/research/2026-04-07-channel-analysis.md` | Scroll slowly — viewer reads the actual content |
| 4.2 | Scroll through all three channels | Scroll at reading pace (~3 sec per channel) | Don't rush — this is the proof moment |
| 4.3 | Line count proof | `wc -l ~/.sibyl/research/2026-04-07-channel-analysis.md` | Small detail that proves it's a real document |

**Edit note:** Real-time. This is payoff. Let it breathe.

---

### SECTION 5 — Git Commit (real-time, ~30 sec raw)
**Goal:** Timestamp the work on disk. "Not just output — it's in the record."

| # | Shot | What to do | Notes |
|---|------|-----------|-------|
| 5.1 | Stage the file | `cd ~/.sibyl && git add research/2026-04-07-channel-analysis.md` | |
| 5.2 | Commit | `git commit -m "research: channel analysis for Reality Pillar distribution (task juno-2026-04-07-001)"` | Show full commit message |
| 5.3 | Show commit hash | `git log --oneline -3` | Hash + timestamp on screen proves this is live |
| 5.4 | Date confirmation | `date` again | Bookend with timestamp — matches Section 1.1 |

**Edit note:** Real-time. Do NOT speed this section — the commit hash and timestamp are the cryptographic proof the piece promises.

---

### OPTIONAL SECTION 6 — Memory Update (real-time, ~20 sec)
**Condition:** Include only if Sibyl has a memory-update mechanism that runs post-research.

| # | Shot | What to do | Notes |
|---|------|-----------|-------|
| 6.1 | Memory write | Show Sibyl appending insight to `~/.sibyl/memories/` | Proves entities have persistent state across sessions |
| 6.2 | Verify memory | `tail -5 ~/.sibyl/memories/research-log.md` | Quick confirmation |

---

## Edit Notes Summary

| Section | Raw Duration | Playback Speed | Reason |
|---------|-------------|---------------|--------|
| 1 (Date + identity) | ~45 sec | 1x real-time | Authenticity anchor |
| 2 (Task filing) | ~30 sec | 1x real-time | Coordination handoff — must be readable |
| 3 (Inference) | ~6 min | 2x (3x for reasoning tokens) | Inference is long; keep viewer engaged |
| 3.4 pause | ~5 sec | 1x real-time | First output reveal — let it land |
| 4 (Output review) | ~45 sec | 1x real-time | Proof moment — must be readable |
| 5 (Git commit) | ~30 sec | 1x real-time | Timestamp proof — non-negotiable |
| 6 (Memory, optional) | ~20 sec | 1x real-time | State persistence proof |
| **Total raw** | **~9 min** | | |
| **Total edited** | **~6–7 min** | | Tight, punchy |

**Target final runtime:** 6–8 min. Under 10 min is essential for YouTube retention and Twitter clip-ability.

---

## Audio / Narration

No voice narration needed. The terminal output tells the story. Use:
- Subtle lo-fi background music (low volume, non-distracting) during sped-up inference section
- Cut music for Sections 1, 4, 5 (silence = weight = proof)
- Optional: brief title cards at section transitions ("Juno files the task" / "Sibyl reasons" / "Output committed to git")

---

## Title Card / Caption Overlays

| Timestamp (approx) | Text |
|---|---|
| 0:00 | "Sibyl Does Research — Live Session, Apr 7 2026" |
| 0:05 | "No script. No demo. Running on local ollama at fourty4." |
| 0:45 | "Juno files the research task →" |
| 1:15 | "Sibyl reads the brief" |
| 1:30 | "Sibyl running on ollama — inference in progress" |
| ~5:00 | "Output appearing in real time →" |
| ~6:00 | "Research complete. Committing to git." |
| ~7:00 | "Work on disk. Timestamped. Verifiable." |

---

## 1-Minute Twitter/X Clip Cut

Extract from the full recording:
- **0:00–0:05:** Date stamp (timestamp proof)
- **0:05–0:20:** Juno task brief visible on screen
- **0:20–0:45:** Inference stream at 3x speed (with 2x overlay indicator)
- **0:45–0:55:** `cat` of output — first channel result visible
- **0:55–1:00:** `git log --oneline` showing the commit

Caption: "Sibyl received a research task from Juno. Read sources. Synthesized findings. Committed output. All on local hardware. No cloud. No API calls. This is what entities actually do."

---

## Pre-Recording Prep Checklist

- [ ] fourty4 is on, ollama running, correct model loaded
- [ ] `~/.sibyl/tasks/incoming/` directory exists and is empty
- [ ] `~/.sibyl/research/` directory exists
- [ ] `~/.sibyl` is a git repo with clean working tree (`git status`)
- [ ] tmux or iTerm split configured (70/30 left/right)
- [ ] Font size set for legibility at 1080p after 2x speedup
- [ ] Background music cued (for inference section)
- [ ] Recording software ready (OBS or QuickTime on fourty4)
- [ ] Do a dry run of the ollama invocation to confirm model responds correctly
- [ ] Clear terminal scrollback immediately before hitting record

---

## Post-Production Handoff to Mercury

When recording is cut and exported:
- Upload to YouTube as unlisted for Mercury review before publishing
- Provide Mercury with:
  - Full title: "Live Session: Sibyl Does Research (koad:io Entity Work, Apr 7 2026)"
  - Description: [Mercury to draft — include link to research output file in ~/.sibyl/research/]
  - Tags: `#AIAgents #LocalLLM #ollama #SelfHosted #koadio`
  - Thumbnail frame: Section 5.3 — the `git log --oneline` showing the commit hash
  - Twitter clip: 1-min extract per cut notes above
  - r/LocalLLaMA post title: "Ran a local AI entity doing actual research work — here's the session recording"
