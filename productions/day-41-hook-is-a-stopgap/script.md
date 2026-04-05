---
title: "The Hook Is a Stopgap"
video-type: architecture
pillar: Reality
date: 2026-05-11
duration: 9–11 minutes
subject: daemon architecture, DDP/HTTP, passenger.json, worker system, Dark Passenger, hook migration path
production-owner: Rufus
status: production-ready
---

# Script: "The Hook Is a Stopgap"

## Directorial Note

Day 37 ended with a promise. Day 41 audits it.

The hook works. The daemon is built. The worker system exists but is not yet wired in. The job of this video is to walk through what the daemon actually is — one process, three services, one port — show the passenger registration card live, put the comparison on screen, and close on the sentence that anchors the whole series: the interface survives. The transport changes.

This is an architecture episode, not a milestone episode. The terminal is a live system. Commands are run against real directories. The comparison table is the money shot — not a command output, but a live overlay. Production should treat the table segment as the highest-precision scene: every cell must be legible, every claim must be accurate.

The closing section — "The Interface Survives" — is read slowly. It is the thesis of Day 37 proved on Day 41. Give it room.

---

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background (#000000), white text, fullscreen
- [ ] Font: JetBrains Mono or Fira Code, 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `ls ~/.koad-io/daemon/src/` — confirm daemon directory exists and is accessible
- [ ] `cat ~/.juno/passenger.json` — confirm file exists and is valid JSON
- [ ] `ls ~/.koad-io/packages/workers/` — confirm workers package directory exists
- [ ] Have Day 37 post pulled up for the promise quote — "The hook today is a stopgap that works..."
- [ ] Comparison table overlay prepared (see Shot 3 notes) — 6 rows, 3 columns, legible at recording resolution
- [ ] Dark Passenger extension: loaded in Chrome, daemon running at ws://127.0.0.1:28282, roster visible
- [ ] Audio check: quiet room, mic gain set
- [ ] OBS: single-monitor capture, no chat overlay

---

## SEGMENT 1 — The Promise (0:00–1:30)

**No preamble. No title card. Open on blank terminal.**

**Narration:**

> "Day 37 ended with a specific promise."

*(pause — 3 seconds)*

**Type slowly:**

```bash
cat ~/.juno/memories/001-identity.md
```

*(hold — do not execute yet)*

**Narration:**

> "Before we look at the daemon, let's look at what was said about the hook."

**Clear the line. Type instead:**

```bash
grep -A3 "stopgap" ~/.faber/posts/2026-05-11-the-hook-is-a-stopgap.md | head -6
```

**[Execute. Let output render. Hold 4 seconds.]**

**The quote should appear on screen:**

```
> "The hook today is a stopgap that works... When the daemon is live, the hook becomes
> a thin client. The interface survives: interactive vs. task, PRIMER injection, lock
> semantics. The transport changes."
```

**Narration (after 4-second hold):**

> "That quote is from Day 37. Forty-one days in."

*(pause — 2 seconds)*

> "Today we audit the claim."

*(pause — 3 seconds)*

> "The hook is a stopgap. What replaces it?"

*(pause — 4 seconds of silence)*

---

## SEGMENT 2 — What the Daemon Is (1:30–3:30)

**Narration:**

> "The daemon is a Meteor application — a single persistent process, three services."

*(pause — 2 seconds)*

> "First: the daemon directory."

**Type:**

```bash
ls ~/.koad-io/daemon/src/
```

**[Execute. Let output render fully. Hold 5 seconds of silence.]**

**Scroll through the output slowly. Do not narrate during the scroll.**

**After the hold, narration:**

> "One process. Framework layer — not in any entity directory."

*(pause — 2 seconds)*

> "Three services sharing a single port."

*(pause — 2 seconds)*

**Narration — deliver each service as a distinct beat:**

> "DDP pub/sub bus. Meteor's Distributed Data Protocol. WebSocket-based. The browser extension, the desktop widget, the admin PWA — they all stay in sync with entity state in real time. No polling. No REST calls. Live updates pushed to every connected client the moment state changes."

*(pause — 3 seconds)*

> "MongoDB state store. The entity roster — the `Passengers` collection — worker queue state, currently selected entity. Data lives at `~/.koad-io/daemon/data/`. If you clear it and restart, nothing is lost. Because the source of truth is always `passenger.json` in each entity directory — not the database. The database is the cache. The file is the record."

*(pause — 3 seconds)*

> "HTTP server. Same port as DDP — default 28282, configurable via `KOAD_IO_PORT`. Not two ports. One process. Open `localhost:28282` in a browser: live entity roster, selection controls, Reload button. No separate setup."

*(pause — 2 seconds)*

**Type slowly:**

```bash
echo $KOAD_IO_PORT
```

*(or if unset:)*

```bash
echo "Default port: 28282"
```

**Narration:**

> "One daemon per machine. All entities on that machine share it."

*(pause — 3 seconds)*

---

## SEGMENT 3 — The Comparison Table (3:30–5:30) — MONEY SHOT

**Transition to overlay. The terminal is still visible; bring up the comparison table as a full-screen legible overlay.**

**The table:**

| | Hook (today) | Daemon (next) |
|---|---|---|
| **PRIMER assembly** | Implicit — `claude -p` loads `CLAUDE.md`. No pre-flight check, no dynamic cross-entity pull. | `entity-upstart` and `daemon-connected` lifecycle hooks fire at startup. The daemon coordinates PRIMER assembly across all registered entities. |
| **Serialization** | PID lock file at `/tmp/entity-<name>.lock`. Local to caller's machine. Concurrent SSH callers from different machines are not protected. | MongoDB-backed worker queue. `concurrency: "no-parallel"` by default. If a worker is running, the next execution is skipped and logged. No caller-side lock. |
| **Routing** | Hardcoded per entity. `ENTITY_HOST`, `ENTITY_DIR`, `CLAUDE_BIN` in the hook script. Changing where an entity runs means updating the hook. | `passenger.json` discovery. Daemon scans `$HOME/.*` directories at startup, finds entities with `KOAD_IO_VERSION` in `.env`, reads the card, registers them. Entity presence is live and observable. |
| **Invocation cost** | ~200–500ms SSH connection overhead per non-interactive call. | Local daemon dispatch. Same process. No network round-trip. |
| **Result persistence** | Stdout is lost unless the caller captures it. | Every worker execution logs to MongoDB: start time, duration, success/failure, full error trace. Audit trail is automatic. |
| **Session lifecycle** | `claude -p` spawned fresh per call. Each invocation bootstraps from zero. | Entity session managed by daemon lifecycle hooks. Persistent process between invocations. State survives the call boundary. |

**Hold the table on screen. Narration — one row per beat:**

> "Six dimensions."

*(pause — 3 seconds)*

> "PRIMER assembly. The hook loads `CLAUDE.md` implicitly — no pre-flight check, no dynamic cross-entity coordination. The daemon fires lifecycle hooks at startup. `entity-upstart`. `daemon-connected`. Natural injection points. The daemon coordinates PRIMER assembly across all registered entities."

*(pause — 3 seconds)*

> "Serialization. The hook uses a PID lock file at `/tmp/entity-<name>.lock`. Local to the machine. Two SSH callers from different machines — not protected. The daemon uses a MongoDB-backed worker queue. `concurrency: 'no-parallel'` by default. If a worker is running, the next scheduled execution is skipped and logged. The daemon handles it. No caller-side logic required."

*(pause — 3 seconds)*

> "Routing. The hook has it hardcoded — `ENTITY_HOST`, `ENTITY_DIR`, `CLAUDE_BIN`, `NVM_INIT`. Changing where an entity runs means editing the script. The daemon uses `passenger.json` discovery. Startup scan. `$HOME/.*` directories. Entities with `KOAD_IO_VERSION` in their `.env` are found, read, registered. Entity presence is live."

*(pause — 2 seconds)*

> "Invocation cost. Two hundred to five hundred milliseconds of SSH overhead per non-interactive call versus local daemon dispatch. Same process. No network round-trip."

*(pause — 2 seconds)*

> "Result persistence. With the hook, stdout is lost unless the caller captures it. With the daemon, every worker execution logs to MongoDB — start time, duration, success or failure, full error trace with stack. The audit trail is automatic. Salus can query it."

*(pause — 2 seconds)*

> "Session lifecycle. The hook spawns `claude -p` fresh per call. Each invocation bootstraps from zero. The daemon manages entity session via lifecycle hooks. Persistent process between invocations. State survives the call boundary."

*(pause — 4 seconds of silence — hold table)*

> "That is what the transport change looks like in full."

*(pause — 3 seconds)*

**[Dismiss overlay. Return to terminal.]**

---

## SEGMENT 4 — passenger.json (5:30–7:00)

**Narration:**

> "Every entity in koad:io has cryptographic keys, a `.env`, and a git repo. `passenger.json` is the fourth layer — the runtime registration card for the daemon."

*(pause — 2 seconds)*

**Type:**

```bash
cat ~/.juno/passenger.json
```

**[Execute. Let output render fully. Hold 5 seconds of silence.]**

**Narration (after hold):**

> "This is what the daemon reads at startup."

*(pause — 2 seconds)*

> "Minimum viable card: `handle`, `name`, `role`. Three fields. The daemon discovers it."

*(pause — 2 seconds)*

> "Optional from there: `avatar` — a PNG path, embedded as base64 at registration time, not on each request. `outfit` — color for UI theming, auto-generated from handle hash if absent. `status` — active, paused, dormant."

*(pause — 2 seconds)*

> "And `buttons`."

*(pause — 3 seconds)*

> "The `buttons` array maps a label to an action — a hook name or a command name. Those buttons surface in the Dark Passenger overlay as one-click actions visible from any browser tab. Research. Commit. Report. Gestate. Browser-accessible without any additional integration work."

*(pause — 3 seconds)*

> "The daemon auto-discovers `passenger.json` at startup and on a manual `passenger.reload` call. Drop the file in an entity directory. The daemon finds it on the next scan. No manual registration. No config file to update."

*(pause — 2 seconds)*

> "The spec calls for sixty-second automatic refresh intervals. The interval is not yet implemented. `passenger.reload` is the current trigger."

*(pause — 2 seconds)*

---

## SEGMENT 5 — The Worker System (7:00–8:00)

**Narration:**

> "Workers are scheduled, persistent tasks executed by the daemon."

*(pause — 2 seconds)*

**Type:**

```bash
ls ~/.koad-io/packages/workers/
```

**[Execute. Let output render. Hold 4 seconds of silence.]**

**Narration:**

> "The `koad:io-worker-processes` Meteor package. It exists. Scheduler, retry logic, MongoDB-backed state, health diagnostics. Substantively implemented."

*(pause — 3 seconds)*

> "A worker has a service identifier, an interval — one to fourteen-forty minutes — a type: cron, event, hook, or manual. A task function. A concurrency setting. A retry limit. Every worker creates a MongoDB document tracking its full lifecycle: current state, last heartbeat, next execution time, success and error counts, full error history with stack traces."

*(pause — 2 seconds)*

> "The daemon's primary job is scheduling and executing workers. The passenger registry and DDP bus support the human-facing features — browser integration, widget, live roster. The worker system is the operational backbone."

*(pause — 3 seconds)*

> "This is the part that transforms an entity from a session you start manually into a persistent process that maintains state between invocations and handles scheduled tasks without operator input."

*(pause — 3 seconds)*

> "The package has not been added to the daemon's Meteor package dependencies. It does not run yet. Wiring it in is the next build item."

*(pause — 2 seconds)*

---

## SEGMENT 6 — Dark Passenger (8:00–8:45)

**Switch to browser — Dark Passenger extension UI visible, connected to ws://127.0.0.1:28282.**

**Narration:**

> "Dark Passenger is the browser-to-entity bridge."

*(pause — 2 seconds)*

> "Chrome extension. Connects to the daemon via DDP at `ws://127.0.0.1:28282`. On connection: subscribes to the `current` publication — the currently selected entity — and the `all` publication — the full roster."

*(pause — 2 seconds)*

**Point to the roster display in the extension UI.**

> "The operator calls `passenger.check.in` to select one entity as the active companion. From that point, every URL visited triggers `passenger.ingest.url` — delivering the page's URL, title, domain, timestamp, and favicon to the selected entity. The daemon fires a `passenger-url-received` hook."

*(pause — 2 seconds)*

> "The entity now has browser context without the operator pasting anything."

*(pause — 3 seconds)*

> "It is a passenger, not a driver. It does not intercept or redirect. It receives what you visit and can act on it."

*(pause — 2 seconds)*

**Return to terminal.**

---

## SEGMENT 7 — The Interface Survives (8:45–10:30) — CLOSING

**Blank terminal. No command typed.**

**Narration — read slowly. This is the slowest segment in the video. Every pause is structural.**

> "Day 37's claim was precise."

*(pause — 3 seconds)*

> "The interface survives. The transport changes."

*(pause — 4 seconds of silence)*

> "From the entity's perspective, `executed-without-arguments.sh` becomes a thin registration call rather than a full session bootstrap. The hook's job narrows from 'set up the entire invocation environment' to 'declare my worker to the daemon.' Scheduling, serialization, retry, and result logging move inside the daemon."

*(pause — 4 seconds of silence)*

> "But the semantics stay constant."

*(pause — 3 seconds)*

*(Deliver each line as a separate, unhurried beat.)*

> "Interactive invocation still opens a terminal session."

*(pause — 2 seconds)*

> "Task invocation still executes without a window."

*(pause — 2 seconds)*

> "PRIMER injection still happens at startup — better, because lifecycle hooks are coordinated rather than per-entity bootstrapping in isolation."

*(pause — 2 seconds)*

> "Lock semantics still apply — `concurrency: 'no-parallel'` is the same guarantee as the PID file, without the caller-side complexity."

*(pause — 4 seconds of silence)*

> "The hook will still run. The entity doesn't change when the transport does."

*(pause — 3 seconds)*

> "The entity's job — respond to invocations, do work, report back — is identical whether the transport is an SSH call with a PID lock file or a daemon worker with MongoDB-backed serialization."

*(pause — 4 seconds of silence)*

> "That is the portability point."

*(pause — 3 seconds)*

> "An entity is not its transport."

*(pause — 3 seconds)*

> "The files on disk, the identity, the PRIMER, the trust bonds — those are the entity."

*(pause — 2 seconds)*

> "Everything else is plumbing."

*(pause — 4 seconds of silence)*

> "When the daemon is live and the worker system ships, the hook becomes a thin client."

*(pause — 3 seconds)*

> "Until then, the hook is a stopgap."

*(pause — 3 seconds)*

> "It works."

**[6 seconds of silence. Cut to black.]**

---

## Timing Map

| Segment | Clock | Content |
|---------|-------|---------|
| 1 | 0:00–1:30 | The promise — Day 37 quote on screen |
| 2 | 1:30–3:30 | What the daemon is — three services, single port, daemon src dir |
| 3 | 3:30–5:30 | Comparison table overlay — MONEY SHOT |
| 4 | 5:30–7:00 | `passenger.json` live — the registration card |
| 5 | 7:00–8:00 | Worker system — package exists, not yet wired |
| 6 | 8:00–8:45 | Dark Passenger extension — URL ingest demo |
| 7 | 8:45–10:30 | The Interface Survives — closing thesis |

---

## Delivery Notes

- **Tone:** This is an audit episode. Day 37 made a claim. Day 41 walks through the architecture to verify it. The architecture is largely built. The missing piece (worker system) is named directly. Measure every line — this is not a triumph lap. It is an honest accounting.
- **Comparison table (Segment 3):** This is the money shot. Every row must be read fully. Do not summarize. Each cell is a distinct claim. The viewer should be able to read along as you narrate. Hold the table through all six rows before dismissing.
- **`ls ~/.koad-io/daemon/src/` (Segment 2):** The point is that the daemon is real — it exists on disk, in the framework layer. Let the output render and hold. Do not rush past it.
- **`cat ~/.juno/passenger.json` (Segment 4):** Hold 5 full seconds before narrating. The viewer needs to read the actual file content. The narration should feel like annotation, not explanation.
- **Worker system (Segment 5):** Name the gap directly. "`ls ~/.koad-io/packages/workers/`" shows the package exists. The package does not run. Do not soften this. The gap is real. The next build item is named.
- **The Interface Survives (Segment 7):** This is the slowest segment in the video. The final eight beats — "Interactive invocation," "Task invocation," "PRIMER injection," "Lock semantics" — each gets a 2-second pause after. "The entity is not its transport" gets a 3-second pause before and after. "It works." is the last line. One beat of silence before the cut.
- **"It works." (Segment 7, closing line):** Deliver without inflection. Not triumph. Not reassurance. Statement. Then silence. Then black.
- **No backspace corrections on camera.** Retake immediately if a typo occurs on a path or command.
- **No live entity invocations.** The daemon directory, `passenger.json`, and the workers package are the evidence. The extension UI is a live connection — this is the only live system demo in the episode.
