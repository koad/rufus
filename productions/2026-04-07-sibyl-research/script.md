---
production: "Live Session: Sibyl Does Research"
issue: https://github.com/koad/rufus/issues/7
date: 2026-04-07
type: title-card-script
format: terminal-capture, no voice-over
companion: shot-list.md
status: production-ready
---

# Script — "Live Session: Sibyl Does Research"

**Format note:** This is a no-voice-over terminal-capture video. The "script" is the sequence of title cards, the exact commands to run on screen, and the framing copy for each section. Nothing is spoken aloud. The terminal output is the content.

---

## OPENING TITLE CARD

**Card 1 (hold 3 sec):**
> Sibyl Does Research
> Live Session — Apr 7, 2026

**Card 2 (hold 4 sec):**
> No script. No demo.
> Running on local ollama — fourty4 (Mac Mini).
> What you see is what happened.

---

## SECTION 1 — The Record Starts Here

*Terminal: left pane, clean prompt.*

**Title card (hold 2 sec):**
> The session starts with a timestamp.
> Everything from here is in the record.

**Commands to run (exact, in order):**

```bash
date
```

Hold on output 3 seconds. The timestamp anchors everything that follows.

```bash
cat ~/.sibyl/memories/001-identity.md | head -20
```

Scroll slowly. Let the identity block read. This is Sibyl's persistent self: not a fresh blank session, a continuous entity with history.

```bash
ls ~/.sibyl/tasks/incoming/
```

Empty. The inbox is clear. No pre-loaded tasks. We're starting from zero.

---

## SECTION 2 — Juno Files the Task

**Title card (hold 3 sec):**
> Juno → Sibyl
> Cross-entity task handoff.

*Framing: the viewer sees Juno (running elsewhere in the stack) drop a task brief into Sibyl's inbox. This is the coordination layer — no Slack, no email, no dashboard. A file on disk is the message.*

**Commands to run (exact):**

```bash
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

After the heredoc writes: pause 2 seconds on the "Task filed by Juno" confirmation line.

```bash
cat ~/.sibyl/tasks/incoming/juno-2026-04-07-channels.md
```

Scroll through the brief at reading pace. The viewer reads the actual task. There is no hidden setup. This is exactly what Sibyl will receive.

**Title card (hold 2 sec):**
> Task received.
> Sibyl reads the brief.

---

## SECTION 3 — Sibyl Executes Research

**Title card (hold 3 sec):**
> Sibyl running on ollama — local inference.
> No API call leaving this machine.

*Both panes now active. Left: Sibyl's inference stream. Right: the output file building in real time.*

**Right pane — start the watch command before invoking Sibyl:**

```bash
watch -n2 "cat ~/.sibyl/research/2026-04-07-channel-analysis.md 2>/dev/null || echo '(file not yet created)'"
```

**Left pane — invoke Sibyl:**

```bash
PROMPT="$(cat ~/.sibyl/tasks/incoming/juno-2026-04-07-channels.md)" sibyl
```

*What happens now:*
- ollama loads the model
- Sibyl reads the task brief
- Inference begins — reasoning tokens stream to terminal
- Sibyl writes structured output to `~/.sibyl/research/2026-04-07-channel-analysis.md`
- Right pane updates every 2 seconds as the file grows

**During inference stream — title card (overlay, small, corner):**
> 2x speed

Do not cut the reasoning stream. Let it run. Speed it up in post. The viewer sees Sibyl thinking — this is not a spinner, this is actual token generation working through the problem.

**At the moment the first channel result appears in the output file (right pane):**

Pause speedup to 1x for approximately 5 seconds.

**Title card (hold 2 sec, then resume 2x):**
> First channel analysis — appearing now.

Resume 2x through the rest of the inference. When Sibyl's summary paragraph writes, slow back to 1x for the final lines.

**After inference completes:**

**Title card (hold 3 sec):**
> Research complete.
> Output written to disk.

---

## SECTION 4 — Output Review

**Title card (hold 2 sec):**
> The work. On disk. Right now.

*This is the proof section. No edits. No cuts. Real-time.*

**Commands to run:**

```bash
cat ~/.sibyl/research/2026-04-07-channel-analysis.md
```

Scroll at reading pace — approximately 3 seconds per channel section. Do not rush. This is the payoff. Let the viewer read.

```bash
wc -l ~/.sibyl/research/2026-04-07-channel-analysis.md
```

Hold on the line count 2 seconds. Small detail. Proves this is a real document, not a placeholder.

---

## SECTION 5 — The Git Commit

**Title card (hold 3 sec):**
> Work on disk.
> Now it goes in the record.

*The commit is the proof the video promises. Not just terminal output — a hash, a timestamp, a verifiable entry in a public repo. The viewer can go check.*

**Commands to run (exact):**

```bash
cd ~/.sibyl && git add research/2026-04-07-channel-analysis.md
```

```bash
git commit -m "research: channel analysis for Reality Pillar distribution (task juno-2026-04-07-001)"
```

Hold on the commit confirmation output 3 seconds. Let the hash appear.

```bash
git log --oneline -3
```

Hold on the log output 5 seconds. The commit hash + message + timestamp are on screen. This frame is the thumbnail.

```bash
date
```

Hold 3 seconds. Same format as the opening timestamp. Bookend. The session started with a date, it ends with a date. What happened in between is in the record.

**Closing title card (hold 5 sec):**
> Sibyl received a task from Juno.
> Ran inference locally on fourty4.
> Wrote structured output to disk.
> Committed it with her identity.
> That commit is in the public record — koad/sibyl on GitHub.
> This is what entities actually do.

---

## OPTIONAL SECTION 6 — Memory Update

*Include only if Sibyl's memory-write mechanism runs post-research.*

**Title card (hold 2 sec):**
> Sibyl logs the session to her own memory.

**Commands:**

```bash
tail -5 ~/.sibyl/memories/research-log.md
```

Hold 3 seconds. Proof that Sibyl has persistent state — she'll remember this task in future sessions.

---

## CLOSING CREDITS CARD

**Card (hold 4 sec):**
> koad:io — Sovereign AI Infrastructure
> github.com/koad
> github.com/sponsors/koad

---

## Command Sequence at a Glance

For the operator running the session — paste reference only. Run commands one at a time during recording, not from a script runner.

```
# Section 1
date
cat ~/.sibyl/memories/001-identity.md | head -20
ls ~/.sibyl/tasks/incoming/

