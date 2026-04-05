---
title: "Recording Day Master Checklist"
owner: Rufus
created: 2026-04-05
purpose: "Open this before hitting record. Every time."
---

# Recording Day Master Checklist

Open this document. Work top to bottom. Do not skip sections.

---

## Part 1: Universal Setup (Every Video, Every Time)

Complete this before touching any video-specific pre-flight. Takes 10 minutes.

### Hardware

- [ ] Confirm the recording machine. Check `hostname` — does it match what this video requires?
  - Video 1 (Clone Walkthrough): thinker
  - Video 2 ($200 Laptop): thinker — non-negotiable, the claim depends on it
  - Video 3 (Sibyl Research): fourty4 — non-negotiable, local inference is the premise
  - Video 4 (Show HN): thinker (preferred)
  - Video 5 (Skeptics): thinker
- [ ] If machine is wrong: stop. Do not compensate. Reschedule.

### Terminal Setup

- [ ] Terminal fullscreen, black background `#000000`, white text — no themes, no powerline glyphs
- [ ] Font: JetBrains Mono or Fira Code at 16–18px. Test legibility at 720p before recording.
  - For Sibyl video (Video 3): 18pt minimum — inference output will be sped 2x in post
- [ ] Strip prompt to bare minimum: `export PS1='$ '` or `export PS1='thinker $ '`
  - No git branch display. No color escapes. The HN audience will notice powerline glyphs.
- [ ] Scrollback buffer set to 10,000+ lines (nothing disappears mid-take)
- [ ] Stage your commands in a notes file — do not type long commands from memory during a take
- [ ] Run the scrollback clear and confirm it works:
  ```bash
  clear && printf '\033[3J'
  ```
  This clears both the visible buffer and the scrollback. Use this exact command before every take, not just `clear`.

### Screen Recording Software

- [ ] Identify which tool this video uses (per video notes below):
  - asciinema: `asciinema --version` — confirm installed
  - OBS: armed at 1920x1080, 60fps, black background capture
- [ ] For OBS: confirm it is capturing the correct display (not mirrored or wrong monitor)
- [ ] For fourty4 (macOS): OBS or QuickTime — confirm it is capturing the correct screen
- [ ] Have the full recording command staged in clipboard, not typed from scratch
- [ ] `mkdir -p ~/.rufus/recordings` — confirm recordings directory exists

### Audio

- [ ] Quiet room confirmed — fans off, phone silenced, no scheduled notifications
- [ ] All notifications disabled: Do Not Disturb on, Slack/Discord closed, no cron output expected
- [ ] Mic gain tested with a spoken test sentence before starting
- [ ] Note: music is post-production only (Sibyl video). Nothing audible during recording.

### Network and Git State

- [ ] `ping -c1 github.com` — GitHub reachable
- [ ] Pull every entity directory this video touches before recording:
  ```bash
  cd ~/.juno && git pull
  ```
  (and any other entity dir per video pre-flight below)
- [ ] `git status` in each pulled directory — working tree must be clean
  - If there are uncommitted changes: commit or stash them before recording. Do not have a dirty working tree visible in the recording terminal.

---

## Part 2: Per-Video Pre-Flight

Go to the section for the video you are recording. Confirm every checkbox before hitting record.

---

### VIDEO 1 — "I Cloned a koad:io Entity" (Day 5, thinker)

**Production directory:** `~/.rufus/productions/2026-04-05-clone-walkthrough/`
**Recording tool:** OBS preferred; asciinema fallback
**Runtime target:** 5–8 minutes

- [ ] Machine is thinker: `hostname` returns thinker
- [ ] `chiron` command responds — test in a SEPARATE terminal (not the recording terminal):
  ```bash
  PROMPT='test' chiron
  ```
  Confirm it responds in character, not generically. If response is generic, check `~/.chiron/memories/` — do not proceed until identity is grounded.
- [ ] `~/.chiron-demo` does NOT exist:
  ```bash
  ls ~/.chiron-demo 2>&1
  ```
  Must return "No such file or directory." If it exists: `rm -rf ~/.chiron-demo`
