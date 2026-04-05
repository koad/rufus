---
title: "Sibyl Does Research — Shot Script"
production-id: 2026-04-07-sibyl-research
date-scripted: 2026-04-05
recording-date: 2026-04-07
recording-mode: terminal-capture-only (asciinema, no OBS)
recording-host: fourty4 (Mac Mini, ollama inference)
runtime-target: 15 min final (raw ~45-60 min, sped to match)
status: scripted — awaiting recording
distribution-owner: Mercury
---

# Shot Script: "Sibyl Does Research"
## Live Session — koad:io Entity Work, Apr 7 2026

---

## Research Prompt to Give Sibyl

**Primary prompt:**

> "What does the developer community actually want from AI agent frameworks?
> What pain points aren't served by existing tools?
> Survey recent developer discussions (HN, Reddit r/LocalLLaMA, GitHub Issues on major agent frameworks),
> identify the top 5 unmet needs, and produce a structured report with evidence.
> Output to ~/.sibyl/research/2026-04-07-agent-framework-gaps.md and commit when complete."

**Why this prompt:**

- It maps to what koad:io is actually building — viewers can see Sibyl researching the exact problem space
- Multi-step synthesis (survey → identify → structure → commit) makes the session visually interesting
- Output is verifiable — developers in the audience can check the sources Sibyl names
- The result feeds directly into Mercury's content pipeline and Faber's positioning work
- "What aren't you being served?" is a universal hook — every developer watching has an opinion

**Fallback / secondary prompt** (if primary runs too long or stalls):

> "What are the top 3 distribution channels for a privacy-first AI infrastructure project
> targeting self-hosted developers in 2026?
> For each: name, audience quality signal, ideal content format, and one concrete posting strategy.
> Output to ~/.sibyl/research/2026-04-07-channel-analysis.md and commit."

---

## Pre-Session Setup (off-camera)

Run these before hitting record:

```bash
# 1. Confirm fourty4 is reachable
ssh fourty4 'hostname && date'

# 2. Confirm ollama is running with the right model
ssh fourty4 'ollama list && ollama ps'

# 3. Confirm Sibyl directories exist
ssh fourty4 'ls ~/.sibyl/tasks/incoming/ && ls ~/.sibyl/research/'

# 4. Clean any stale files from the research slot
ssh fourty4 'ls ~/.sibyl/research/ | grep 2026-04-07'

# 5. Confirm ~/.sibyl is a clean git repo
ssh fourty4 'cd ~/.sibyl && git status'

# 6. Set terminal font to readable size (18pt+ body, dark theme)
# iTerm: Cmd+= until comfortable at a 1080p recording resolution

# 7. Configure tmux split
ssh fourty4 'tmux new-session -d -s sibyl-record'
# Left pane (70%): Sibyl session
# Right pane (30%): watch pane for output file
```

---

## Title Card / Intro Text

Overlay at the START of the final video (0:00–0:10):

```
"Sibyl Does Research"
Live session — Apr 7 2026
Running on local hardware. No cloud. No API calls.
```

Sub-text (smaller, lower third):
```
fourty4 — Mac Mini — ollama inference
koad:io sovereign entity
```

---

## Scene-by-Scene Breakdown

---

### SCENE 1 — Timestamp Proof (real-time, ~30 sec raw → 30 sec edited)

**What happens:**
Operator runs `date` and `whoami` at the top of a clean terminal. No prior session history visible.

**Screen content:**
```
Mon Apr  7 09:12:04 EDT 2026
sibyl
```

**Cue to operator:**
- Clear scrollback first: `clear && printf '\033[3J'`
- Then run `date` — pause 3 seconds — run `whoami`
- Do NOT run any other commands before this

**Title card overlay:**
`"Live. Unscripted. Timestamped."`

**Edit note:** Hold at 1x. This 30 seconds is the authenticity anchor for the whole piece.

---

### SCENE 2 — Identity Check (real-time, ~30 sec raw → 30 sec edited)

**What happens:**
Show that Sibyl has a persistent identity — she is not a blank session.

