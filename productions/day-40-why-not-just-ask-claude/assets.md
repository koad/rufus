---
title: "Shot List — Why Not Just Ask Claude to Do Everything?"
video: day-40-why-not-just-ask-claude
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "Why Not Just Ask Claude to Do Everything?"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines

### State verification (CRITICAL: verify all paths immediately before recording)
- [ ] `git -C /home/koad/.sibyl/ log --oneline | head -20` — confirm accessible, at least 15 entries present
- [ ] `ls ~/.veritas/` — confirm verdict files visible (Days 33–38 sequence)
- [ ] Audio check: quiet room, mic gain set
- [ ] OBS: single-monitor capture configured, no chat overlay

### What to know before recording

**The structural argument of this video:**

Sub-agents work. Day 6 proved it. The question is what a sub-agent session produces versus what a separate entity leaves behind. Three demonstrations: (1) Sibyl's git log as accumulated research practice — visible, traceable, Sibyl's own trajectory. (2) Veritas's review trail as an independently auditable accountability chain. (3) The Copia correction — not a QA failure story, a knowledge isolation story. Segment 4 is the center of the video.

**The five technical facts to carry through the video:**

1. Day 6 ran nine entities as sub-agents (session summary says nine; enumerated list says ten — discrepancy is in the source, not our accounting)
2. Sibyl's git log is the research practice made visible — not files, a track record with timestamps and authorship
3. Veritas commits verdict files to `~/.veritas/` — the trail is independent of Faber's session, auditable as a distinct chain
4. The Copia correction: $24/month (wrong) → CAD ~140/month (correct) — caught by accounting context, not QA context
5. Separate context domains catch separate classes of errors — this is the theoretical claim the Copia correction demonstrates

**Key accuracy constraints:**
- Day 6 count: cite nine (from the session summary). Acknowledge the ten/nine discrepancy exists in the source if it comes up.
- Copia correction: the wrong figure was **$24/month**, the correct figure was **CAD ~140/month**
- Veritas review sequence (Days 33–38): FAIL, NEEDS_CORRECTION, APPROVED WITH ONE CORRECTION REQUIRED, APPROVED WITH TWO CORRECTIONS REQUIRED, APPROVED WITH TWO CORRECTIONS REQUIRED
- Argus Day 30 health check: 8 of 19 entities non-compliant; Iris was the only PRIMER failure, most others were `passenger.json` gaps

---

## Shot 1: The Opening Question

**Segment:** SEGMENT 1 (0:00–1:00)
**Duration:** 60 seconds

**What to show:**
Blank terminal. No commands. This is a narration-only shot.

**Key delivery beats:**
- "Why not just ask Claude to do everything?" — 4 seconds of silence after
- "This is not a rhetorical question." — 2-second pause, then move to Day 6 evidence
- "When does the answer matter?" — 4 seconds of silence after (end of segment)

**Technical notes:**
- No commands typed in this segment
- Blank terminal is the frame
- Retake trigger: opening delivered with rhetorical energy; "This is not a rhetorical question" delivered rhetorically

---

## Shot 2: Sibyl's Git Log — CENTRAL TERMINAL SCENE

**Segment:** SEGMENT 2 (1:00–3:30)
**Duration:** 150 seconds

**What to run:**
```bash
git -C /home/koad/.sibyl/ log --oneline | head -20
```

**Expected output — approximately 20 lines of commit history:**
Should include entries for: ICM synthesis, agent data destruction incidents, forking brief, inter-agent comms, Reddit r/selfhosted positioning, Show HN framing, sovereign identity standards, sponsor acquisition patterns, trust bonds deep-dive, week 1 retrospective.

**CRITICAL HOLD:** 8 seconds of silence after output renders. Do not start narrating. Let the viewer read.

**Key delivery beats (after the 8-second hold):**
- "That is a research practice." — 3-second pause after
- "You can see the ICM synthesis brief from Day 6." — trace the source-to-citation chain
- "It would not show the researcher's own trajectory." — one of the two central contrast lines; 3-second pause after
- "One step longer. One step less verifiable." — end of segment; 4-second silence after

**Technical notes:**
- The git log output stays on screen through most of Segment 2 — do not clear it
- If Sibyl's repo is not accessible at `/home/koad/.sibyl/`, check `git -C ~/.sibyl/ log --oneline` (relative path)
- The output should be dense enough to be visually compelling as evidence — at least 12 entries
- Retake trigger: hold shorter than 6 seconds; narration begins before hold completes; verbose commentary on individual commit messages

---

## Shot 3: Veritas Review Trail

**Segment:** SEGMENT 3 (3:30–5:00)
**Duration:** 90 seconds

**What to run:**
```bash
ls ~/.veritas/
```

