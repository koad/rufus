---
title: "Director's Notes — Live Session: Sibyl Does Research"
video: 2026-04-07-sibyl-research
author: Rufus
date: 2026-04-05
status: production-ready
---

# Director's Notes: "Live Session: Sibyl Does Research"

## Why This Video Matters

Every other video in this series shows files and git logs as evidence. This one shows the work happening. Sibyl receiving a task from Juno, reasoning through it, writing structured output to disk, and committing it — on local hardware, no cloud API, no demo mode. That is the claim the koad:io ecosystem makes. This video is the proof.

---

## System State at the Start of Recording

This video is the most operationally complex in the schedule. It requires setup on fourty4 — a separate physical machine — before recording begins. Budget 30 minutes for setup and a dry run. Do not skip the dry run.

**Machine: fourty4 (Mac Mini). Non-negotiable.**
The entire point of this video is local inference on owned hardware. If you record on any other machine, the premise is false. If fourty4 is unavailable, reschedule.

**What must be true before the screen recorder starts:**

- SSH from thinker to fourty4 is working: `ssh fourty4 echo ok` returns `ok`
- ollama is running on fourty4: `ssh fourty4 'ollama list && ollama ps'` — confirm the intended model is present and no stale process is running
- `~/.sibyl` on fourty4 is current: `ssh fourty4 'cd ~/.sibyl && git pull'`
- `~/.sibyl/tasks/incoming/` exists on fourty4: `ssh fourty4 'ls ~/.sibyl/tasks/incoming/'` — must not error
- `~/.sibyl/research/` exists on fourty4: `ssh fourty4 'ls ~/.sibyl/research/'` — must not error
- `~/.sibyl` is a clean git repo: `ssh fourty4 'cd ~/.sibyl && git status'` must show "nothing to commit, working tree clean"
- The specific research output file does NOT exist yet: `ssh fourty4 'ls ~/.sibyl/research/2026-04-07-channel-analysis.md 2>&1'` must show "No such file"
- Dry run complete: run the ollama invocation once off-camera and confirm it produces structured output before recording begins. If the model returns garbage, switch models or reschedule.

**Terminal arrangement on fourty4 (set this up before recording begins):**
- tmux or iTerm two-pane horizontal split: 70% left (Sibyl session), 30% right (watch pane)
- Right pane pre-loaded with: `watch -n2 cat ~/.sibyl/research/2026-04-07-channel-analysis.md`
- Font size: 18pt or larger — inference output will be sped up 2x in post; if the text is small at 1x it will be illegible at 2x
- Prompt set to minimal: `export PS1="[sibyl@fourty4] $ "`
- Scrollback buffer: 10,000+ lines
- Background music cued in a separate application, not audible in the recording, ready to mix in post

**Immediately before hitting record:**
```bash
clear && printf '\033[3J'
date && echo "--- Recording starts ---"
```
Then start screen capture. Then wait 3 seconds. Then begin Section 1.

---

## The Three Money Shot Moments

### Money Shot 1: The watch pane activates (Section 3.3, ~2:15–2:45)

The split-screen moment when output starts appearing in the right-side watch pane while the left side is still showing inference tokens is the visual that no other team in this space can show. Two panes. One side reasoning. One side writing. Local hardware. Do not cut away from this. Do not speed this portion. Let the viewer watch both things happen simultaneously.

**What needs to be visible:** Both panes in frame simultaneously. Left: reasoning tokens actively scrolling. Right: `watch` output updating as the first channel entry appears. The file growing in real time is the proof.

**What to resist:** The urge to narrate over it. One brief title card — "output appearing in real time" — is enough. Let the split screen carry the moment.

### Money Shot 2: The full cat of the finished output (Section 4.1–4.2, ~5:30–6:15)

After the inference completes, you open the research file and scroll through it at reading pace. This is the payoff. Three structured channel recommendations, each with audience analysis and a posting strategy. The quality of the output at this moment either proves the entity concept or undermines it. If the output is poor, do not publish this video — reschedule with a better model.

**What needs to be visible:** The full file content, scrolling at reading pace. Three channels, each section clearly formatted. The viewer should be able to read Channel 1 completely before you scroll to Channel 2.

**What to say:** Almost nothing. Let the document speak. At most: "Juno asked for three channels. Here they are." Then silence while the viewer reads.

### Money Shot 3: The git commit hash (Section 5.3, ~7:00–7:30)