- [ ] GitHub reachable (git clone requires it): `ping -c1 github.com`
- [ ] OBS or screen recorder armed at 1920x1080
- [ ] Know the 5 shots in order. Full script at `productions/2026-04-05-clone-walkthrough/script.md`.

**Final check — run this, then immediately start recording:**
```bash
clear && printf '\033[3J' && ls ~/.chiron-demo 2>&1
```
Output must end with "No such file or directory." If it does: hit record.

---

### VIDEO 2 — "The $200 Laptop Experiment" (Day 7, thinker)

**Production directory:** `~/.rufus/productions/2026-04-07-200-dollar-laptop/`
**Recording tool:** asciinema (command is in script — stage it in clipboard, do not retype)
**Runtime target:** 7–8 minutes

- [ ] Machine is thinker: `hostname` returns thinker. If wrong machine: stop, reschedule.
- [ ] `neofetch` installed and shows thinker's actual specs:
  ```bash
  neofetch
  ```
  Verify hostname matches. If neofetch not installed, fallback: `uname -a && free -h && lscpu | head -10`
- [ ] `~/.juno` is current and clean:
  ```bash
  cd ~/.juno && git pull && git status
  ```
- [ ] SSH to fourty4 is working — this step appears on camera, cannot be faked:
  ```bash
  ssh fourty4 echo ok
  ```
  Must return `ok`. If it times out or fails: stop, reschedule. There is no workaround.
- [ ] Hook file is in place:
  ```bash
  ls ~/.juno/hooks/executed-without-arguments.sh
  ```
- [ ] Run the git log and note the commit count BEFORE recording — you will say this number on camera:
  ```bash
  git log --oneline --since="2026-03-30" --until="2026-04-06" ~/.juno | wc -l
  ```
  Write the number down. Do not guess it mid-take.
- [ ] `~/.juno/memories/001-identity.md` exists: `ls ~/.juno/memories/001-identity.md`
- [ ] asciinema record command staged in clipboard (includes dollar sign escape — do not retype from memory)

**Final check — run this, then immediately start asciinema:**
```bash
clear && printf '\033[3J'
```
Wait 3 seconds of silence after starting. Then speak.

---

### VIDEO 3 — "Live Session: Sibyl Does Research" (Day 7, fourty4)

**Production directory:** `~/.rufus/productions/2026-04-07-sibyl-research/`
**Recording tool:** OBS (macOS) or QuickTime on fourty4
**Runtime target:** 6–8 minutes (edited from ~15 min raw)
**Budget 30 minutes for setup and dry run before recording begins.**

- [ ] SSH to fourty4 from thinker is working:
  ```bash
  ssh fourty4 echo ok
  ```
  Must return `ok`. If not: reschedule entirely. No fallback machine.
- [ ] ollama running with correct model on fourty4:
  ```bash
  ssh fourty4 'ollama list && ollama ps'
  ```
  Confirm the intended model is present and responding.
- [ ] `~/.sibyl` on fourty4 is current and clean:
  ```bash
  ssh fourty4 'cd ~/.sibyl && git pull && git status'
  ```
  Must show "nothing to commit, working tree clean."
- [ ] `~/.sibyl/tasks/incoming/` exists on fourty4:
  ```bash
  ssh fourty4 'ls ~/.sibyl/tasks/incoming/'
  ```
- [ ] `~/.sibyl/research/` exists on fourty4:
  ```bash
  ssh fourty4 'ls ~/.sibyl/research/'
  ```
- [ ] Target output file does NOT yet exist:
  ```bash
  ssh fourty4 'ls ~/.sibyl/research/2026-04-07-channel-analysis.md 2>&1'
  ```
  Must show "No such file."
- [ ] DRY RUN COMPLETE — run the ollama invocation once off-camera and confirm it produces structured output. If it returns garbage: try a different model, run again. Do not proceed to recording until dry run passes.
- [ ] Terminal on fourty4 configured: tmux or iTerm two-pane split (70% left: Sibyl session / 30% right: watch pane)
- [ ] Right pane pre-loaded with:
  ```bash
  watch -n2 cat ~/.sibyl/research/2026-04-07-channel-analysis.md
  ```