# Section 2
cat > ~/.sibyl/tasks/incoming/juno-2026-04-07-channels.md << 'EOF'
[heredoc — see shot-list.md]
EOF
cat ~/.sibyl/tasks/incoming/juno-2026-04-07-channels.md

# Section 3 — right pane first
watch -n2 "cat ~/.sibyl/research/2026-04-07-channel-analysis.md 2>/dev/null || echo '(file not yet created)'"
# Section 3 — left pane
PROMPT="$(cat ~/.sibyl/tasks/incoming/juno-2026-04-07-channels.md)" sibyl

# Section 4
cat ~/.sibyl/research/2026-04-07-channel-analysis.md
wc -l ~/.sibyl/research/2026-04-07-channel-analysis.md

# Section 5
cd ~/.sibyl && git add research/2026-04-07-channel-analysis.md
git commit -m "research: channel analysis for Reality Pillar distribution (task juno-2026-04-07-001)"
git log --oneline -3
date

# Optional Section 6
tail -5 ~/.sibyl/memories/research-log.md
```

---

## Title Card Copy — Complete List

| Section | Text |
|---------|------|
| Opening 1 | "Sibyl Does Research / Live Session — Apr 7, 2026" |
| Opening 2 | "No script. No demo. / Running on local ollama — fourty4 (Mac Mini). / What you see is what happened." |
| S1 intro | "The session starts with a timestamp. / Everything from here is in the record." |
| S2 intro | "Juno → Sibyl / Cross-entity task handoff." |
| S2 close | "Task received. / Sibyl reads the brief." |
| S3 intro | "Sibyl running on ollama — local inference. / No API call leaving this machine." |
| S3 first-output | "First channel analysis — appearing now." |
| S3 close | "Research complete. / Output written to disk." |
| S4 intro | "The work. On disk. Right now." |
| S5 intro | "Work on disk. / Now it goes in the record." |
| S5 closing | "Sibyl received a task from Juno. / Ran inference locally on fourty4. / Wrote structured output to disk. / Committed it with her identity. / That commit is in the public record — koad/sibyl on GitHub. / This is what entities actually do." |
| S6 intro (optional) | "Sibyl logs the session to her own memory." |
| Credits | "koad:io — Sovereign AI Infrastructure / github.com/koad / github.com/sponsors/koad" |

---

## Key Argument — The Closing Beat

The video builds to one claim: **the git commit is the proof.**

Not the terminal output. Not the cat command. The commit. Because:

1. It has a hash — unique, verifiable
2. It has a timestamp — matches the date you saw at the start of the recording
3. It has an author — `Sibyl <sibyl@kingofalldata.com>` — the entity signed the work
4. It's in a public repo — anyone watching can go to koad/sibyl and see it

The four-line closing title card delivers this argument without voice-over. The shot-list.md Section 5.3 frame — `git log --oneline -3` — is the thumbnail because it's the single frame that makes the case.

---

## What to Avoid

- **Do not narrate.** The title cards are sufficient. Voice-over risks talking over readable terminal content and introduces a scripting burden that undermines the "live session" claim.
- **Do not skip the reasoning stream.** The token stream showing Sibyl thinking is the most differentiating footage this video has. Speed it up; do not cut it.
- **Do not rush Section 4.** The output review is the payoff. Three seconds per channel section is not slow — it's correct.
- **Do not edit the commit section.** The timestamp on the commit must match the date shown in Section 1. Any cut that hides the timestamp removes the proof.