**Hold output for 5 seconds of silence before narrating.**

**Expected output:**
Verdict files covering Days 33–38 sequence. Filenames should be visible — the specific filenames matter less than the visible trail of time-stamped review outputs.

**Key delivery beats:**
- Review sequence read in full: FAIL → NEEDS_CORRECTION → APPROVED WITH ONE CORRECTION REQUIRED → APPROVED WITH TWO CORRECTIONS REQUIRED → APPROVED WITH TWO CORRECTIONS REQUIRED
- "If Veritas had been a sub-agent called from within Faber's session, that trail would not exist." — 3-second pause after
- "Only Faber's session invoking a reviewer role. The commits would bear Faber's authorship. The attribution would be entangled." — closing beat; 4-second silence

**Technical notes:**
- The listing is the evidence — the viewer should see files, not an empty directory
- If the verdict files are in a subdirectory (e.g., `~/.veritas/verdicts/`), run `ls ~/.veritas/verdicts/` instead
- Retake trigger: hold shorter than 4 seconds; review sequence omitted or paraphrased

---

## Shot 4: The Copia Correction — MONEY SHOT

**Segment:** SEGMENT 4 (5:00–7:00)
**Duration:** 120 seconds

**What to show:**
Terminal, blank after Shot 3 output. This is a narration-only segment.

**No commands typed in this segment.**

**Key delivery beats — this is the most important segment in the video:**
- "Day 29." — 3-second pause after. Isolated. Do not continue immediately.
- "A post claimed twenty-four dollars per month." — 2-second pause
- "The actual figure was approximately one hundred forty Canadian dollars per month." — 3-second pause
- "Veritas reviewed the post. Veritas missed the error." — 2-second pause
- "Iris reviewed the post. Iris missed the error." — 3-second pause
- **"Copia caught it."** — 4 seconds of silence after. This is the structural moment. Do not fill it.
- "She caught it because she has an independent accounting context." — measured, not triumphant
- "Separate context domains catch separate classes of errors." — 4-second pause after. This is the theoretical claim. Do not rush to close.

**CRITICAL:** Do not collapse the two missed-it lines. Veritas gets her own sentence. Iris gets her own sentence. "Copia caught it." is then isolated as a third beat with silence after.

**Technical notes:**
- This is the most intellectually important segment — it carries the theoretical load of the entire video
- The argument is: not a QA failure story, a knowledge isolation story. Carry that distinction through the narration.
- Retake trigger: "Copia caught it" delivered with triumphalism; silence after "Copia caught it" shorter than 3 seconds; the knowledge isolation framing lost in favor of QA framing

---

## Shot 5: Keyrings — Cryptographic Accountability

**Segment:** SEGMENT 5 (7:00–7:45)
**Duration:** 45 seconds

**What to show:**
Terminal, blank. Narration-only.

**No commands typed in this segment.**

**Key delivery beats:**
- "When Vulcan signs a file, Vulcan signed it — not Juno on Vulcan's behalf." — 3-second pause after
- "'Juno said Vulcan did it' versus 'Vulcan cryptographically attested to it.'" — say both clauses distinctly; 3-second pause after
- "The difference is who can be held accountable." — 4-second silence; end of segment

**Technical notes:**
- Short segment — the argument is compressed. Deliver each beat fully before moving on.
- Retake trigger: the contrast phrase ("Juno said" vs "Vulcan attested") run together without a pause between clauses

---

## Shot 6: The Cost Is Real

**Segment:** SEGMENT 6 (7:45–8:45)
**Duration:** 60 seconds

**What to show:**
Terminal, blank. Narration-only.

**Key delivery beats:**
- Cost figures delivered matter-of-fact: "two to five minutes," "thirty to sixty minutes of entity time" — not apology, not dismissal
- "Eight of nineteen entities non-compliant" — specific, not vague
- "Separate entities are valuable specifically when the work needs to compound." — closing line; 4-second silence after

**Technical notes:**
- Tone for this segment: honest accounting. Not undermining the previous argument; acknowledging the real tradeoffs.
- Retake trigger: overhead presented apologetically; tone shifts to either defensive or dismissive

---

## Shot 7: What Day 40 Looks Like — Closing

**Segment:** SEGMENT 7 (8:45–9:30)
**Duration:** 45 seconds

**Return to terminal. Blank screen. No command typed.**

**Narration is the scene. Every pause is structural.**

**Delivery map:**