**Commands to run:**
```bash
cat ~/.sibyl/memories/001-identity.md | head -20
```

**What viewer sees:**
Sibyl's identity file — ENTITY=sibyl, her role, her specialties. Proof she's not a prompt, she's an entity.

**Title card overlay:**
`"Sibyl — Research & Intelligence entity"`

**Edit note:** Real-time. Short. Don't linger — one scroll pass and move on.

---

### SCENE 3 — Juno Files the Task (real-time, ~60 sec raw → 60 sec edited)

**What happens:**
Operator simulates Juno filing a research task to Sibyl's task inbox. Viewer sees inter-entity coordination — Juno → Sibyl handoff happening on disk.

**Commands to run:**
```bash
# Show inbox is empty
ls ~/.sibyl/tasks/incoming/

# File the task via heredoc
cat > ~/.sibyl/tasks/incoming/juno-2026-04-07-gaps.md << 'EOF'
---
from: juno
to: sibyl
task-id: research-2026-04-07-001
priority: high
requested-by: faber
due: 2026-04-07
---

# Research Task: AI Agent Framework Gap Analysis

The community wants to understand what developer pain points
existing AI agent frameworks don't serve.

Survey developer discussions and identify the top 5 unmet needs.
Produce a structured report with evidence.

Output to: ~/.sibyl/research/2026-04-07-agent-framework-gaps.md
Commit when complete.
EOF

echo "Task filed by Juno at $(date)"

# Show the filed task
cat ~/.sibyl/tasks/incoming/juno-2026-04-07-gaps.md
```

**What viewer sees:**
- Empty inbox → task file being written → confirmation → task contents on screen

**Title card overlay (at cat output):**
`"Juno files the research brief →"`

**Edit note:** Real-time. The YAML brief must be readable. Do not cut or speed this section.

---

### SCENE 4 — Sibyl Executes (2x–3x speed, ~30–45 min raw → 8 min edited)

**What happens:**
Sibyl's inference session runs. Operator invokes Sibyl with the task as input via the entity's hook or ollama directly. Left pane shows inference stream; right pane shows output file building.

**Commands to run (left pane):**
```bash
# Start the watch pane in the right split first
# (tmux split-pane -h -l 30%)
watch -n2 cat ~/.sibyl/research/2026-04-07-agent-framework-gaps.md

# Then in the left pane — invoke Sibyl
PROMPT="$(cat ~/.sibyl/tasks/incoming/juno-2026-04-07-gaps.md)" sibyl
# OR if entity hook doesn't handle task files:
ollama run sibyl "$(cat ~/.sibyl/tasks/incoming/juno-2026-04-07-gaps.md)"
```

**Sub-sections within SCENE 4:**

| Sub-scene | Raw duration | Edit speed | Viewer sees |
|-----------|-------------|-----------|-------------|
| 4a — Invocation | ~15 sec | 1x real-time | Full prompt going in — must be readable |
| 4b — Reasoning tokens | ~10 min | 3x | Sibyl thinking — fast stream, shows work |
| 4c — First structure | ~2 min | 1.5x | First "Unmet Need #1" header appears in watch pane |
| 4d — PAUSE at first result | ~10 sec | 1x real-time | Let viewer read the first finding — payoff |
| 4e — Remaining 4 needs | ~15 min | 2x | Watch pane fills up — entity doing real synthesis |
| 4f — Summary writing | ~3 min | 1.5x | Final synthesis paragraph — Sibyl wraps the report |
| 4g — Commit confirmation | ~15 sec | 1x real-time | "Output committed" or equivalent close signal |

**Title card overlays:**
- At 4a: `"Sibyl reads the brief"`
- At 4b: `"Reasoning in progress — ollama on fourty4"`
- At 4c/4d: `"Output appearing in real time →"` (right pane highlight)
- At 4f: `"Research complete"`

**Edit notes:**
- Add a small unobtrusive speed indicator in the corner (e.g., `"2x"` / `"3x"`) whenever sped up
- The watch pane building in real-time is the visual hook — make sure it's readable
- If reasoning tokens are very verbose, 3x is fine — the viewer understands "thinking"
- Do NOT cut the first-output reveal (4d) — this is the money shot

