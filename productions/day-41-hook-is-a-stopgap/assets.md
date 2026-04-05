---
title: "Shot List — The Hook Is a Stopgap"
video: day-41-hook-is-a-stopgap
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "The Hook Is a Stopgap"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines

### State verification (CRITICAL: verify all paths immediately before recording)
- [ ] `ls ~/.koad-io/daemon/src/` — confirm accessible
- [ ] `cat ~/.juno/passenger.json` — confirm file exists, valid JSON, handle/name/role present
- [ ] `ls ~/.koad-io/packages/workers/` — confirm workers package directory exists
- [ ] Dark Passenger extension: loaded in Chrome, daemon running, roster UI populated at localhost:28282
- [ ] `KOAD_IO_PORT` environment variable: check value or confirm default 28282
- [ ] Day 37 promise quote accessible for reference during recording
- [ ] Audio check: quiet room, mic gain set
- [ ] OBS: single-monitor capture configured, no chat overlay

### What to know before recording

**The structural argument of this video:**

The hook works. The daemon is built. The worker system exists but is not yet wired in. This video audits the Day 37 promise against current system state. The argument is honest — most of the architecture is in place, one critical piece (the worker system) is the named gap. The comparison table is the intellectual center. "The Interface Survives" section is the thesis landing.

**The five technical facts to carry through the video:**

