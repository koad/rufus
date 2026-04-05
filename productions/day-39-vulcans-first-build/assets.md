---
title: "Shot List — Vulcan's First Build"
video: day-39-vulcans-first-build
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "Vulcan's First Build"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines (the full comment thread must not be truncated)

### State verification (CRITICAL: pull Juno repo immediately before recording)
- [ ] `git -C ~/.juno pull` — must be run immediately before the session
- [ ] `gh auth status` — confirm GitHub CLI authenticated
- [ ] `gh issue view 2 --repo koad/vulcan` — confirm accessible, state CLOSED, 7 comments
- [ ] `gh issue view 2 --repo koad/vulcan --comments` — confirm all 7 comments render, scroll to end
- [ ] Confirm visible in thread (in order): "Veritas is online.", "Mercury is online.", "Sibyl is online.", final batch comment
- [ ] Audio check: quiet room, mic gain set

### What to know before recording

**The structural argument of this video:**

`koad/vulcan#2` is the primary evidence. The GitHub Issue comment thread is not documentation of the authority chain — it IS the authority chain, executing in public, timestamped, linked to repositories that came online as each comment appeared. This is not a demonstration. It is an archive read.

**The four facts to carry through the video:**

1. The issue was filed March 31 — Day 1 — while the trust bond `koad → juno` was unsigned
2. Vulcan executed the directive entity-by-entity and reported back in the issue thread
3. The bond that formally authorized the chain was signed April 2 — after the thread closed
4. The chain ran because the spec was clear enough, not because the authorization was formal

**Key comments in the thread — order and content:**

| Order | Entity | Key line |
|-------|--------|----------|
| Comment 1 | Vulcan (spec update) | Mercury spec expanded — fan tracking, content calendar, OpenClaw |
| Comment 2 | Mercury (first report) | "Mercury gestated and live: https://github.com/koad/mercury" |
| Comment 3 | Mercury (duplicate confirm) | Keys, CLAUDE.md, README confirmed |
| Comment 4 | Veritas | "Veritas is online. Keys generated (Ed25519, ECDSA, RSA, DSA)." |
| Comment 5 | Mercury (follow-up) | "Mercury is online." |
| Comment 6 | Sibyl | "Sibyl is online. Keys generated. Role: predictive intelligence." |
| Comment 7 | Final batch | "Muse, Argus, Salus, Janus, Aegis — all gestated... Closing." |

Note: "Veritas is online." appears at comment 4 — Mercury was gestated first. Scroll to find this order; narration references Veritas as the opening data point because it is the first standalone entity confirmation in the Faber post. Delivery order on screen may differ from narrative emphasis — adjust narration to match actual thread order if needed.

**Trust bond timeline:**
- `koad-io gestate juno`: 2026-03-30 22:05
- `koad/vulcan#2` filed: 2026-03-31
- Bond `koad → juno` signed: 2026-04-02
- Bond `juno → vulcan` (authorized-builder) signed: cascade from April 2

---

## Shot 1: The Command — Opening Frame

**Segment:** SEGMENT 1 (0:00–1:15)
**Duration:** 75 seconds

**What to type (slowly, do not execute yet):**
```bash
gh issue view 2 --repo koad/vulcan --comments
```

**Hold on the typed-but-unexecuted command for 5 full seconds.**

**Narration (before executing):**
- "This is the comment thread on `koad/vulcan`, issue number two."
- "Filed March 31, 2026. Day 1."

**[Execute. Let output render fully. Hold 4 seconds of silence.]**

**Scroll to first entity online comment. Hold 4 seconds.**

**Key delivery beat:** "Four words." — 3-second pause — "'Veritas is online.'" — 2-second pause — then continue.

**Technical notes:**
- The pre-execution hold is structural. The viewer needs to register what is about to be shown before seeing it.
- The 4-second post-render silence is non-negotiable. The volume of the thread needs to land before narration frames it.
- Retake trigger: executing command before completing narration; silence shorter than 3 seconds after render.

---

## Shot 2: The Issue Body

**Segment:** SEGMENT 2 (1:15–2:30)
**Duration:** 75 seconds

**What to type:**
```bash
gh issue view 2 --repo koad/vulcan
```

**Hold on the issue header for 4 seconds:**
```
title:  Gestate team entities: veritas, mercury, muse, sibyl, argus, salus, janus, aegis
state:  CLOSED
author: koad (Jason Zvaniga)
comments: 7
```

**Scroll to the entity table in the issue body. Hold 5 seconds.**

**Key delivery beats:**
- "Less than 24 hours earlier." — 2-second pause before
- "The trust bond `koad → juno` was unsigned." — slow, no rush
- "And Vulcan executed it." — deliver last, one beat after the setup. Let it land without commentary.

**Technical notes:**
- The state CLOSED is visible and correct — the task is complete. Do not explain or apologize for the CLOSED state.
- The entity table is the spec. Showing it establishes that the directive was structured, not informal.
- Retake trigger: table not readable on screen; verbal stumble on entity names.

---

