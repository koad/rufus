---
title: "Shot List — The $200 Laptop Experiment"
video: 2026-04-07-200-dollar-laptop
production-owner: Rufus
hardware: thinker (mandatory)
tier: 3
capture: asciinema + ffmpeg
status: production-ready
---

# Shot List: "The $200 Laptop Experiment"

## Pre-Production Checklist

### Environment

- [ ] Record on thinker — the actual machine. No exceptions.
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text
- [ ] Font: JetBrains Mono (or Fira Code / Hack) at 16–18px — legible at 720p
- [ ] Shell prompt: minimal — `$ ` or host `$ ` only. No git decorations. No powerline.
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] Confirm `neofetch` or `inxi -F` installed and outputs clean on thinker
- [ ] Confirm `~/.juno` is current: `cd ~/.juno && git pull`
- [ ] Confirm SSH to fourty4 works: `ssh fourty4 echo ok`
- [ ] Confirm hook file exists and is readable: `ls ~/.juno/hooks/executed-without-arguments.sh`
- [ ] Confirm `git log --oneline --since="2026-03-30"` on `~/.juno` returns commits
- [ ] asciinema installed: `asciinema --version`
- [ ] ffmpeg installed: `ffmpeg -version`
- [ ] Scrollback buffer: 10,000+ lines — nothing disappears mid-take
- [ ] Mic check: quiet room, gain tested

### Recording Command

```bash
asciinema rec \
  --title "The \$200 Laptop Experiment — koad:io Day 7" \
  --idle-time-limit 2 \
  --env TERM,SHELL \
  ~/.rufus/recordings/2026-04-07-200-dollar-laptop-raw.cast
```

---

## Shot 1: Cold Open — Empty Terminal

**Segment:** SEGMENT 1 (0:00–0:10)
**Duration:** ~10 seconds

**Screen shows:**
- Terminal window, black background, cursor blinking
- Nothing else

**Type:** Nothing yet.

**Say:**
> "Seven days ago, koad:io's first operation started on this machine."

**Technical notes:**
- Hold 2–3 seconds of silence at the very start. Clean cut point for editing.
- Do not start speaking until cursor has been visible for at least 2 seconds.

---

## Shot 2: Specs Reveal — neofetch

**Segment:** SEGMENT 1 (0:10–1:00)
**Duration:** ~50 seconds

**Type:**
```bash
neofetch
```

**Expected output:** neofetch ASCII logo + system info block. Key lines to let viewer read:
- OS
- Host / Model
- CPU
- Memory
- Shell

**Say (as specs render):**
> "This is thinker. A refurbished laptop. You can see the specs."

*(pause on CPU and memory lines)*

> "Not a cloud VM. Not a workstation with a GPU. A commodity machine —
> the kind you buy used when you're not sure you need anything better."

*(pause)*

> "Today is Day 7. The experiment has a result."

**Technical notes:**
- Let neofetch fully render before speaking.
- Do NOT cut or speed up the neofetch output. The specs are the argument.
- If neofetch is not installed, use `inxi -F | head -20` as fallback.
- Retake trigger: neofetch errors or shows wrong machine (verify hostname).

---

## Shot 3: The Thesis Echo

**Segment:** SEGMENT 2 (1:00–1:20)
**Duration:** ~20 seconds

**Type:**
```bash
echo "The entity is the directory."
```

**Expected output:**
```
The entity is the directory.
```

**Say (after it prints):**
> "The entity is the directory. The model is just the reasoning engine
> that reads the directory. Sovereignty lives entirely in the files."

**Technical notes:**
- Type slowly. Let the line sit on screen before speaking.
- This is the thesis frame. One sentence. Let it breathe.

---

## Shot 4: ls ~/.juno/

**Segment:** SEGMENT 2 (1:20–1:55)
**Duration:** ~35 seconds

**Type:**
```bash
ls ~/.juno/
```

**Expected output:**
```
ALICE_PRODUCTION_PLAN.md  CONTEXT         GOVERNANCE.md  LOGS            OPERATIONS.md  PROJECTS   README.md   TEAM_STRUCTURE.md  archive  commands  documentation  features  home   hooks  id   keybase  lib  man  media  memories  proc  production  productions  res  scripts  ssl  trust  usr  var
```
*(exact layout depends on terminal width)*

**Say:**
> "That's Juno. An AI business orchestrator. CLAUDE.md is her identity.
> memories/ is her context. trust/ holds her authorization bonds.
> commands/ holds her skills. All of it: files on disk. A git repo."

**Technical notes:**
- Brief pause after `ls` output before speaking — let viewer scan the listing.
- Speak at a measured pace while the directory names are visible.

---

## Shot 5: Directory Size

**Segment:** SEGMENT 2 (1:55–2:15)
**Duration:** ~20 seconds

**Type:**
```bash
du -sh ~/.juno/
```

**Expected output:** Size figure (likely in the low megabytes range)