- [ ] Font size on fourty4 confirmed at 18pt+ — test: record 30 seconds of terminal output, speed to 2x in editing software, confirm still legible. If not legible at 2x: increase font and recheck.
- [ ] Screen recording on fourty4 armed and capturing the correct display

**Final check — run in the recording terminal on fourty4, then start screen capture:**
```bash
clear && printf '\033[3J'
date && echo "--- Recording starts ---"
```
Wait 3 seconds. Then begin Section 1.

---

### VIDEO 4 — "Show HN: Agent Home Directory" (Day 10, thinker)

**Production directory:** `~/.rufus/productions/2026-04-10-show-hn-agent-home-directory/`
**Recording tool:** asciinema or OBS
**Runtime target:** 4–6 minutes
**Audience:** HackerNews. They read code. Any typo, any `^C`, any notification will be commented on.

- [ ] Machine is thinker (preferred): `hostname`
- [ ] `~/.juno` is current:
  ```bash
  cd ~/.juno && git pull && git status
  ```
- [ ] Run the git log and note the exact commit count — say this exact number on camera, do not guess:
  ```bash
  git -C ~/.juno log --author="Juno" --oneline | wc -l
  ```
  Write it down.
- [ ] GPG key for Juno is imported:
  ```bash
  gpg --list-keys juno@kingofalldata.com
  ```
  If not found: import it now, before recording.
- [ ] GPG verify passes — run this in a SEPARATE terminal and confirm before recording:
  ```bash
  gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc
  ```
  Must return "Good signature from Juno." If it returns anything else: stop. Do not proceed. Diagnose and fix before recording.
- [ ] Trust bond file exists and is readable:
  ```bash
  cat ~/.juno/trust/bonds/juno-to-sibyl.md
  ```
- [ ] `~/.juno/memories/001-identity.md` exists: `ls ~/.juno/memories/001-identity.md`
- [ ] All notifications disabled. No browser. No other windows. Nothing that can steal focus.
- [ ] Stage these four commands in a notes file (clipboard rotation) — do not type from memory:
  1. `cat ~/.juno/memories/001-identity.md`
  2. `gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc`
  3. `cat ~/.juno/trust/bonds/juno-to-sibyl.md`
  4. `git -C ~/.juno log --author="Juno" --oneline`
- [ ] No music planned. No end card. This video ends on fade to black — silence is intentional.

**Final check — run this, then immediately start recording:**
```bash
clear && printf '\033[3J'
```
Wait 3 seconds of silence. First spoken line: "Three commands. That's all I'm going to run."

---

### VIDEO 5 — "The Week 1 Skeptics Were Right" (Day 12, thinker)

**Production directory:** `~/.rufus/productions/2026-04-12-week1-skeptics/`
**Recording tool:** OBS preferred (browser shot in Shot 5 requires screen capture)
**Runtime target:** 7–9 minutes

- [ ] Machine is thinker: `hostname`
- [ ] `~/.juno` is current:
  ```bash
  cd ~/.juno && git pull && git status
  ```
- [ ] GitHub CLI authenticated:
  ```bash
  gh auth status
  ```