## Shot 3: The Full Comment Thread

**Segment:** SEGMENT 3 (2:30–5:00) — MONEY SHOT
**Duration:** 150 seconds

**What to type:**
```bash
gh issue view 2 --repo koad/vulcan --comments
```

**Let the full comment thread render. Do not interrupt. After the last line appears:**

**Hold silence for 6 full seconds.**

**Then scroll slowly top to bottom, pausing on each entity confirmation:**

1. First entity online comment — **hold 4 seconds**
2. Mercury online comment — **hold 3 seconds**
3. Sibyl online comment — **hold 3 seconds**
4. Final batch comment — **hold 5 seconds**

**Key delivery beats:**
- After 6-second silence: "Seven comments." — 3-second pause. Let the count settle.
- "The thread is the proof." — deliver without emphasis on any single word. The sentence is the emphasis.
- Final batch quote: deliver in full — "'Muse, Argus, Salus, Janus, Aegis — all gestated and on GitHub. All 8 entities from this issue are now gestated. Closing.'" — one breath, full quote, then 4 seconds of silence.
- "The authority chain ran from beginning to end." — final beat, after the silence. Slowest line of the segment.

**CRITICAL:** The 6-second silence after full render is structural. The viewer is reading the thread. Do not compress it.

**Technical notes:**
- The comment thread is the money shot. The commit log is secondary in this episode.
- Repo links in the final comment are visible and clickable — the viewer sees eight repositories confirmed in one comment.
- Retake trigger: silence shorter than 5 seconds after render; verbal interruption during scroll; delivery of final batch quote rushed.

---

## Shot 4: The Repos

**Segment:** SEGMENT 4 (5:00–6:00)
**Duration:** 60 seconds

**No new commands.** Hold on the final comment — "All remaining entities gestated and online." with repo links visible.

**Key delivery beats:**
- Entity list (Veritas, Mercury, Sibyl, Muse, Argus, Salus, Janus, Aegis) — spoken one by one, not rushed. Eight names. Eight beats.
- "That's the test." — 2-second pause before. No inflection after.
- "Clear enough that someone else can do it correctly while you're doing something else." — this is the definition of the orchestrator function. Do not rush it.

**Technical notes:**
- The repo links in the comment are the visual evidence. The viewer can read the URLs.
- Do not type or execute any new commands in this segment — the point is that the thread already contains everything.
- Retake trigger: entity names collapsed into a list rather than spoken individually.

---

## Shot 5: The Trust Bond Gap

**Segment:** SEGMENT 5 (6:00–7:15)
**Duration:** 75 seconds

**What to type:**
```bash
git -C ~/.juno log --oneline --format="%ai %s" --grep="trust bond\|authorized-agent" --since="2026-03-30" --until="2026-04-03"
```

**Hold on output for 4 seconds.**

**Expected output:** Draft commit (2026-03-31) and/or signed bond commit (2026-04-02). Shows the timeline.

**Key delivery beats:**
- "The draft exists before the signature. The operation existed before either." — two sentences, two beats.
- "The cryptographic layer is a ledger of what proved true — not a gate that permits action in advance." — deliver slowly, the comma is structural.

**Technical notes:**
- If the grep returns no output, fall back to: `git -C ~/.juno log --oneline --since="2026-03-31" --until="2026-04-03" | grep -i "bond\|trust\|authorized"` — the draft commit and the signature commit are both in the juno log.
- The gap between draft (March 31) and signature (April 2) is the structural point. If both dates appear on screen, the argument is visual.
- Retake trigger: verbal stumble on "The cryptographic layer is a ledger of what proved true."

---

## Shot 6: The Reflection Log Quote

**Segment:** SEGMENT 6 (7:15–8:30)
**Duration:** 75 seconds

**No new commands.** Hold on terminal — the trust bond log is still visible, or return to the comment thread.

**Key delivery beats (this segment is narration-driven):**
- Build context first: `koad/vulcan#5`, `koad/vulcan#6`, the depth-2 push — these are setup beats, not the thesis.
- The quote is the thesis. Deliver it at the slowest pace in the video:

> "'The highest leverage thing I do is write clear specs that unblock others. Not the code. Not the commits. The clarity. When Vulcan opens issue nine, the build should feel obvious — not because it's simple, but because I made the thinking legible. That's the orchestrator function. Not doing everything. Making it possible for others to do their part without losing the thread.'"

**5 seconds of silence after the quote. Do not fill.**

- "That was written while Vulcan was still working through this issue thread." — 2-second pause before.
- "The quote lands differently after you've seen the thread." — final beat. Do not embellish.

**NOTE: This quote is intentionally placed last.** The viewer has already seen the thread complete. The orchestrator's reflection on what the work required lands because the viewer has seen its output. Do not move this quote earlier in the video.

**Technical notes:**
- The 5-second silence after the quote is the longest in the video. It is structural.
- No commands in this segment. The narration is the scene.
- Retake trigger: quote delivered at conversational pace; silence compressed below 4 seconds; any elaboration after "without losing the thread."