**Say:**
> "If sovereignty lives in the files, then any machine that can run git
> and SSH is sufficient. You don't need the cloud. You don't need
> expensive hardware."

*(pause)*

> "That was the bet. Seven days of production work to test it."

**Technical notes:**
- This line ends Segment 2. Clean pause before Segment 3 begins.
- If `du` runs slow, use `--apparent-size` flag — or skip and cut straight to next shot.

---

## Shot 6: Cat the Hook — Dispatch Chain Reveal

**Segment:** SEGMENT 3 (2:30–3:45)
**Duration:** ~75 seconds — this is the technical core

**Type:**
```bash
cat ~/.juno/hooks/executed-without-arguments.sh
```

**Expected output:** Full content of the hook file — the SSH dispatch logic, base64 encoding, FORCE_LOCAL handling.

**Say (narrating as the file scrolls):**

*As the file begins to render:*
> "This is thinker's job. The hook fires when you run an entity command."

*At the base64 encode line:*
> "Reads the prompt. Base64-encodes it."

*At the SSH invocation:*
> "SSHes to fourty4 — the Mac Mini. fourty4 starts a Claude Code session.
> The inference happens there."

*After the file finishes:*
> "That's thinker's contribution: run a shell script and establish an
> SSH connection. A Raspberry Pi could do thinker's job."

**Technical notes:**
- This is the most technically dense shot. Do not rush the scroll.
- If the hook file is long — let it scroll. Full file is the point.
- Narrate the key steps as they appear on screen, not before.
- Retake trigger: any moment where narration gets ahead of what's visible on screen.

---

## Shot 7: SSH to fourty4

**Segment:** SEGMENT 3 (3:45–4:10)
**Duration:** ~25 seconds

**Type:**
```bash
ssh fourty4 echo "fourty4 is up"
```

**Expected output:**
```
fourty4 is up
```

**Say (while waiting for the SSH response):**
> "fourty4 is always on. A Mac Mini. Roughly $400, one-time. It handles
> the Claude API calls. But that's not GPU inference — it's API calls
> over the network. A $50-a-month VPS does the same job."

**Say (after response appears):**
> "Total infrastructure: thinker, fourty4, flowbie — existing hardware.
> No cloud platform subscription. No SaaS fee. No vendor with admin
> access to your entities."

**Technical notes:**
- Accept natural SSH latency. Do not cut the wait.
- If SSH is slow: `--idle-time-limit 2` in asciinema will compress the gap to 2 seconds. Acceptable.
- If fourty4 is down: stop recording. Do not simulate this step. Reschedule.

---

## Shot 8: The Cost Line

**Segment:** SEGMENT 3 (4:10–4:30)
**Duration:** ~20 seconds

**Type:**
```bash
echo "thinker: \$200 one-time. fourty4: \$400 one-time. Cloud: \$0/month."
```

**Expected output:**
```
thinker: $200 one-time. fourty4: $400 one-time. Cloud: $0/month.
```

**Say:**
> "The expensive part isn't hardware. I'll show you what is."

**Technical notes:**
- Line sits on screen. Let the viewer read it. No rush.
- This closes Segment 3 and sets up the cost reframe in Segment 5.

---

## Shot 9: Git Log — Seven Days of Commits

**Segment:** SEGMENT 4 (4:30–5:30)
**Duration:** ~60 seconds — do not rush this shot

**Type:**
```bash
cd ~/.juno && git log --oneline --since="2026-03-30" --until="2026-04-06"
```

**Expected output:** 40–50 commit lines, one-line each, dated across 7 days.

**Say (before running):**
> "Here's what seven days on this machine produced. Not a slide. Commits."

**Say (narrating as the log scrolls — pick out key lines):**
> "Juno gestated and pushed to GitHub. Vulcan built Alice Phase 2A —
> it's live on kingofalldata.com right now."

*(as log continues)*
> "Faber wrote six posts. Sibyl synthesized a research paper. Chiron
> bootstrapped with a full curriculum spec."

*(as log continues)*
> "Trust bonds signed, GPG-verified. Fifteen entities migrated.
> Hook architecture fixed and signed. GitHub Sponsors live."

**Technical notes:**
- This is the emotional core of the video. Do not cut. Do not speed up.
- Let all commits scroll. The volume is the point.
- If log is very long, `--idle-time-limit 2` handles any pause. Do not pipe to `head`.
- Speak at a pace that lets the viewer absorb the commit messages, not just hear the VO.

---

## Shot 10: Commit Count

**Segment:** SEGMENT 4 (5:30–5:50)
**Duration:** ~20 seconds

**Type:**
```bash
git log --oneline --since="2026-03-30" --until="2026-04-06" | wc -l
```

**Expected output:** A number (40–60 expected).

**Say:**
> "These are commits. Auditable. Check the git log yourself —
> it's public at github.com/koad/juno."

*(pause)*

> "One human. A $200 laptop. A Mac Mini. A team of entities
> with directories on disk."

