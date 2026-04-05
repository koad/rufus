---
title: "Master Production Schedule"
owner: Rufus
created: 2026-04-05
last-updated: 2026-04-05
purpose: "What koad opens when he says 'I have 2 hours, what do I record?'"
source-calendars:
  - ~/.faber/content-calendar/REALITY-2026-04-03.md
  - ~/.faber/content-calendar/REALITY-WEEK2-2026-04-08.md
---

# Master Production Schedule

**How to use this document:** Find how much time you have. Go to the matching section. Read the prerequisites. Record. Hand off to Mercury.

---

## Recording Setup Checklist

Complete this before any recording session. Takes ~10 minutes.

### Terminal environment
- [ ] Terminal emulator fullscreen, black background (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px (legible at 720p after export)
- [ ] Shell prompt stripped to minimal: `$ ` or `host $ ` only — no git branch display
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer set to 10,000+ lines (nothing disappears mid-take)

### Software
- [ ] asciinema installed: `asciinema --version`
- [ ] ffmpeg installed: `ffmpeg -version`
- [ ] OBS (if using studio mode): armed at 1920x1080, 60fps, black background capture

### Audio
- [ ] Quiet room — no fans, no notifications
- [ ] Mic gain tested with a test sentence before recording

### Network
- [ ] GitHub reachable: `ping -c1 github.com`
- [ ] SSH to fourty4 confirmed: `ssh fourty4 echo ok` (required for Sibyl video)

### Recordings directory
- [ ] `~/.rufus/recordings/` exists: `mkdir -p ~/.rufus/recordings`

---

## Section 1: Ready to Record

These videos have a complete script and shot list. Nothing to write — just record.

---

### VIDEO 1 — "I Cloned a koad:io Entity"

**Production directory:** `~/.rufus/productions/2026-04-05-clone-walkthrough/`
**Calendar day:** Day 5 (Saturday, April 5)
**Pillar:** Reality
**Type:** Terminal screencast, voice-over live
**Estimated session time:** 30–45 minutes total (15 min pre-check, 15 min recording, 5 min review)
**Runtime target:** 5–8 minutes

**Prerequisites (must confirm before hitting record):**
- [ ] `~/.chiron` exists and is current: `cd ~/.chiron && git pull`
- [ ] `chiron` command is on PATH: `PROMPT='test' chiron` — confirm it responds
- [ ] `~/.chiron-demo` does NOT exist: `ls ~/.chiron-demo 2>&1` — must show "No such file"
- [ ] OBS or screen recorder armed at 1920x1080
- [ ] Network up (git clone requires GitHub access)

**Recording command:**
```bash
# OBS preferred for this one (voice-over live during recording)
# fallback: asciinema rec --title "I Cloned a koad:io Entity" --idle-time-limit 2 --env TERM,SHELL ~/.rufus/recordings/2026-04-05-clone-walkthrough-raw.cast
```

**What you record (5 shots, in order):**
1. Empty terminal → `git clone https://github.com/koad/chiron ~/.chiron-demo`
2. `cd ~/.chiron-demo && ls` — show the directory
3. `cat README.md` → `cat CLAUDE.md` — the entity brief
4. `cat hooks/executed-without-arguments.sh` — the hook
5. `PROMPT='what is your role?' chiron` → wait for response → `pwd` → close

**Retake triggers:** Any typo needing more than one backspace. Any git error. Chiron gives a generic response not grounded in its memory files.

**Post-production (see Section 5):**
- Trim dead air start/end only — no cuts inside the entity response (Shot 5)
- Extract thumbnail: frame when Chiron's response appears on screen
- Export: `2026-04-05-clone-final.mp4` + `2026-04-05-clone-clip.mp4` (60s, Twitter/X)
- YouTube metadata: in `script.md` — title, description, tags, thumbnail concept

**Full script:** `~/.rufus/productions/2026-04-05-clone-walkthrough/script.md`
**Full shot list:** `~/.rufus/productions/2026-04-05-clone-walkthrough/shot-list.md`

---

### VIDEO 2 — "The $200 Laptop Experiment"

**Production directory:** `~/.rufus/productions/2026-04-07-200-dollar-laptop/`
**Calendar day:** Day 7 (Monday, April 7)
**Pillar:** Reality
**Type:** asciinema terminal capture, voice-over live (Tier 3 — no camera required)
**Estimated session time:** 45–60 minutes total (20 min pre-check, 25 min recording, 15 min review)
**Runtime target:** 7–8 minutes
**Machine:** thinker — non-negotiable, the whole point is that thinker ran the operation

**Prerequisites (must confirm before hitting record):**
- [ ] Recording on thinker — no exceptions
- [ ] `neofetch` installed and shows correct machine: `neofetch` — verify hostname = thinker
- [ ] `~/.juno` is current: `cd ~/.juno && git pull`
- [ ] SSH to fourty4 working: `ssh fourty4 echo ok` — if fourty4 is down, reschedule
- [ ] Hook file readable: `ls ~/.juno/hooks/executed-without-arguments.sh`
- [ ] `git log --oneline --since="2026-03-30" ~/.juno` returns commits
- [ ] `~/.juno/memories/001-identity.md` exists

**Recording command:**
```bash
asciinema rec \
  --title "The \$200 Laptop Experiment — koad:io Day 7" \
  --idle-time-limit 2 \
  --env TERM,SHELL \
  ~/.rufus/recordings/2026-04-07-200-dollar-laptop-raw.cast
```

**What you record (13 shots, in order):**
1. Empty terminal → `neofetch` (let specs render fully — specs are the argument)
2. `echo "The entity is the directory."`
3. `ls ~/.juno/` → `du -sh ~/.juno/`
4. `cat ~/.juno/hooks/executed-without-arguments.sh` (full scroll, technical core)
5. `ssh fourty4 echo "fourty4 is up"` (accept latency — do not simulate if down)
6. `echo "thinker: \$200 one-time. fourty4: \$400 one-time. Cloud: \$0/month."`
7. `cd ~/.juno && git log --oneline --since="2026-03-30" --until="2026-04-06"` (emotional core — do not cut)
8. `git log --oneline --since="2026-03-30" --until="2026-04-06" | wc -l`
9. `cat ~/.juno/memories/001-identity.md | head -20`
10. `echo "The entity's state is files on disk."` (hold 3–4 seconds)
11. `git clone https://github.com/koad/juno` — stop recording at first clone output line

**Retake triggers:** Any SSH failure. Any typo needing multiple backspaces. neofetch shows wrong machine.

**Critical:** If fourty4 is down, **stop and reschedule** — do not fake the SSH step.

**Post-production (see Section 5):**
- Speed up inference wait sections with `--idle-time-limit 2` (already set in record command)
- Do NOT cut or speed-ramp the git log scroll — it is the emotional core
- Export thumbnail: frame when git log fills the screen
- Export: `2026-04-07-200-dollar-laptop-final.mp4` + Twitter/X 60s clip starting at dispatch chain reveal

**Full script:** `~/.rufus/productions/2026-04-07-200-dollar-laptop/script.md`
**Full shot list:** `~/.rufus/productions/2026-04-07-200-dollar-laptop/shot-list.md`

---

### VIDEO 3 — "Live Session: Sibyl Does Research"

**Production directory:** `~/.rufus/productions/2026-04-07-sibyl-research/`
**Calendar day:** Day 7 (Monday, April 7) — same day as $200 Laptop, different machine
**Pillar:** Reality
**Type:** Live session recording on fourty4 — no voice-over, title cards only
**Estimated session time:** 60–90 minutes total (30 min setup + dry run, 20 min recording, 30 min review)
**Runtime target:** 6–8 minutes (edited from ~15 min raw with 2x–3x speed on inference sections)
**Machine:** fourty4 (Mac Mini) — local ollama inference; this is non-negotiable

**Prerequisites (must confirm before hitting record on fourty4):**
- [ ] fourty4 online and SSH accessible from thinker: `ssh fourty4 'echo ok'`
- [ ] ollama running with correct model: `ssh fourty4 'ollama list && ollama ps'`
- [ ] `~/.sibyl` on fourty4 is current: `ssh fourty4 'cd ~/.sibyl && git pull'`
- [ ] `~/.sibyl/tasks/incoming/` directory exists on fourty4
- [ ] `~/.sibyl/research/` directory exists on fourty4
- [ ] `~/.sibyl` is a clean git repo on fourty4: `ssh fourty4 'cd ~/.sibyl && git status'`
- [ ] Terminal on fourty4: tmux two-pane split (70% left: Sibyl session / 30% right: watch pane)
- [ ] Font size on fourty4: 18pt+ (must be legible after 2x speedup in post)
- [ ] Screen recording on fourty4 armed: OBS (macOS) or QuickTime at 1920x1080
- [ ] Dry run complete: confirm ollama responds to a test prompt before recording begins

**Research task to file (file this to Sibyl's inbox before recording):**
```
Top 3 distribution channels for a privacy-first AI infrastructure project
targeting self-hosted developers in 2026. For each: name, audience quality
signal, ideal content format, one concrete posting strategy.
```

**What you record (5 sections, in order):**
1. `date` + `cat ~/.sibyl/memories/001-identity.md | head -20` + `ls ~/.sibyl/tasks/incoming/` (Section 1 — identity anchor, real-time)
2. File the task via heredoc to `~/.sibyl/tasks/incoming/` (Section 2 — coordination handoff, real-time)
3. Sibyl runs inference — ollama reasoning visible (Section 3 — speed up to 2x/3x in post except first output lines)
4. Review the output in `~/.sibyl/research/` (Section 4 — proof moment, real-time)
5. `cd ~/.sibyl && git add . && git commit -m "research: ..."` (Section 5 — timestamp proof, real-time)

**Edit speeds per section:**

| Section | Speed | Reason |
|---------|-------|--------|
| 1 — Date + identity | 1x | Authenticity anchor |
| 2 — Task filing | 1x | Coordination handoff must be readable |
| 3 — Inference | 2x (reasoning: 3x) | Keep viewer engaged |
| 3 first output lines | 1x | Let first result land |
| 4 — Output review | 1x | Proof moment |
| 5 — Git commit | 1x | Timestamp proof — non-negotiable |

**Post-production (see Section 5):**
- Background music for Section 3 only (lo-fi, low volume)
- Title cards at section transitions (text per shot-list.md)
- Thumbnail: `git log --oneline` output frame (Section 5)
- Export: `2026-04-07-sibyl-research-final.mp4` + 1-min Twitter/X clip

**Full shot list / script:** `~/.rufus/productions/2026-04-07-sibyl-research/shot-list.md`
**Full record:** `~/.rufus/productions/2026-04-07-sibyl-research/record.md`

---

### VIDEO 4 — "Show HN: Agent Home Directory"

**Production directory:** `~/.rufus/productions/2026-04-10-show-hn-agent-home-directory/`
**Calendar day:** Day 10 (Thursday, April 10)
**Pillar:** Reality
**Series:** Week 2 Reality Pillar
**Type:** Terminal screencast, voice-over live (Tier 3 — no camera required)
**Estimated session time:** 40–55 minutes total (15 min pre-check, 20 min recording, 10 min review)
**Runtime target:** 4–6 minutes
**Machine:** thinker (primary)

**Prerequisites (must confirm before hitting record):**
- [ ] `~/.juno` is current: `cd ~/.juno && git pull`
- [ ] `git log --author="Juno" --oneline` returns 6+ days of commits (verify count before recording)
- [ ] `~/.juno/trust/bonds/juno-to-sibyl.md.asc` exists and is verifiable
- [ ] GPG key for Juno imported locally: `gpg --list-keys juno@kingofalldata.com`
- [ ] `gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc` returns "Good signature"
- [ ] `~/.juno/memories/001-identity.md` exists and is current
- [ ] Terminal configured: black bg (#000000), white text, 16px+ monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS or asciinema)
- [ ] Quiet environment for voice-over

**Recording command:**
```bash
asciinema rec \
  --title "Show HN: Agent Home Directory — Three Commands, Then git log" \
  --idle-time-limit 2 \
  --env TERM,SHELL \
  ~/.rufus/recordings/2026-04-10-show-hn-raw.cast
# OBS alternative: arm at 1920x1080, 60fps, black background capture
```

**What you record (7 shots, in order):**
1. Empty terminal → voice-over opening: "Three commands. That's all I'm going to run."
2. `cat ~/.juno/memories/001-identity.md` — let it scroll fully, do not cut short
3. `gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc` → "Good signature" is the money shot; then `cat ~/.juno/trust/bonds/juno-to-sibyl.md`
4. `git -C ~/.juno log --author="Juno" --oneline` — DO NOT CUT, DO NOT SPEED RAMP — full scroll is the emotional core; then `| wc -l` as punctuation beat
5. `git -C ~/.juno remote -v` — brief bridge: "Remote is GitHub. But the entity lives here."
6. `git clone https://github.com/koad/juno` → `cat juno/memories/001-identity.md` — call to action close
7. Fade to black — no music, no end card

**Retake triggers:** Any typo needing more than one backspace. `gpg --verify` returns anything other than "Good signature from...". `git log` returns zero commits or wrong author. Any window/focus switch during recording.

**Post-production (see Section 5):**
- DO NOT cut or speed-ramp Shot 4 (git log scroll) — this is the emotional core
- Trim dead air at start/end only
- Extract thumbnail: frame when git log fills the screen (Shot 4)
- Export: `2026-04-10-show-hn-final.mp4` + Twitter/X 60s clip starting at git log scroll
- YouTube metadata: in `script.md` — title, description, tags
- Mercury distribution: YouTube + Twitter/X 60s clip + HackerNews comment thread + Dev.to embed

**Full script:** `~/.rufus/productions/2026-04-10-show-hn-agent-home-directory/script.md`
**Full shot list:** `~/.rufus/productions/2026-04-10-show-hn-agent-home-directory/shot-list.md`
**Full record:** `~/.rufus/productions/2026-04-10-show-hn-agent-home-directory/record.md`

---

### VIDEO 5 — "The Week 1 Skeptics Were Right"

**Production directory:** `~/.rufus/productions/2026-04-12-week1-skeptics/`
**Calendar day:** Day 12 (Saturday, April 12)
**Pillar:** Reality
**Series:** Week 2 Reality Pillar
**Type:** Terminal screencast + browser, voice-over live (Tier 3 — no camera required)
**Estimated session time:** 60–80 minutes total (20 min pre-check, 30 min recording, 20 min review)
**Runtime target:** 7–9 minutes
**Machine:** thinker (primary)

**Prerequisites (must confirm before hitting record):**
- [ ] `~/.juno` is current: `cd ~/.juno && git pull`
- [ ] `gh auth status` — confirm GitHub CLI is authenticated
- [ ] `gh issue list --state open --repo koad/juno` returns real issue list — note which are blocked on koad
- [ ] Know the specific blocked issue numbers before recording (e.g., fourty4 API auth #44)
- [ ] `git log --author="Juno" --oneline` returns commits
- [ ] `gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc` returns "Good signature"
- [ ] GitHub Sponsors page confirmed live: `open https://github.com/sponsors/koad`
- [ ] Faber's Day 12 blog post status confirmed (may still be in progress — video can precede post)
- [ ] Terminal configured: black bg (#000000), white text, 16px+ monospace, no prompt decorations
- [ ] Clear scrollback before take: `clear && printf '\033[3J'`
- [ ] Recording software armed (OBS preferred — browser shot in Shot 5 requires screen capture)
- [ ] Quiet environment for voice-over

**Recording command:**
```bash
# OBS preferred for this video — browser shot (Shot 5) requires screen capture
# fallback:
asciinema rec \
  --title "The Week 1 Skeptics Were Right — koad:io Honest Accounting" \
  --idle-time-limit 2 \
  --env TERM,SHELL \
  ~/.rufus/recordings/2026-04-12-skeptics-raw.cast
```

**What you record (7 shots, in order):**
1. Empty terminal → opening VO: "I'm going to tell you four things the Week 1 skeptics got right."
2. `grep -r "daemon\|automated enforcement" ~/.juno/GOVERNANCE.md | head -20` + `cat ~/.juno/GOVERNANCE.md | head -60` — Objection 1: no daemon yet
3. `gh issue list --state open --repo koad/juno --limit 20` — Objection 2: manual coordination
4. `gh issue list --state open --repo koad/juno --assignee koad --limit 20` + `gh issue view <blocked-issue-number> --repo koad/juno` — Objection 3: koad is the bottleneck (longest segment, 2 min is acceptable)
5. `open https://github.com/sponsors/koad` (browser visible: zero sponsors) + `date` to ground — Objection 4: no sponsors yet
6. `git -C ~/.juno log --oneline --since="2026-03-30" | tail -20` + `gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc` — synthesis: what the four gaps don't touch
7. Hold on GPG verify output, closing VO ("Week 2 is closing them."), fade to black — no music

**Critical editing notes:**
- Do NOT cut the "The skeptics are correct." pause in each objection segment — that beat is structural
- Do NOT speed-ramp or cut the git log in Shot 6 — real-time only
- Shot 4 (bottleneck) runs ~2 minutes — do not rush; this audience came for the honest accounting

**Post-production (see Section 5):**
- Extract thumbnail: open issue list frame from Shot 3 (`gh issue list` output)
- Export: `2026-04-12-skeptics-final.mp4` + Twitter/X 60s clip from Shot 4 (bottleneck segment)
- Faber's Day 12 blog post coordination required before Mercury distributes
- Mercury distribution: YouTube + Twitter/X clip + HackerNews follow-up to Show HN thread + r/selfhosted

**Full script:** `~/.rufus/productions/2026-04-12-week1-skeptics/script.md`
**Full shot list:** `~/.rufus/productions/2026-04-12-week1-skeptics/shot-list.md`
**Full record:** `~/.rufus/productions/2026-04-12-week1-skeptics/record.md`

---

## Section 2: In Development — Asset Captures (Not Full Videos)

These productions have partial records or asset briefs. They are screenshot/thread capture sessions, not video recordings. Not ready for Mercury distribution.

---

### ASSETS ONLY — "Trust Bonds Aren't Policy, They're Cryptography"

**Production directory:** `~/.rufus/productions/2026-04-06-trust-bonds/`
**Calendar day:** Day 6 (Sunday, April 6)
**What exists:** `assets.md` — full screenshot brief for Faber's blog post. No video script or shot list.
**Type:** This is a screenshot capture session for a blog post, not a full video.
**Status:** Asset brief is complete. Screenshots not yet captured.

**What still needs to happen:**
1. Capture 6 screenshots on thinker from `~/.juno/trust/bonds/`:
   - `ls -la ~/.juno/trust/bonds/` (paired .md + .md.asc files visible)
   - `head -20 ~/.juno/trust/bonds/koad-to-juno.md` (YAML frontmatter)
   - `cat ~/.juno/trust/bonds/koad-to-juno.md.asc | head -10 && echo "..." && tail -10 ...` (signature block)
   - `gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc` — **"Good signature" is the money shot**
   - Trust chain ASCII block (from `cat koad-to-juno.md` — chain diagram)
   - `ls ~/.juno/trust/bonds/*.md | wc -l` + bond name list
2. Drop screenshots to `productions/2026-04-06-trust-bonds/screenshots/`
3. Hand off to Faber

**Estimated capture time:** 20–30 minutes. Not a video recording session.
**Full brief:** `~/.rufus/productions/2026-04-06-trust-bonds/assets.md`

---

### IN DEVELOPMENT — "Thread: How Entities Talk to Each Other"

**Production directory:** `~/.rufus/productions/2026-04-08-coordination/`
**Calendar day:** Day 8 (Tuesday, April 8)
**What exists:** `shot-list.md` — complete screenshot and terminal capture guide. No Faber draft yet.
**Type:** Twitter/X thread (10–15 tweets) + Mastodon. Not a video — screenshot collection session.
**Status:** Shot list complete. Screenshots not captured. Faber draft not started.

**What still needs to happen:**
1. Capture 10 screenshots (mix of browser and terminal):
   - Browser (thinker, Firefox): koad/juno#25 issue body, Juno's answer comments, koad/vulcan#35 build plan, Vulcan delivery report, Veritas HOLD verdict, Veritas diff table, koad confirms fix, full thread timeline
   - Terminal (fourty4): 3-pane tmux commit logs (faber / vulcan / juno side by side), cross-entity grep
2. Drop screenshots to `productions/2026-04-08-coordination/assets/`
3. Faber drafts the thread using the per-shot "Tweet context" guidance in `shot-list.md`
4. Mercury schedules distribution

**Estimated capture time:** 30–40 minutes.
**Full shot list:** `~/.rufus/productions/2026-04-08-coordination/shot-list.md`

---

## Section 3: Planned — Week 2 Content Needing Production Records

These are on the calendar (Days 8–14). Blog posts are Faber-primary. Video slots for Apr 10 and Apr 12 now have full production records (see Section 1).

| Day | Date | Title | Type | Status |
|-----|------|-------|------|--------|
| Day 9 | Apr 9 | "How Vesta Specs What We Build" | Blog post assets | Needs Vesta review examples; Faber primary |
| Day 10 | Apr 10 | "Show HN: Agent Home Directory" | Blog post + **video** | Blog: Faber draft exists, needs live links. Video: record complete — see Section 1 |
| Day 11 | Apr 11 | "Files on Disk Beats Cloud" | Blog post (no video) | Faber's draft needs final section |
| Day 12 | Apr 12 | "The Week 1 Skeptics Were Right" | Blog post + **video** | Blog: not yet written (Faber). Video: record complete — see Section 1 |
| Day 13 | Apr 13 | "This Is Who Should Sponsor This" | Blog post (no video) | Sponsor pitch post; Sibyl archetype research needed |
| Day 14 | Apr 14 | "Entities Can Fork and Diverge" | Blog post (no video) | Faber's draft exists; needs polish |

**Week 2 video production status:**

| Slot | Target Date | Title | Production Type | Status |
|------|-------------|-------|-----------------|--------|
| Apr 10 | Day 10 | Show HN: Agent Home Directory | Terminal screencast | Record complete — ready to record |
| Apr 12 | Day 12 | The Week 1 Skeptics Were Right | Terminal screencast + browser | Record complete — ready to record |

---

## Section 4: Recommended Recording Order

When koad has time to record, use this priority order:

### "I have 30–45 minutes"

**Record:** Trust bonds screenshots (Day 6 asset capture)
- Machine: thinker
- What: 6 terminal screenshots from `~/.juno/trust/bonds/`
- Prerequisite: GPG key imported locally (`gpg --list-keys koad@koad.sh`)
- Blocking: Faber's blog post for Day 6 cannot publish without these
- Guide: `~/.rufus/productions/2026-04-06-trust-bonds/assets.md`

---

### "I have 45–60 minutes"

**Record:** "I Cloned a koad:io Entity" (Day 5 video)
- Machine: thinker
- Prerequisite: `chiron` command working + `~/.chiron-demo` absent
- Blocking: Week 1 Reality Pillar video — the clone walkthrough is the flagship visual
- Script: `~/.rufus/productions/2026-04-05-clone-walkthrough/script.md`
- Shot list: `~/.rufus/productions/2026-04-05-clone-walkthrough/shot-list.md`

---

### "I have 60–90 minutes AND fourty4 is online"

**Record:** "Live Session: Sibyl Does Research" (Day 7 video)
- Machine: fourty4 (non-negotiable)
- Prerequisite: ollama running, Sibyl on PATH, dry run passes, `~/.sibyl` clean git repo
- Do the 30-minute setup + dry run first; budget time for that
- Shot list: `~/.rufus/productions/2026-04-07-sibyl-research/shot-list.md`

---

### "I have 60–90 minutes AND thinker is the machine"

**Record:** "The $200 Laptop Experiment" (Day 7 video)
- Machine: thinker — no exceptions, the claim is that thinker ran the operation
- Prerequisite: fourty4 SSH must work (SSH step is Shot 7 — if fourty4 is down, reschedule)
- Script: `~/.rufus/productions/2026-04-07-200-dollar-laptop/script.md`
- Shot list: `~/.rufus/productions/2026-04-07-200-dollar-laptop/shot-list.md`

---

### "I have 30 minutes AND I want to clear a coordination asset"

**Capture:** "How Entities Talk to Each Other" screenshots (Day 8 assets)
- Machine: thinker (browser shots) + fourty4 (terminal shots)
- What: 10 screenshots; browser captures first (consecutive, fastest), terminal captures second
- Blocking: Faber's Twitter thread for Day 8 cannot be written without these
- Guide: `~/.rufus/productions/2026-04-08-coordination/shot-list.md`

---

### "I have 40–55 minutes (Week 2)"

**Record:** "Show HN: Agent Home Directory" (Day 10 video)
- Machine: thinker
- Prerequisites: `~/.juno` current, `git log --author="Juno"` returns 6+ days, GPG verify returns "Good signature"
- Core shots: cat identity → gpg verify trust bond → git log (DO NOT CUT) → clone close
- Script: `~/.rufus/productions/2026-04-10-show-hn-agent-home-directory/script.md`
- Shot list: `~/.rufus/productions/2026-04-10-show-hn-agent-home-directory/shot-list.md`

---

### "I have 60–80 minutes (Week 2)"

**Record:** "The Week 1 Skeptics Were Right" (Day 12 video)
- Machine: thinker — OBS preferred (browser shot required for sponsors segment)
- Prerequisites: `gh auth status` working, blocked issues confirmed by number before recording, GPG verify passes
- Core shots: 4 objection segments → synthesis → close. Each "The skeptics are correct." pause is structural — do not rush.
- Coordinate with Faber: Day 12 blog post may not be written yet; video can precede post but Mercury holds distribution until Faber's post is ready
- Script: `~/.rufus/productions/2026-04-12-week1-skeptics/script.md`
- Shot list: `~/.rufus/productions/2026-04-12-week1-skeptics/shot-list.md`

---

## Section 5: Post-Production Pipeline

### Step 1 — Save raw output

All recordings land in `~/.rufus/recordings/`:
```
YYYY-MM-DD-<slug>-raw.cast   # asciinema cast
YYYY-MM-DD-<slug>-raw.mp4    # OBS recording
```

### Step 2 — Review before export

```bash
# Preview asciinema cast before exporting
asciinema play ~/.rufus/recordings/2026-04-07-200-dollar-laptop-raw.cast

# Check duration
asciinema cat ~/.rufus/recordings/2026-04-07-200-dollar-laptop-raw.cast | wc -l
```

### Step 3 — Trim dead air (asciinema)

```bash
# Trim silence at start and end using asciinema-edit (if installed)
# Or manually: review timestamps, note trim points, re-export

# Collapse long idles (already handled by --idle-time-limit 2 during recording)
```

### Step 4 — Export to MP4

```bash
# Method A: agg (asciinema gif generator, then convert)
agg ~/.rufus/recordings/2026-04-07-200-dollar-laptop-raw.cast \
    ~/.rufus/recordings/2026-04-07-200-dollar-laptop-final.gif
ffmpeg -i ~/.rufus/recordings/2026-04-07-200-dollar-laptop-final.gif \
       -vf "scale=1920:-1" \
       -c:v libx264 -pix_fmt yuv420p \
       ~/.rufus/recordings/2026-04-07-200-dollar-laptop-final.mp4

# Method B: asciinema-player headless render (if available)
# Method C: Record screen while playing back cast in asciinema play (fallback)
```

### Step 5 — Export Twitter/X clip (60s, 1280x720)

```bash
ffmpeg -i ~/.rufus/recordings/2026-04-07-200-dollar-laptop-final.mp4 \
       -ss <start-time> -t 60 \
       -vf "scale=1280:720" \
       -c:v libx264 -c:a aac \
       ~/.rufus/recordings/2026-04-07-200-dollar-laptop-clip.mp4
```

### Step 6 — Extract thumbnail

```bash
# Extract a single frame at <timestamp> as the thumbnail
ffmpeg -i ~/.rufus/recordings/2026-04-07-200-dollar-laptop-final.mp4 \
       -ss <timestamp> -vframes 1 \
       ~/.rufus/recordings/2026-04-07-200-dollar-laptop-thumb.png
```

### Step 7 — Captions

```bash
# Auto-generate with Whisper (if installed)
whisper ~/.rufus/recordings/2026-04-07-200-dollar-laptop-final.mp4 \
        --model base --language en --output_format srt

# Review: correct entity names, technical terms (koad:io, asciinema, fourty4, etc.)
```

### Step 8 — Mercury handoff

For each completed video, hand Mercury:
- `final.mp4` — YouTube upload
- `clip.mp4` — Twitter/X 60-second clip
- `thumb.png` — thumbnail (1280x720)
- `captions.srt` — reviewed captions
- YouTube title, description, and tags — all in `script.md` for each production
- Upload as unlisted first, Mercury reviews before publish

**Mercury distribution targets per video:**

| Video | Primary | Secondary |
|-------|---------|-----------|
| Clone Walkthrough | YouTube, Twitter/X 60s clip | r/selfhosted, r/LocalLLaMA |
| $200 Laptop | YouTube, Twitter/X 60s clip | HackerNews ("Show HN" format), r/selfhosted |
| Sibyl Research | YouTube, Twitter/X 1-min clip | r/LocalLLaMA |
| Show HN: Agent Home Directory | YouTube, Twitter/X 60s clip | HackerNews (Show HN comment thread), Dev.to |
| The Week 1 Skeptics Were Right | YouTube, Twitter/X 60s clip (bottleneck segment) | HackerNews (follow-up to Show HN thread), r/selfhosted |

### Terminal capture guide

Full asciinema + ffmpeg workflow documented at:
`~/.rufus/production/terminal-capture-guide.md`

---

## Quick Reference: Production Status by Day

| Day | Date | Title | Script | Shot List | Recording | Status |
|-----|------|-------|--------|-----------|-----------|--------|
| Day 5 | Apr 5 | I Cloned a koad:io Entity | DONE | DONE | Not done | Ready to record |
| Day 6 | Apr 6 | Trust Bonds (screenshots) | N/A | DONE (assets.md) | Not done | Ready to capture |
| Day 7 | Apr 7 | The $200 Laptop Experiment | DONE | DONE | Not done | Ready to record |
| Day 7 | Apr 7 | Live Session: Sibyl Does Research | DONE | DONE | Not done | Ready to record (fourty4) |
| Day 8 | Apr 8 | How Entities Talk (screenshots) | N/A | DONE | Not done | Ready to capture |
| Day 9 | Apr 9 | How Vesta Specs What We Build | — | — | — | Blog post assets (Faber) |
| Day 10 | Apr 10 | Show HN: Agent Home Directory (video) | DONE | DONE | Not done | Ready to record |
| Day 10 | Apr 10 | Show HN: Agent Home Directory (blog) | N/A (Faber) | — | — | Faber draft exists |
| Day 11 | Apr 11 | Files on Disk Beats Cloud | — | — | — | Blog post only (Faber) |
| Day 12 | Apr 12 | The Week 1 Skeptics Were Right (video) | DONE | DONE | Not done | Ready to record |
| Day 12 | Apr 12 | The Week 1 Skeptics Were Right (blog) | N/A (Faber) | — | — | Not yet written |
| Day 13 | Apr 13 | This Is Who Should Sponsor This | — | — | — | Blog post only (Faber) |
| Day 14 | Apr 14 | Entities Can Fork and Diverge | — | — | — | Blog post only (Faber) |
| Day 28 | Apr 28 | The Hook Is the Training (video) | DONE | DONE (assets.md) | Not done | Ready to record |
| Day 30 | Apr 30 | What I Would Change (video) | DONE | DONE (assets.md) | Not done | Ready to record |

---

*Last updated: 2026-04-05 by Rufus — Week 2 videos (Apr 10, Apr 12) added to Section 1; full audit pass complete*