- [ ] Pull the live issue list and note the blocked issue numbers BEFORE recording — you will reference specific issue numbers on camera:
  ```bash
  gh issue list --state open --repo koad/juno --assignee koad --limit 20
  ```
  Write down the blocked issue numbers (e.g., fourty4 API auth #44). Do not discover these live mid-take.
- [ ] Git log returns commits:
  ```bash
  git log --author="Juno" --oneline ~/.juno | head -5
  ```
- [ ] GPG verify passes:
  ```bash
  gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc
  ```
  Must return "Good signature." If not: stop, fix, recheck.
- [ ] GitHub Sponsors page is live — confirm in browser before recording: `https://github.com/sponsors/koad`
  Note current sponsor count. You will show this on camera.
- [ ] Faber's Day 12 blog post status confirmed. Video can precede the post, but Mercury holds distribution until post is ready. Coordinate before recording if possible.
- [ ] OBS armed at 1920x1080 — browser shot in Shot 5 requires full screen capture, not terminal-only

**Final check — run this, then immediately start recording:**
```bash
clear && printf '\033[3J'
```
Wait 3 seconds. Opening line: "I'm going to tell you four things the Week 1 skeptics got right."

---

## Part 3: If Something Goes Wrong

### Demo command fails mid-take
Stop recording. Say nothing on camera about the failure. Do not try to fix it on camera.
- Diagnose in a SEPARATE terminal.
- Once fixed and confirmed working, restart from Shot 1 with `clear && printf '\033[3J'`.
- You are restarting a shot, not the whole video. The raw file can have multiple attempts — the editor finds the clean take.

### Inference gives garbage output (Video 3)
Stop. Do not proceed. In a separate terminal: `ssh fourty4 'ollama list'` — try a different model. Run the dry run again. If a second model also fails: reschedule. Do not publish any video where the Sibyl output is not credible.

### Wrong machine
Hard stop. Do not compensate. Do not rename anything. Do not record and call it the right machine. The machine identity is part of the claim. Reschedule to the correct machine.

### Typo needing more than one backspace
Stop the take. `clear && printf '\033[3J'`, restart from Shot 1. The HN audience reads every keystroke.

### A notification or focus event appears on screen
Stop immediately. This applies especially to Video 4 (Show HN). Disable all notifications. Restart from Shot 1.

### You flub a sentence during VO
Pause for 3 full seconds. Restate from the beginning of the prior sentence. Do not keep talking through the flub. The pause gives the editor a clean cut point. Continue recording — do not stop the whole take for a voice stumble.

### SSH to fourty4 fails during a live shot (Videos 2 and 3)
Stop recording. This step cannot be faked, edited around, or skipped. Diagnose: `ping -c1 fourty4` from a separate terminal. If fourty4 is down: reschedule the whole session. The machine's availability is part of the claim.

### The take runs over target runtime
Do not panic-cut money shots. Trim VO instead:
- Cut commentary, not footage
- The git log scroll is never cut, never sped — every video
- The inference stream (Video 3): narrate less, not faster
- The close shots always run at full pace — that is where the argument lands

---

## Part 4: Post-Recording

### Immediately after recording
- [ ] Note the raw filename: `~/.rufus/recordings/YYYY-MM-DD-<slug>-raw.cast` or `-raw.mp4`
- [ ] Play back the first 30 seconds to confirm the recording actually captured. Do not skip this.
- [ ] Note any take issues: timestamps of flubs, retry points, shots to discard

### Export pipeline
Follow Section 5 of `PRODUCTION-SCHEDULE.md` for the full export pipeline:
1. Review raw file (asciinema play or OBS playback)
2. Trim dead air start/end only
3. Export to MP4 via agg + ffmpeg (or asciinema → agg → ffmpeg)
4. Export 60-second Twitter/X clip at 1280x720
5. Extract thumbnail frame
6. Generate captions with Whisper; review entity names and technical terms

### Notify Mercury
When final.mp4, clip.mp4, thumb.png, and captions.srt are ready:
```bash
ssh juno@dotsh 'keybase chat send koad "Mercury: [VIDEO TITLE] is ready for distribution. Files at ~/.rufus/recordings/YYYY-MM-DD-<slug>-. Metadata in productions/YYYY-MM-DD-<slug>/script.md."'
```
Or file a GitHub issue on koad/mercury with the handoff details and file paths.

Mercury needs: `final.mp4`, `clip.mp4`, `thumb.png`, `captions.srt` (reviewed), and YouTube title/description/tags from `script.md`.
Upload as unlisted first. Mercury reviews before publish.

### Log completion
Add a line to `~/.rufus/PRODUCTION-SCHEDULE.md` under the Quick Reference table changing the video's Recording status from "Not done" to "Done — raw at `~/.rufus/recordings/<filename>`".

Then commit the update:
```bash
cd ~/.rufus && git add PRODUCTION-SCHEDULE.md && git commit -m "log: [VIDEO TITLE] recording complete"
```

---

*Last updated: 2026-04-05 by Rufus*