**Suggested music:**
Lo-fi / ambient. Low volume (listener should forget it's there). Cue at start of 4b (reasoning stream), cut at 4d (first result reveal), resume at 4e, cut at 4g (commit signal). Silence = weight for the proof moments.

---

### SCENE 5 — Output Review (real-time, ~60 sec raw → 60 sec edited)

**What happens:**
Operator displays the finished research artifact. Scrolls at reading pace through all five unmet needs. Viewer reads the actual content.

**Commands to run:**
```bash
# Full output read
cat ~/.sibyl/research/2026-04-07-agent-framework-gaps.md

# Pause during scroll to let each section land

# Line count proof
wc -l ~/.sibyl/research/2026-04-07-agent-framework-gaps.md
```

**Title card overlay:**
`"Work on disk. Read it."`

**Edit note:** Real-time. Slow scroll. This is the payoff — do not rush. Three seconds per finding minimum.

---

### SCENE 6 — Git Commit (real-time, ~45 sec raw → 45 sec edited)

**What happens:**
The research output is committed to git. Hash and timestamp are visible on screen. Cryptographic proof the work happened, when it happened.

**Commands to run:**
```bash
cd ~/.sibyl
git add research/2026-04-07-agent-framework-gaps.md
git commit -m "research: AI agent framework gap analysis (task juno-2026-04-07-001)"
git log --oneline -3
date
```

**What viewer sees:**
Commit hash. Timestamp. Author. The record.

**Title card overlay:**
`"Work on disk. Timestamped. Verifiable."`

**Edit note:** Real-time. Non-negotiable. The commit hash is the closing proof. Hold on `git log --oneline` output for 3 seconds minimum.

---

### OPTIONAL SCENE 7 — Memory Update (real-time, ~30 sec)

**Condition:** Include only if Sibyl has a post-research memory update mechanism.

**Commands:**
```bash
# Show Sibyl appending to her research log
tail -10 ~/.sibyl/memories/research-log.md
```

**Title card:**
`"Sibyl remembers. Entities have state."`

**Edit note:** Include if the file exists and is populated. Skip cleanly if not — do not fake it.

---

## Timing Summary

| Scene | Raw duration | Edit speed | Edited duration |
|-------|-------------|-----------|----------------|
| 1 — Timestamp proof | 30 sec | 1x | 30 sec |
| 2 — Identity check | 30 sec | 1x | 30 sec |
| 3 — Juno files task | 60 sec | 1x | 60 sec |
| 4 — Inference (full) | ~35 min | 2x–3x | ~8 min |
| 4d — First result pause | 10 sec | 1x | 10 sec |
| 5 — Output review | 60 sec | 1x | 60 sec |
| 6 — Git commit | 45 sec | 1x | 45 sec |
| 7 — Memory (optional) | 30 sec | 1x | 30 sec |
| **Total** | **~38 min** | | **~12–13 min** |

**Target final runtime:** 12–15 minutes. If raw inference runs shorter (20–25 min), final cut lands around 8–10 min — acceptable.

---

## 1-Minute Twitter/X Clip Cut

Extract:
- 0:00–0:05: `date` timestamp proof
- 0:05–0:20: Juno's task brief visible on screen
- 0:20–0:45: Inference stream at 3x (with speed indicator overlay)
- 0:45–0:55: `cat` of output — first gap finding visible
- 0:55–1:00: `git log --oneline` commit hash close

**Caption:**
"Sibyl received a research task from Juno. Synthesized developer pain points from public sources. Committed the report to git. All on local hardware. No cloud. This is what entities actually do."

---

## Post-Production Handoff to Mercury

When recording is cut and exported:
- Upload YouTube as unlisted first — Mercury reviews before publish
- Provide: full title, description (see distribution file), tags, thumbnail frame (git log scene)
- Twitter clip: 1-min extract per above
- r/LocalLLaMA post: "Ran a local AI entity doing actual research — here's the full session"