**Technical notes:**
- Brief pause after the count appears. Let the viewer do the math.
- Do not editorialize the number — just let it sit.

---

## Shot 11: Juno's Identity Memory

**Segment:** SEGMENT 5 (6:30–7:00)
**Duration:** ~30 seconds

**Type:**
```bash
cat ~/.juno/memories/001-identity.md | head -20
```

**Expected output:** First 20 lines of Juno's identity memory file.

**Say:**
> "Juno knows who she is at the start of Day 7 the same way she did on
> Day 1. Same CLAUDE.md. Same memories committed to git. Same trust bonds."

*(pause)*

> "There's no session state to expire. No persistent process to crash.
> No database to corrupt."

**Technical notes:**
- Read at the pace the lines appear. Don't get ahead.
- If the file has changed since Day 1 (it has, with new memories), that's fine — the point is that it's committed and stable, not that it's frozen.

---

## Shot 12: The Thesis Return

**Segment:** SEGMENT 5 (7:00–7:15)
**Duration:** ~15 seconds

**Type:**
```bash
echo "The entity's state is files on disk."
```

**Expected output:**
```
The entity's state is files on disk.
```

**Say:**
> "Files on disk don't age."

**Technical notes:**
- Slowest moment in the video. One sentence. Full pause before next shot.
- Editor: hold on this line for 3–4 seconds before cutting to Shot 13.

---

## Shot 13: The Final Command

**Segment:** SEGMENT 5 (7:15–7:30)
**Duration:** ~15 seconds

**Type:**
```bash
git clone https://github.com/koad/juno
```

**Do NOT wait for the clone to complete. Stop recording at the first line of clone output.**

**Say (as clone begins):**
> "thinker could fail today. The data survives — committed and pushed.
> New machine. Git clone. SSH key. The operation continues."

*(brief pause — over the first clone output line)*

> "After git clone."

**[STOP RECORDING / FADE as clone output starts scrolling]**

**Technical notes:**
- The visual of the clone beginning is the close. We don't need to see it finish.
- asciinema: stop recording (Ctrl+D) as the clone begins to show transfer progress.
- If clone fails to start (network issue): retake. The clone starting is the final image.

---

## Shot 14: Fade / Cut to Black

**Duration:** 2–3 seconds

- No music
- No animation
- Simple cut to black or 1-second fade
- Hold on last terminal frame (clone starting) for 1 extra second before fade — editor's call

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 2 (neofetch) | Do NOT cut the render. Full output must show. |
| Shot 6 (hook cat) | Do NOT rush. Technical core. Full scroll. |
| Shot 7 (SSH) | Accept latency. `--idle-time-limit 2` compresses it. |
| Shot 9 (git log) | Do NOT cut. Do NOT speed up. Emotional core. |
| Shot 12 (echo) | Hold 3–4 seconds on this line before cutting. |
| Shot 13 (clone) | Stop at first clone output line. Fade. |
| Shot 5 close | 2-second pause before Segment 3. Clean breathing room. |

**Cuts to remove:**
- Any backspace or visible typo correction (retake if > 1 backspace)
- Any unintentional pause > 8 seconds (outside Shots 9, 12)
- Any window or focus switch

**No:**
- No zoom effects
- No lower-thirds or captions overlay (separate captions track via Whisper)
- No background music
- No speed ramp — no segment should run faster than recorded
- No transitions except cut-to-black at end

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| neofetch not installed | Use `inxi -F \| head -20` or `uname -a && free -h && lscpu \| head -10` |
| fourty4 SSH fails | Stop recording. Do not simulate. Reschedule when fourty4 is up. |
| Hook file missing or moved | Stop recording. Locate file first: `find ~/.juno -name "*.sh" -path "*/hooks/*"` |
| git log shows fewer commits than expected | Acceptable — run it. Don't inflate. |
| git clone fails to start | Retake Shot 13. Check network first. |
| asciinema cast is corrupted | Re-record. Confirm asciinema works before starting. |
| Take runs past 10 minutes | Trim Shot 10 (commit count VO) and compress Shot 8 (cost echo). Do not trim git log. |

---

## Final Deliverables from This Session

- [ ] Raw cast: `~/.rufus/recordings/2026-04-07-200-dollar-laptop-raw.cast`
- [ ] Edited cast (trimmed dead air only): `~/.rufus/recordings/2026-04-07-200-dollar-laptop-edit.cast`
- [ ] MP4 export (YouTube): `~/.rufus/recordings/2026-04-07-200-dollar-laptop-final.mp4`
- [ ] Clip (60s, Twitter/X): `~/.rufus/recordings/2026-04-07-200-dollar-laptop-clip.mp4`
- [ ] Thumbnail: `~/.rufus/recordings/2026-04-07-200-dollar-laptop-thumb.png`
- [ ] Captions: auto via Whisper, reviewed and corrected
- [ ] Hand-off to Mercury: title, description, tags applied (see script.md)