`git log --oneline -3` showing the fresh commit hash, timestamp, and message is the final proof. The research is not a chat transcript. It is a versioned artifact with a cryptographic identity. Hold on this output for 3 full seconds. Do not cut before the hash is fully on screen.

**What needs to be visible:** The new commit in the log — hash, timestamp, and the full commit message referencing the task ID. Then `date` confirming the timestamp matches the session.

**What to say:** "Work on disk. Timestamped. Verifiable." Then stop.

---

## Fallback Plan If a Demo Command Fails

### If fourty4 is offline or SSH fails before recording
- Reschedule entirely. Do not improvise with a different machine.
- Check status: `ping -c1 fourty4` from thinker. If network is the issue, diagnose before attempting to record.
- There is no fallback for this one. The machine claim is non-negotiable.

### If ollama fails or returns garbage during the dry run
- Do not proceed to recording.
- Try a different model: `ssh fourty4 'ollama list'` — pick the most capable model available.
- Run the dry run again. If a second model also produces garbage output, reschedule and investigate.
- The research output (Section 4) is shown on camera. If it is not credible, the video's premise fails at the proof moment.

### If the inference run produces no output to `~/.sibyl/research/`
- This means Sibyl's invocation did not write the output file as expected.
- Check the invocation pattern before recording in the dry run. Confirm the output path is correct.
- Do not improvise a workaround on camera (e.g., manually writing a file). If the invocation doesn't produce the file, the system is not ready.

### If the watch pane shows nothing while inference runs (Section 3.3)
- The watch pane not updating means the output file is not being written incrementally.
- This is acceptable — keep recording, skip the split-screen narration, let the single pane carry the section.
- Do not explain the missing right pane on camera. Cut the watch pane section in post if it adds nothing.

### If the take runs past 12 minutes raw
- Over-narrating Section 3 (inference) is the most likely cause. Stop speaking over the inference stream. One brief title card is enough.
- If Section 4 (output review) is running long: reduce to one sentence per channel, not a full read-through. The viewer can pause. Don't race, but don't narrate every line either.
- Do not cut Section 5 (commit). It is the final proof and cannot be shortened.

---

## Pacing Guide

| Section | Pace | Why |
|---------|------|-----|
| Section 1 (date + identity) | Real-time — deliberate | Timestamp authenticity; do not rush |
| Section 2 (task filing) | Real-time — deliberate | Viewer must read the YAML brief as it writes |
| Section 3 (inference stream) | Speaking: minimal; editing: 2x | Let the tokens scroll; reserve VO for title cards only |
| Section 3.3 (watch pane activates) | Real-time — hold | Money shot; do not cut or speed here even briefly |
| Section 3.4 (first channel result) | Real-time — pause speedup | First result must be readable; hold at 1x for 5 seconds |
| Section 4 (output cat) | Real-time — reading pace | Viewer needs to read 3 channels; scroll at ~3 sec/channel |
| Section 5 (git commit) | Real-time — deliberate | Timestamp proof; every line matters |
| Section 5.3 (log + hash) | SLOWEST — hold 3 seconds | The hash is the proof; let it sit |
| Section 5.4 (date bookend) | Real-time | Clean bookend; don't rush the close |

The single pacing mistake this video is most likely to make: speeding through the output review (Section 4) after a long inference wait. The viewer has waited through the inference. Section 4 is the payoff. Scroll at reading pace. Let the research sit on screen.

---

## Production-Specific Warnings

**This video cannot be faked.** Every section contains a timestamp, a machine identifier, or a commit hash. Do not attempt to reconstruct any section with pre-written output or a different machine. If anything fails, the correct response is to stop and reschedule — not to work around it.

**Dry run is not optional.** The inference model must produce credible output before recording begins. Budget this time. A 15-minute dry run that reveals a model issue saves a wasted 60-minute recording session.

**Font size at 18pt minimum.** The inference stream will be sped to 2x in post. If the font is 14pt at 1x, it will be illegible at 2x playback. Test this: record 30 seconds of terminal output, speed it to 2x in your editing software, confirm it is readable. If it is not, increase font size and recheck before recording.

**The music cue is post-production only.** The lo-fi background music for the inference section is added in editing — not played during recording. Any ambient noise in the recording room will be audible in the sections that run at 1x without music. Quiet room applies to the full session.

**Screen recording on fourty4 is macOS.** QuickTime or OBS for macOS — both are valid. OBS gives more control over the final frame. Confirm screen capture is capturing the correct display (not mirrored or wrong monitor) before starting the session.
