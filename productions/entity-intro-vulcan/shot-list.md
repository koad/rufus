---
title: "Shot List — Meet Vulcan"
series: entity-intro
entity: vulcan
video: entity-intro-vulcan
production-owner: rufus
hardware: thinker (primary) / flowbie (fallback)
status: production-ready
---

# Shot List: Meet Vulcan

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, pure black bg (#000000), white text (#FFFFFF)
- [ ] Font: JetBrains Mono or Fira Code at 16–18px — no ligatures needed
- [ ] Shell prompt stripped: `$ ` only — no git decorations, no username, no path
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.vulcan && git pull` run in a SEPARATE terminal before recording
- [ ] Confirm `gh issue list --repo koad/vulcan --state closed | head -10` returns 10 results
- [ ] Prepare Alice repo access: clone `https://github.com/koad/kingofalldata-dot-com` to `~/.demo-koadcom` in a separate terminal, OR confirm gh API fallback works
- [ ] `~/.demo-vulcan` does NOT exist: `ls ~/.demo-vulcan 2>&1` should show error
- [ ] GitHub reachable and authenticated: `gh auth status`
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, short test sentence, confirm no echo

---

## Opening Card

**Timestamp:** 0:00–0:05
**Duration:** 5 seconds

**Screen content:**
```
vulcan
builder
koad:io ecosystem
```
Centered, white on black, monospace font matching terminal.

**Voice:** None.

**Production note:** Can be typed live in the recording terminal before clearing, or produced as a static PNG overlay in post. Live preferred — no post work needed.

---

## Shot 1: Identity Read

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:05–0:25
**Duration:** ~20 seconds

**Commands to type:**
```bash
cd ~/.vulcan && head -5 README.md
```

**Expected output:** First 5 lines of Vulcan's README — entity name, role, repo link.

**Voice:** First half of Segment 1 VO (Vulcan receives from Juno via Issues, ships to real repos, production not prototypes).

**Technical notes:**
- Type slowly — let viewer track command and output together
- Pause 2 seconds after output appears before continuing VO
- If README head-5 is sparse, use `head -10`

---

## Shot 2: Team Position

**Segment:** SEGMENT 1 — Who
**Timestamp:** 0:25–0:40
**Duration:** ~15 seconds

**Screen:** No new typing. Voice only over static output.

**Voice:** Second half of Segment 1 VO (Muse → Vulcan → Veritas → Mercury; Vulcan turns specs into software).

**Technical notes:**
- Let the README output stay on screen while speaking
- Natural pause before moving to Segment 2

---

## Shot 3: Vulcan Directory

**Segment:** SEGMENT 2 — What
**Timestamp:** 0:40–1:00
**Duration:** ~20 seconds

**Commands to type:**
```bash
ls ~/.vulcan/
```

**Expected output:** Standard entity directory structure — commands, docs, id, etc.

**Voice:** First part of Segment 2 VO — deliverables don't live here, they live in the repos he builds for.

**Technical notes:**
- Brief shot — sets up the pivot to GitHub
- Pause after output before next command

---

## Shot 4: Open Issue Queue

**Segment:** SEGMENT 2 — What
**Timestamp:** 1:00–1:30
**Duration:** ~30 seconds

**Commands to type:**
```bash
gh issue list --repo koad/vulcan --state open | head -5
```

**Expected output:** Current open issues assigned to Vulcan — ongoing work queue.

**Voice:** Second part of Segment 2 VO — GitHub Issues are the work queue, Juno files, Vulcan builds, issue closes when done.

**Technical notes:**
- This is the bridge from "what Vulcan is" to "what Vulcan ships"
- Pause after output — let viewer read the issue titles
- Pivot line ("Let's look at what he's already shipped") leads directly to Segment 3

---

## Shot 5: Clone

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:30–1:55
**Duration:** ~25 seconds

**Commands to type:**
```bash
git clone https://github.com/koad/vulcan ~/.demo-vulcan
```

**Expected output:** Standard git clone progress output.

**Voice:** "You can clone Vulcan right now..." VO from Segment 3.

**Technical notes:**
- Type the clone command slowly and deliberately — read it aloud as you type
- Let clone output scroll in full — do not skip or cut here
- After clone completes, brief pause before next command

---

## Shot 6: ls Demo Directory

**Segment:** SEGMENT 3 — Clone
**Timestamp:** 1:55–2:00
**Duration:** ~5 seconds

**Commands to type:**
```bash
ls ~/.demo-vulcan
```

**Voice:** "That's the entity. But the real proof is in the repos he's shipped to."

**Technical notes:**
- Fast shot — pivot line leads directly into Segment 4
- Do not narrate the file names

---

## Shot 7: Closed Issues

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:00–2:25
**Duration:** ~25 seconds

**Commands to type:**
```bash
gh issue list --repo koad/vulcan --state closed | head -10
```

**Expected output:** 10 most recently closed issues with issue numbers, titles, labels, and dates.

**Voice:** Segment 4 VO first half — name 4–5 specific closed issues (Alice UI, blog infrastructure, hook bug, accessibility fixes). Close with "Every CLOSED label is a task that went from filed to shipped."

**Technical notes:**
- PAUSE after output — 3 full seconds minimum before speaking
- Let the viewer scan the CLOSED labels — they are the proof
- Name real issue titles from the output (do not guess — read from screen)
- If output wraps or truncates titles, that is fine — the CLOSED state is still visible

---

## Shot 8: Vulcan's Commits on Alice

**Segment:** SEGMENT 4 — Demo
**Timestamp:** 2:25–2:50
**Duration:** ~25 seconds

**Commands to type (primary):**
```bash
git -C ~/.demo-koadcom log --author="Vulcan" --oneline -5
```

**Expected output:**
```
[hash] Build: Alice curriculum integration — serve Chiron levels via Meteor...
[hash] Build: blog infrastructure — routes, markdown rendering, nav link...
[hash] Update PRIMER.md — reflect 2026-04-04 session progress
[hash] Build Alice Phase 2A — 12-level learning journey (mocked)
[hash] Apply Mercury copy, Iris amendment, PWA service worker + icons
```

**Fallback command (if local repo not available):**
```bash
gh api 'repos/koad/kingofalldata-dot-com/commits?per_page=5' \
  --jq '.[].commit | "\(.author.name): \(.message | split("\n")[0])"'
```

**Voice:** Segment 4 VO second half — name the commits (curriculum integration, blog, Alice Phase 2A, Mercury copy). Close: "That's not a plan. That's a production codebase with Vulcan's name on the commits. Alice Phase 2A is live on kingofalldata.com right now. Vulcan built it."

**Technical notes:**
- Pause after output — let viewer read the commit messages
- The commit titles are descriptive — read two or three aloud verbatim
- "Vulcan built it" is the closing statement of the entire video — deliver it last, clearly, no trailing words

---

## Closing Card

**Timestamp:** 2:50–3:00
**Duration:** 10 seconds

**Screen content:**
```
git clone https://github.com/koad/vulcan
koad.sh
```

**Voice:** None.

**Technical notes:**
- Same aesthetic as opening card
- If typed live: type slowly, cursor blinks on last line
- If PNG overlay: fade in over 1 second, hold

---

## Retake Triggers

Stop and retake if any of the following occur:
- Background noise audible in voice track
- Typing error that requires visible correction
- `git clone` fails or hangs
- `gh issue list` returns zero closed issues (auth or network issue — check gh auth status)
- Git log command fails — switch to gh API fallback
- VO stumble on the closing line ("Alice Phase 2A is live... Vulcan built it") — this is the video's thesis, practice it

---

## Total Shot Count: 8 + 2 cards = 10 units