1. The daemon is a single Meteor process: DDP pub/sub + MongoDB + HTTP, all on port 28282 (`KOAD_IO_PORT`)
2. `passenger.json` is how entities register — auto-discovered at startup and on `passenger.reload` (60-second interval is spec'd, not implemented)
3. The worker system (`koad:io-worker-processes`) exists at `~/.koad-io/packages/workers/` — substantively implemented, not yet wired into the daemon
4. Dark Passenger connects to `ws://127.0.0.1:28282`, subscribes to `current` and `all` publications, delivers URL context via `passenger.ingest.url`
5. The interface semantics (interactive/task/PRIMER/locks) are preserved in the daemon model — only the transport changes

**Key accuracy constraints:**
- Port is 28282, configurable via `KOAD_IO_PORT` — not hardcoded
- Daemon is at `~/.koad-io/daemon/src/` — framework layer, not entity layer
- Worker package exists but does NOT run — do not imply it is operational
- `passenger.reload` is the current trigger; 60-second auto-refresh is spec'd only
- Dark Passenger WebSocket endpoint: `ws://127.0.0.1:28282` — not a different port

---

## Shot 1: The Promise — Opening Frame

**Segment:** SEGMENT 1 (0:00–1:30)
**Duration:** 90 seconds

**What to run:**
```bash
grep -A3 "stopgap" ~/.faber/posts/2026-05-11-the-hook-is-a-stopgap.md | head -6
```

**Expected output — the Day 37 quote:**
```
> "The hook today is a stopgap that works... When the daemon is live, the hook becomes
> a thin client. The interface survives: interactive vs. task, PRIMER injection, lock
> semantics. The transport changes."
```

**Hold output for 4 seconds before narrating.**

**Key delivery beats:**
- "Today we audit the claim." — 3-second pause before the line
- "The hook is a stopgap. What replaces it?" — end of segment, 4 seconds of silence after

**Technical notes:**
- If the grep path doesn't resolve, use the equivalent in `~/.faber/posts/` — the post file is `2026-05-11-the-hook-is-a-stopgap.md`
- The quote must be legible on screen — if it wraps awkwardly, adjust terminal width before recording
- Retake trigger: quote not fully visible; verbal stumble on "The transport changes."

---

## Shot 2: The Daemon Directory

**Segment:** SEGMENT 2 (1:30–3:30)
**Duration:** 120 seconds

**What to run:**
```bash
ls ~/.koad-io/daemon/src/
```

**Hold output for 5 seconds of silence before narrating.**

**Optional supporting command:**
```bash
echo $KOAD_IO_PORT
```
(or `echo "Default port: 28282"` if unset)

**Key delivery beats:**
- Three-service breakdown delivered as distinct beats — DDP, MongoDB, HTTP — not as a list read in one breath
- "The database is the cache. The file is the record." — one pause before each sentence
- "One daemon per machine. All entities on that machine share it." — closing beat for the segment, 3-second pause after

**Technical notes:**
- The daemon directory listing is the proof of existence. Hold it. Let the viewer read the filenames.
- The port/service section is narration-driven — the `ls` output stays on screen as a backdrop
- Retake trigger: three services collapsed into one paragraph without distinct pauses; silence shorter than 4 seconds after `ls` output

---

## Shot 3: Comparison Table Overlay — MONEY SHOT

**Segment:** SEGMENT 3 (3:30–5:30)
**Duration:** 120 seconds

**Format:** Full-screen overlay — 6 rows, 3 columns. Must be legible at recording resolution (1920x1080 minimum).

**Table content:**

| Row | Hook (today) | Daemon (next) |
|-----|-------------|---------------|
| PRIMER assembly | `claude -p` loads `CLAUDE.md`. No pre-flight check, no dynamic cross-entity pull. | `entity-upstart` and `daemon-connected` lifecycle hooks. Daemon coordinates PRIMER assembly across all registered entities. |
| Serialization | PID lock at `/tmp/entity-<name>.lock`. Concurrent SSH callers from different machines not protected. | MongoDB-backed worker queue. `concurrency: "no-parallel"`. Next execution skipped and logged if worker is running. |
| Routing | Hardcoded: `ENTITY_HOST`, `ENTITY_DIR`, `CLAUDE_BIN`, `NVM_INIT`. Changing where entity runs = editing the hook. | `passenger.json` discovery. Daemon scans `$HOME/.*` at startup. Entities with `KOAD_IO_VERSION` in `.env` auto-registered. |
| Invocation cost | ~200–500ms SSH overhead per non-interactive call. | Local daemon dispatch. No network round-trip. |
| Result persistence | Stdout lost unless caller captures it. | Every execution logs to MongoDB: start time, duration, success/failure, error trace. Audit trail automatic. |
| Session lifecycle | `claude -p` spawned fresh per call. Bootstraps from zero each invocation. | Daemon lifecycle hooks. Persistent process between invocations. State survives call boundary. |

**Hold the full table on screen through all six rows of narration before dismissing.**

**Key delivery beats:**
- "Six dimensions." — 3-second pause after. Let the viewer orient to the table structure.
- Each row narrated as its own unit — complete the hook description before describing the daemon
- "That is what the transport change looks like in full." — closing beat, 3-second pause after, then dismiss overlay
- Do not paraphrase table cells — read the technical content accurately

**CRITICAL:** Every claim in the table must match the technical facts in the pre-production checklist. Do not improvise cell content during narration.

**Technical notes:**
- The table is a live overlay — prepare it as a presentation slide or OBS scene, not a terminal printout
- All six rows must be visible simultaneously if display allows; if not, reveal row by row on narration cue
- Row order is structural — do not reorder
- Retake trigger: any table claim improvised away from spec; any row skipped; overlay dismissed before all six rows narrated

---

## Shot 4: passenger.json Live Read

**Segment:** SEGMENT 4 (5:30–7:00)
**Duration:** 90 seconds

**What to run:**
```bash
cat ~/.juno/passenger.json
```

**Hold output for 5 full seconds before narrating.**

**Expected output should include:**
- `handle`, `name`, `role` (required fields)
- Optionally: `avatar`, `outfit`, `status`, `buttons`

**Key delivery beats:**
- "This is what the daemon reads at startup." — first line after the hold
- "`buttons` array" section gets its own beat — 3-second pause before "The buttons array"
- "The daemon auto-discovers `passenger.json` at startup" — delivered as architecture, not instruction
- "The spec calls for sixty-second automatic refresh intervals. The interval is not yet implemented." — deliver this gap directly, no softening

**Technical notes:**
- The `passenger.json` content must be readable on screen — if the file is lengthy, terminal scroll may be needed; do not crop or pipe through `head` — show the full file
- The `buttons` field is a structural point — if the current `~/.juno/passenger.json` has no `buttons`, note it as optional during narration
- Retake trigger: file content not legible; narration begins before 5-second hold completes

---

## Shot 5: Workers Package Directory

**Segment:** SEGMENT 5 (7:00–8:00)
**Duration:** 60 seconds

**What to run:**
```bash
ls ~/.koad-io/packages/workers/
```

**Hold output for 4 seconds before narrating.**

**Key delivery beats:**
- "The `koad:io-worker-processes` Meteor package. It exists." — hold 2 seconds after "It exists."
- Worker capabilities listed (scheduler, retry, MongoDB state, health diagnostics) — one breath, measured
- "The package has not been added to the daemon's Meteor package dependencies. It does not run yet." — deliver directly. No hedging.
- "Wiring it in is the next build item." — final beat, 2-second pause after

**Technical notes:**
- The `ls` output is the evidence that the package exists
- The gap (not wired in) must be stated explicitly — this is the honest accounting
- Do not imply the worker system is operational — it is not
- Retake trigger: worker system gap understated or omitted; `ls` output truncated

---

## Shot 6: Dark Passenger Extension UI

**Segment:** SEGMENT 6 (8:00–8:45)
**Duration:** 45 seconds

**Switch to browser.** Dark Passenger extension UI visible.

**What to show:**
- Extension panel open
- Connection confirmed to `ws://127.0.0.1:28282`
- Entity roster visible (populated from daemon)
- If possible: demonstrate `passenger.check.in` selecting an active entity

**Key delivery beats:**
- "Connects to the daemon via DDP at `ws://127.0.0.1:28282`" — point to connection indicator if visible
- "The entity now has browser context without the operator pasting anything." — 3-second pause after
- "It is a passenger, not a driver." — slow, 2-second pause before

**Technical notes:**
- This is the only live-system demo in the episode — the extension must be visibly connected
- If the daemon is not running when recording begins, start it before this shot and confirm extension reconnects
- Do not demonstrate URL ingest live — describe the behavior, show the connection
- WebSocket endpoint must be visible or confirmable: `ws://127.0.0.1:28282`
- Retake trigger: extension shows disconnected state; roster empty

---

## Shot 7: The Interface Survives — Closing

**Segment:** SEGMENT 7 (8:45–10:30)
**Duration:** 105 seconds

**Return to terminal. Blank screen. No command typed.**

**Narration is the scene. Every pause is structural.**

**Delivery map:**

| Line | Pause after |
|------|-------------|
| "Day 37's claim was precise." | 3 seconds |
| "The interface survives. The transport changes." | 4 seconds silence |
| [full migration paragraph] | 4 seconds silence |
| "But the semantics stay constant." | 3 seconds |
| "Interactive invocation still opens a terminal session." | 2 seconds |
| "Task invocation still executes without a window." | 2 seconds |
| "PRIMER injection still happens at startup..." | 2 seconds |
| "Lock semantics still apply..." | 4 seconds silence |
| "The hook will still run. The entity doesn't change when the transport does." | 3 seconds |
| [full job description paragraph] | 4 seconds silence |
| "That is the portability point." | 3 seconds |
| "An entity is not its transport." | 3 seconds |
| "The files on disk, the identity, the PRIMER, the trust bonds — those are the entity." | 2 seconds |
| "Everything else is plumbing." | 4 seconds silence |
| "When the daemon is live and the worker system ships, the hook becomes a thin client." | 3 seconds |
| "Until then, the hook is a stopgap." | 3 seconds |
| "It works." | 6 seconds silence → cut to black |

**Key delivery beats:**
- "The interface survives. The transport changes." — two sentences, two beats. Do not run them together.
- "An entity is not its transport." — slowest single line of the video
- "It works." — no inflection. Statement only. Then silence. Then black.

**CRITICAL:** The four-beat sequence (Interactive invocation / Task invocation / PRIMER injection / Lock semantics) is a list, but do not deliver it as a list. Each line is a separate claim. Each gets its full 2-second pause.

**Technical notes:**
- No commands typed in this segment
- The blank terminal is the visual. The narration carries the argument.
- Cut to black during the 6-second silence after "It works." — not on the word itself
- Retake trigger: "It works." delivered with uplift or relief; silence after "It works." shorter than 5 seconds; any elaboration after "It works."

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 1 (post-quote hold) | 4 seconds minimum. DO NOT fill. |
| Shot 2 (post-ls silence) | 5 seconds minimum. DO NOT fill with narration during. |
| Shot 3 (table overlay) | DO NOT DISMISS until all six rows narrated. The continuous table view is structural. |
| Shot 4 (post-cat hold) | 5 full seconds. Viewer reads the file. |
| Shot 5 (post-ls hold) | 4 seconds minimum. |
| Shot 7 (post-"transport changes" silence) | 4 seconds. First major silence of closing. |
| Shot 7 (post-"constant" beats) | 2 seconds each — maintain throughout the four-line sequence |
| Shot 7 ("It works." closing silence) | 6 seconds. Cut to black in the silence. |

**Cuts to remove:**
- Any backspace or typo correction
- Any pause longer than 10 seconds outside intentional beats
- Any window or focus switch (except terminal → browser → terminal for Segment 6)
- Any verbal filler ("um", "so", "like") — retake the segment

**No:**
- No zoom effects
- No lower-thirds or text overlays (except the comparison table overlay in Segment 3)
- No background music
- No speed ramp
- No B-roll

**Tone distinction from Day 39:**
- Day 39: milestone — the authority chain ran, retrospective read of a closed issue
- Day 41: audit — a promise made on Day 37 measured against current system state
- Day 39 should feel slightly resolved. Day 41 should feel honest and architectural.
- The worker system gap is named directly — this is not a setback, it is the next item on the build list.

---

## Graphics / Text Overlay Notes

- Comparison table (Shot 3): only overlay in the episode. Full-screen. 6 rows × 3 columns. White on dark background, matching terminal aesthetic.
- Optional thumbnail frame: Shot 7, blank terminal, last line visible — "It works." — or the comparison table with all six rows visible
- Thumbnail text options:
  - `The hook works. The daemon is next.`
  - `One port. Three services. The interface survives.`
  - `Day 41: The daemon architecture.`

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `ls ~/.koad-io/daemon/src/` fails | Show `ls ~/.koad-io/daemon/` — the daemon directory existing at all is the relevant evidence |
| `cat ~/.juno/passenger.json` returns no file | Show `ls ~/.juno/*.json` to confirm the file name; check if it's `passenger.json` or `passenger.json.example`; if absent, show another entity's passenger.json from `~/.vulcan/` or `~/.sibyl/` and note the path |
| `ls ~/.koad-io/packages/workers/` empty | Show `ls ~/.koad-io/packages/` — the workers directory existing at all is the evidence; if absent entirely, narrate the gap more directly |
| Dark Passenger extension disconnected | Start daemon with `cd ~/.koad-io/daemon/src && meteor` (or equivalent) on screen; let extension reconnect; show the reconnect indicator |
| `KOAD_IO_PORT` unset | `echo "Default port: 28282"` on screen — the default is the relevant fact |
| Comparison table overlay fails to load | Fall back to typing the table as a formatted `cat` of a temp markdown file, or reference it from the Faber post: `grep -A 30 "Hook vs. Daemon" ~/.faber/posts/2026-05-11-the-hook-is-a-stopgap.md` |

---

## Required Screen Captures

| Shot | Content | Purpose |
|------|---------|---------|
| Shot 1 | Day 37 promise quote rendered in terminal | The promise being audited |
| Shot 2 | `ls ~/.koad-io/daemon/src/` output | Daemon exists — framework layer |
| Shot 3 | Comparison table, all six rows | MONEY SHOT — transport change in full |
| Shot 4 | `cat ~/.juno/passenger.json` full output | Registration card live on screen |
| Shot 5 | `ls ~/.koad-io/packages/workers/` output | Worker package exists — not yet wired |
| Shot 6 | Dark Passenger extension UI, roster visible | DDP connection live |
| Shot 7 | Blank terminal, "It works." as final beat | Closing frame |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-41-hook-is-a-stopgap-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-41-hook-is-a-stopgap-final.mp4` (9–11 min, trimmed per notes above)
- [ ] Thumbnail: `day-41-hook-is-a-stopgap-thumb.png` (1280x720 — comparison table or "It works." terminal frame)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, passenger.json, DDP, MongoDB, KOAD_IO_PORT, PRIMER, Dark Passenger, concurrency, entity-upstart, daemon-connected)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