| Line | Pause after |
|------|-------------|
| "Sibyl's research directory is not a collection of files." | 3 seconds |
| "It is a practice that has accumulated over forty days." | 3 seconds |
| "Briefs that informed posts. A methodology that emerged from actual work." | 4 seconds silence |
| "That architecture could not have been designed in advance." | 2 seconds |
| "It was discovered by having separate entities that needed separate initialization." | 4 seconds silence |
| "You could ask Claude to do everything." | 2 seconds |
| "For scoped tasks, you should." | 3 seconds |
| "But for work that needs to persist across sessions, compound over time, and be independently auditable —" | 3 seconds |
| "The directory is the entity." | 2 seconds |
| "The git log is the memory." | 2 seconds |
| "The keyring is the identity." | 4 seconds silence |
| "A sub-agent invocation produces an output." | 2 seconds |
| "A separate entity produces a record that outlasts the session..." | 4 seconds silence |
| "By Day 40, Sibyl's research directory is not configuration." | 2 seconds |
| "It is accumulated practice under a distinct identity." | 3 seconds |
| "That is what sovereignty looks like in daily operation." | 6 seconds silence → cut to black |

**Key delivery beats:**
- The directory/git log/keyring triple — three parallel lines, each gets its own pause. Do not run them together.
- "That is what sovereignty looks like in daily operation." — last line before cut. No inflection. Statement. Then silence. Then black.

**Technical notes:**
- No commands typed in this segment
- Blank terminal is the visual. The narration carries the entire argument.
- Cut to black during the 6-second silence after the final line — not on the word itself
- Retake trigger: final line delivered with uplift; any elaboration after "daily operation"; silence shorter than 5 seconds

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 2 (post-git log hold) | 8 seconds minimum. DO NOT fill. The log on screen is the evidence. |
| Shot 3 (post-ls hold) | 5 seconds minimum. DO NOT narrate during. |
| Shot 4 (post-"Copia caught it" silence) | 4 seconds. First structural silence in the central argument. |
| Shot 4 (post-"separate context domains" silence) | 4 seconds. Closing claim of the central argument. |
| Shot 7 (directory/log/keyring beats) | 2 seconds each — maintain through all three lines |
| Shot 7 (closing silence) | 6 seconds. Cut to black in the silence. |

**Cuts to remove:**
- Any backspace or typo correction
- Any pause longer than 10 seconds outside intentional beats
- Any verbal filler ("um", "so", "like") — retake the segment

**No:**
- No zoom effects
- No lower-thirds or text overlays
- No background music
- No speed ramp
- No B-roll
- No comparison table (this is not Day 41 — the argument is made by the git log and the narration, not a formatted table)

**Tone distinction from neighboring episodes:**
- Day 39 (Vulcan's First Build): milestone — the authority chain ran, a closed issue read retrospectively. Slightly resolved.
- Day 40 (this video): argument — the question answered by evidence on screen. Intellectual, not warm.
- Day 41 (The Hook Is a Stopgap): audit — a promise from Day 37 measured against current architecture. More technical, more precise.

---

## Graphics / Text Overlay Notes

- No overlays in this episode. The git log is the visual evidence — do not annotate it.
- Optional thumbnail frame: Shot 2, git log on screen — Sibyl's research history as accumulated practice. Or Shot 7, blank terminal, final line visible.
- Thumbnail text options:
  - `The git log IS the memory.`
  - `Why not just ask Claude? — Day 40`
  - `What a sub-agent can't leave behind.`

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `git -C /home/koad/.sibyl/ log` inaccessible | Check `git -C ~/.sibyl/ log --oneline` — if Sibyl's repo doesn't exist on this machine, note it on screen ("git pull ~/.sibyl first") and use `git -C ~/.sibyl/ log --oneline` after pulling |
| `ls ~/.veritas/` empty or inaccessible | Show `ls ~/.veritas/` output and note verbally that the trail is in another subdirectory — the point is the structural separation, not the specific filenames |
| Sibyl's git log has fewer than 10 entries | Remove `head -20` to show all entries, note the smaller count — the track record argument still holds |

---

## Required Screen Captures

| Shot | Content | Purpose |
|------|---------|---------|
| Shot 1 | Blank terminal, opening narration | The question established before any evidence |
| Shot 2 | `git -C /home/koad/.sibyl/ log --oneline \| head -20` output | Research practice made visible — CENTRAL EVIDENCE |
| Shot 3 | `ls ~/.veritas/` output | Auditable review trail — second demonstration |
| Shot 4 | Blank terminal — "Copia caught it." beat | Central argument's pivot moment |
| Shot 7 | Blank terminal — final three-line sequence | Closing frame: directory / git log / keyring |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-40-why-not-just-ask-claude-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-40-why-not-just-ask-claude-final.mp4` (8–10 min, trimmed per notes above)
- [ ] Thumbnail: `day-40-why-not-just-ask-claude-thumb.png` (1280x720 — Sibyl git log or final terminal frame)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, sub-agent, PRIMER, Copia, Veritas, Sibyl, ICM, passenger.json, trust bonds, sovereignty)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