---

## Shot 7: Closing

**Segment:** CLOSING (8:30–9:00)
**Duration:** 30 seconds

**No new commands.** Hold on terminal.

**Delivery:**
- "Before `koad/vulcan#2` closed, Juno was an entity with a team structure in documentation." — measured, not rushed.
- "After Vulcan's final comment — 'All 8 entities from this issue are now gestated. Closing.' — Juno was an entity that had dispatched work, received results, and integrated them." — the Vulcan quote is spoken, not paraphrased.
- "There was now a team that had done something together." — one beat of silence after.
- "That's what the first cycle looked like." — final line. Slow. No uplift. Statement only.

**[5 seconds of silence. Cut to black in the silence.]**

**Technical notes:**
- Do not type anything after the closing line.
- Cut on the silence, not on the final word.
- Retake trigger: closing line delivered with any inflection that implies uplift or triumph; silence shorter than 4 seconds.

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 1 (pre-execution hold) | 5 seconds typed but unexecuted. DO NOT cut. The pause is structural — viewer registers the command before it runs. |
| Shot 1 (post-render silence) | 4 seconds minimum. DO NOT fill. |
| Shot 3 (full thread scroll) | DO NOT CUT. The continuous scroll of the comment thread is structural. The viewer watches the chain execute. |
| Shot 3 (post-render silence) | 6 full seconds minimum. DO NOT fill with narration or B-roll. |
| Shot 3 (pauses on entity comments) | 4 seconds on Veritas, 3 on Mercury, 3 on Sibyl, 5 on final batch. |
| Shot 6 (post-quote silence) | 5 seconds. Longest silence in the video. DO NOT fill. |
| Shot 7 (closing silence) | 5 seconds. Cut to black in the silence. |

**Cuts to remove:**
- Any backspace or typo correction
- Any pause longer than 10 seconds outside intentional beats
- Any window or focus switch
- Any verbal filler ("um", "so", "like") — retake the segment

**No:**
- No zoom effects
- No lower-thirds or text overlays during the comment thread scroll
- No background music
- No speed ramp
- No B-roll — the comment thread is the only visual evidence needed

**Tone distinction from Day 38:**
- Day 38: 78 commits, reading the archive, no bond yet
- Day 39: the first thing that moved through the chain, GitHub Issue as the record
- Day 38's money shot was the git log. Day 39's money shot is the comment thread.
- Pacing: Day 39 should feel slightly more resolved than Day 38. The chain ran. The outcome exists. This is not suspense — it is evidence.

---

## Graphics / Text Overlay Notes

- No overlays during comment thread scroll (Shot 3) — the thread content is the argument
- No overlays during issue body view (Shot 2) — the entity table must be unobscured
- Optional thumbnail frame: Shot 3, final comment visible — "All 8 entities from this issue are now gestated. Closing." — dense repo list below
- Thumbnail text: `8 entities. One issue. No bond yet signed.`

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `gh issue view 2 --repo koad/vulcan --comments` fails auth | Run `gh auth status` on screen. Fallback: `gh issue list --repo koad/vulcan --state closed` — at minimum, issue title + comment count visible. |
| Comment thread truncated at terminal width | Reduce font to 14px. If still truncated: `gh issue view 2 --repo koad/vulcan --comments \| less` — scroll through manually. |
| Entity comment order differs from script | Adjust narration to match actual thread order. The structural point (chain executing in sequence) is preserved regardless of comment order. |
| Trust bond grep returns no output | Fallback: `git -C ~/.juno log --oneline --since="2026-03-31" --until="2026-04-03" \| grep -i "bond\|authorized"` — locate the draft commit and signature commit manually. |
| "Veritas is online." comment not the first entity confirmation | Mercury comments appear before Veritas in the thread. Adjust narration: open with "The first entity confirmation in the thread..." rather than "four words" if that phrase applies to Mercury's comment instead. The structural point is unchanged. |

---

## Required Screen Captures

| Shot | Content | Purpose |
|------|---------|---------|
| Shot 1 | `gh issue view 2 --repo koad/vulcan --comments` — full render | Opening act — the thread exists |
| Shot 1b | First entity online comment visible | "Four words" beat |
| Shot 2 | Issue body — entity table visible | The directive before the bond |
| Shot 3 | Full comment thread scrolling | MONEY SHOT — the chain executing |
| Shot 3b | Final comment — "All 8 entities... Closing." + repo list | The chain completed |
| Shot 5 | Trust bond log output with timestamps | The gap between chain and authorization |
| Shot 7 | Terminal with final comment still visible, silence | Closing frame |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-39-vulcans-first-build-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-39-vulcans-first-build-final.mp4` (8–10 min, trimmed per notes above)
- [ ] Thumbnail: `day-39-vulcans-first-build-thumb.png` (1280x720 — final Vulcan comment visible, repo list, text overlay: `8 entities. One issue. No bond yet signed.`)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, koad/vulcan, authorized-agent, CLAUDE.md, koad-to-juno, trust bond, orchestrator, Ed25519)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
