---
title: "Shot List — Show HN: Agent Home Directory"
video: 2026-04-10-show-hn-agent-home-directory
production-owner: Rufus
hardware: thinker (primary)
tier: Tier 3 — terminal capture
status: production-ready
---

# Shot List: "Show HN: Agent Home Directory"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text
- [ ] Font: JetBrains Mono (or Fira Code / Hack) at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `thinker $ ` only. No git branch display, no powerline
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] Confirm `~/.juno` is current: `cd ~/.juno && git pull` (do this BEFORE recording, not on camera)
- [ ] Confirm `git log --author="Juno" --oneline` returns output (test before recording)
- [ ] Confirm GPG verify works: `gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc` — must return "Good signature"
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, gain set with a test sentence
- [ ] Scrollback buffer: 10,000+ lines

---

## Shot 1: The Empty Terminal

**Segment:** SETUP (0:00–0:10)
**Duration:** ~10 seconds

**What the screen shows:**
- Full-screen terminal
- Shell prompt only
- Cursor blinking

**What to type:** Nothing.

**What to say:**
> "Three commands. That's all I'm going to run. Let me show you what they tell you."

**Technical notes:**
- Pause 2–3 seconds after opening before speaking — clean cut point for editor
- No split screen. Full terminal only.
- This is the establishing shot. Keep it brief.

---

## Shot 2: Command One — cat the identity file

**Segment:** SEGMENT 1 — Identity (0:10–1:00)
**Duration:** ~50 seconds

**What to type:**
```bash
cat ~/.juno/memories/001-identity.md
```

**Expected output:** Full identity memory file — Juno's role, team position, who she reports to, operational context. ~40–60 lines.

**What to say (while file scrolls):**

As file begins:
> "Command one. This is Juno's identity file. A committed file on disk — not a prompt parameter. Not a runtime variable."

On the role/team section (if visible):
> "Juno is the business orchestrator. That's not a description I typed into a chat window — it's a file with a six-day git history. Every restart, every framework swap, every host migration — she reads this file."

After file finishes:
> "That file has been on disk since day one. The git history proves it."

**Technical notes:**
- Full cat, not `head`. Let the complete file display.
- Let it rest 2–3 seconds after scrolling finishes before moving to Shot 3.
- If the file is very long (>80 lines), it's acceptable — don't cut it short.

---

## Shot 3: Command Two — gpg --verify the trust bond

**Segment:** SEGMENT 2 — Authorization (1:00–2:00)
**Duration:** ~60 seconds

**What to type:**
```bash
gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc
```

**Expected output:**
```
gpg: Signature made [date]
gpg:                using Ed25519 key [key-id]
gpg: Good signature from "Juno <juno@kingofalldata.com>"
```

**What to say (before running):**
> "Command two. Authorization."

**What to say (as command runs):**
> "Juno issued a signed peer bond to Sibyl — the research entity. This verifies the cryptographic signature."

**When output appears — highlight "Good signature":**
> "Good signature. That's not a role setting in a config file. That's a signed authorization agreement that can be verified by anyone with GPG installed."

**Then show the bond file itself:**
```bash
cat ~/.juno/trust/bonds/juno-to-sibyl.md
```

**What to say (while bond file displays):**
> "Open it with any text editor — it tells you exactly what Sibyl is permitted to do, who said so, and when. Compare that to a 403 error with no explanation."

**Technical notes:**
- The "Good signature" line is the money shot of this segment. Pause before speaking after it appears — let the viewer read it.
- Show both the verify output AND the bond contents. The verify proves authenticity; the bond contents prove readability.
- If GPG verify fails for any reason: stop recording. Do not continue. Fix the issue.
- Retake trigger: anything other than "Good signature from Juno..."

---

## Shot 4: Command Three — git log

**Segment:** SEGMENT 3 — History (2:00–3:30)
**Duration:** ~90 seconds (DO NOT CUT THIS SEGMENT)

**What to type:**
```bash
git -C ~/.juno log --author="Juno" --oneline
```

**Expected output:** Full log of commits — 200+ entries across 6 days. Let it scroll. All of it.

**What to say before running:**
> "Command three. History."

**What to say while the log scrolls (slow, deliberate — let it scroll):**
> "213 commits. Six days. Every decision Juno made — timestamped, attributed, tamper-evident."

*(pause — let the scroll continue)*

> "Not a vendor audit log. Not a cloud dashboard. The same git you already use."

*(pause — more scroll)*

> "Each one of those lines is a session. A decision. A deliverable. You can read any of them."

**After the scroll completes (or reaches terminal bottom):**
```bash
git -C ~/.juno log --author="Juno" --oneline | wc -l
```

**What to say when count appears:**
> "That number. That's the entity's cognitive history. On your disk. Revertable. Forkable. Clonable."

**Technical notes:**
- DO NOT cut or speed-ramp this shot. The scroll is the emotional core of the entire video.
- Accept all latency and scroll time naturally.
- If terminal buffer is too small to show all commits, that's fine — the scroll filling the screen is the image we need.
- The `wc -l` line after is a deliberate punctuation beat. Type it slowly.

---

## Shot 5: The Bridge — Show the repo

**Segment:** TRANSITION (3:30–4:00)
**Duration:** ~30 seconds

**What to type:**
```bash
git -C ~/.juno remote -v
```

**Expected output:**
```
origin  https://github.com/koad/juno (fetch)
origin  https://github.com/koad/juno (push)
```

**What to say:**
> "Remote is GitHub. Public. Anyone can read the history."

*(pause)*

> "But the entity lives here — on this disk. The remote is a mirror, not the source of truth."

**Technical notes:**
- Brief shot. Set up the close. Don't linger.

---

## Shot 6: The Try It Command

**Segment:** CLOSE — Call to Action (4:00–4:45)
**Duration:** ~45 seconds

**What to type (slowly, deliberately):**
```bash
git clone https://github.com/koad/juno
cat juno/memories/001-identity.md
```

**What to say while typing the clone:**
> "To understand the pattern — one clone, then read the identity file."

**After cat output appears:**
> "No setup required to understand it. That's persistent agent identity. Files on disk."

*(pause — 2 seconds)*

> "Not vaporware. Not a demo. Commits."

*(pause)*

> "Link in the description."

**Technical notes:**
- Type at comfortable, deliberate pace — no rushing the clone command.
- Let the clone complete fully before typing the cat command.
- The last three sentences are the video's closing statement. One breath each. Pauses intentional.
- Editor: do NOT cut these pauses.

---

## Shot 7: Fade to Black

**Duration:** 2–3 seconds
- Simple cut to black or 1-second fade
- No music. No end card animation.
- Optional: hold on terminal with clone output for 1 extra second before fade.

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 1 to Shot 2 | Clean cut after opening line |
| Shot 2 (cat identity) | Full file display — do NOT cut short |
| Shot 3 (gpg verify) | Full output must show — pause on "Good signature" |
| Shot 3 (cat bond) | Full bond file display |
| Shot 4 (git log) | DO NOT CUT. DO NOT SPEED RAMP. Full scroll is the emotional core. |
| Shot 5 (remote -v) | Clean and brief |
| Shot 6 (close) | Pauses between sentences are intentional beats — do NOT cut them |

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp anywhere
- No cuts inside the git log scroll

**Cuts permitted:**
- Any pause > 10 seconds outside intentional closing beats (Shot 6)
- Dead air at very start and very end of recording

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `gpg --verify` fails | Stop recording. Fix GPG issue. Do not proceed with a failed verify. |
| `git log` returns empty | Stop recording. Confirm correct directory and author name. |
| Network error on `git clone` (Shot 6) | Only the final clone matters; retake Shot 6 from its start |
| Take goes > 6 minutes | Tighten Shot 2 VO — reduce commentary, let file scroll carry more weight |

---

## Final Deliverables

- [ ] Raw recording: `~/.rufus/recordings/2026-04-10-show-hn-raw.mp4` or `.cast`
- [ ] Edited cut: `~/.rufus/recordings/2026-04-10-show-hn-final.mp4` (4–6 min)
- [ ] Twitter/X clip: `~/.rufus/recordings/2026-04-10-show-hn-clip-twitter.mp4` (60s — start at git log scroll)
- [ ] Thumbnail: `~/.rufus/recordings/2026-04-10-show-hn-thumb.png` (1280x720 — frame from git log filling screen)
- [ ] Captions: auto-generated + manually reviewed (correct: Juno, koad:io, Sibyl, GPG)
- [ ] Upload-ready package handed to Mercury with metadata from `script.md`
