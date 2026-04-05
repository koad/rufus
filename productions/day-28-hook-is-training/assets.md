---
title: "Shot List — The Hook Is the Training"
video: day-28-hook-is-training
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "The Hook Is the Training"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines

### State verification
- [ ] `cd ~/.juno && git pull` — confirm current
- [ ] `cd ~/.koad-io && git pull` — confirm current
- [ ] `ls ~/.sibyl/hooks/` — confirm Sibyl's hooks directory exists and has files
- [ ] `gpg --list-keys juno@kingofalldata.com` — confirm Juno's GPG key is imported
- [ ] `gpg --verify ~/.juno/hooks/executed-without-arguments.sh` — **must return "Good signature" before you record**
- [ ] `head -30 ~/.juno/hooks/executed-without-arguments.sh` — confirm signed policy block is visible
- [ ] OBS armed at 1920x1080, 60fps, black background capture
- [ ] Mic check

---

## Shot 1: Empty Terminal — Entity Directory

**Segment:** SEGMENT 1 (0:00–0:15)
**Duration:** ~15 seconds

**What the screen shows:**
- Terminal. Prompt only. Nothing else.

**What to type:** Nothing yet.

**What to say:**
> "There are two directories in every koad:io entity. They do opposite
> things. Let me show you."

**Technical notes:**
- Pause 2–3 seconds after opening before speaking — gives editor a clean cut point.

---

## Shot 2: ls ~/.juno/

**Segment:** SEGMENT 1 (0:15–0:45)
**Duration:** ~30 seconds

**What to type:**
```
ls ~/.juno/
```

**Expected output:**
```
CLAUDE.md  GOVERNANCE.md  OPERATIONS.md  README.md
commands   hooks          id             memories
opencode   trust          ...
```

**What to say:**
> "You can see commands/ and hooks/. Commands is for the operator to reach in
> — you type juno commit self and the framework finds that command. Hooks is
> for the system to call out — when a condition is met, when an orchestration
> signal arrives, the hook fires. The operator didn't decide. The operation did."

**Technical notes:**
- Pause on the listing for 2–3 seconds before speaking.

---

## Shot 3: Cat the Hook

**Segment:** SEGMENT 2 (0:45–2:00)
**Duration:** ~75 seconds

**What to type:**
```
cat ~/.juno/hooks/executed-without-arguments.sh
```

**Expected output:** Full hook script. Key blocks to identify on-screen as they scroll:
1. LOCKFILE / PID lock section
2. PROMPT detection and two-branch conditional
3. Non-interactive path rejection: `echo "juno: remote prompt rejected..."` + `exit 1`

**What to say over each block:**

*On LOCKFILE block:*
> "PID lock. If Juno is already running, she is busy. You get a message and
> the invocation exits."

*On PROMPT detection:*
> "If PROMPT is set — single-shot mode. If nothing is set — interactive
> session. One hook, two modes."

*On the non-interactive rejection:*
> "This is the governance decision. Juno cannot be remote-triggered via a
> prompt. That path exits with an error. File a GitHub issue instead. The
> rule is in the code that runs."

**Technical notes:**
- Do NOT cut the scroll. Full file must display.
- Pause briefly on each key block before speaking about it — viewer reads, then you explain.
- Retake trigger: any typo during the cat command.

---

## Shot 4: GPG Verify the Policy Block

**Segment:** SEGMENT 3 (2:00–3:15)
**Duration:** ~75 seconds

**What to type (two commands):**

```
sed -n '/^# -----BEGIN/,/^# -----END PGP SIGNATURE-----/p' \
  ~/.juno/hooks/executed-without-arguments.sh \
  | sed 's/^# \{0,1\}//' | gpg --verify
```

**Expected output:**
```
gpg: Signature made ...
gpg: using ED25519 key ...
gpg: Good signature from "Juno <juno@kingofalldata.com>"
```

**"Good signature from Juno" is the money shot. Hold on it.**

**What to say after output appears:**

*(on "Good signature" — pause 2 seconds, then:)*
> "Good signature from Juno."

*(pause)*

> "There is a GPG-signed policy block embedded in a bash comment at the top
> of this hook. It names the entity, the file, the date, and the policy —
> interactive sessions allowed, non-interactive rejected, notification via
> GitHub Issues only. Every field is signed. Change any line — the signature
> breaks."

**Technical notes:**
- Accept natural GPG latency — do NOT cut the wait.
- If GPG returns anything other than "Good signature" — **STOP**. Do not proceed. Fix the key import or verify step in a separate terminal. Only record when it passes.
- This is the most important technical moment in the video. Do not rush past it.

---

## Shot 5: Show the Policy Block Inline

**Segment:** SEGMENT 3 (continued)
**Duration:** ~30 seconds

**What to type:**
```
head -30 ~/.juno/hooks/executed-without-arguments.sh
```

**Expected output:** The signed policy block as bash comments — entity, file, date, policy fields, rationale, PGP signature.

**What to say:**
> "This is a governance document. The behavior of the hook is a direct
> expression of the trust bond above it — koad authorized Juno as an agent,
> no entity may drive Juno via prompt injection. That decision is
> cryptographically attributed and enforced at runtime."

**Technical notes:**
- Let the block display for 3 seconds before speaking.
- The signed comment block should be clearly visible in the frame.

---

## Shot 6: Sibyl's Hooks Directory

**Segment:** SEGMENT 4 (3:15–4:15)
**Duration:** ~30 seconds

**What to type:**
```
ls ~/.sibyl/hooks/
```

**Expected output:** Sibyl's hook files — competitive-analysis, market-signal-research, technical-feasibility, etc.

**What to say:**
> "Sibyl is a research entity. Her hooks enumerate what she is: competitive
> analysis, market signal research, technical feasibility, audience profiling.
> When you enumerate the hooks, you enumerate the entity."

*(pause)*

> "The daemon knows which entity to dispatch for which event because it reads
> this directory. An operator who opens this directory understands what
> Sibyl is *for* — not what she might be prompted to do, but what she was
> built to do."

**Technical notes:**
- If `~/.sibyl/hooks/` does not exist or is empty: reschedule this video. The shot is load-bearing — if Sibyl's hooks can't be shown, the capability argument lacks visual evidence.
- Short pause after listing appears before speaking.

---

## Shot 7: The Close — ls ~/.juno/hooks/ Again

**Segment:** SEGMENT 5 (4:15–5:00)
**Duration:** ~45 seconds

**What to type:**
```
ls ~/.juno/hooks/
```

**Expected output:** Juno's hooks directory listing.

**What to say — slowest pacing in the video:**

> "The hook is not a wrapper."

*(pause — 2 seconds)*

> "A wrapper calls a model with a prompt. The hook carries the accumulated
> behavioral specification that makes each invocation consistent."

*(pause)*

> "The training, in the operational sense, is on the filesystem."

*(pause)*

> "If you want to understand a koad:io entity, don't read its README."

*(pause)*

> "Read its hooks."

*(pause — let it land.)*

**Technical notes:**
- Slowest pacing in the video.
- Each sentence = one breath, one pause. Do not compress.
- Editor: do NOT cut these pauses. They are structural beats.

---

## Shot 8: Fade / Cut to Black

**Duration:** 2–3 seconds

- No music
- Simple cut or 1-second fade
- Optional: hold on the hooks listing for 1 extra second before fade

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 3 (cat hook) | Do NOT cut. Full scroll is load-bearing. |
| Shot 4 (gpg verify) | Accept natural latency. Do NOT cut the wait. "Good signature" must be on screen. |
| Shot 5 (head -30) | Hold on signed block for 3s before VO. |
| Shot 6 (Sibyl hooks) | Short pause before VO. Do not rush. |
| Shot 7 (close) | Do NOT cut pauses. Intentional beats throughout. |

**Cuts to remove:**
- Any backspace or typo correction (retake if > 1 backspace)
- Any pause > 8 seconds outside of intentional beats in Shot 7
- Any window or focus switch

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `gpg --verify` returns error or no signature | STOP. Fix key import. Do NOT record until it passes. |
| `~/.sibyl/hooks/` does not exist | STOP. Reschedule. Shots 6 requires real files. |
| `cat` hook fails or hook missing | Kill recording. Fix entity state. |
| Scrollback cuts off during Shot 3 | Kill recording. Increase scrollback buffer. Restart from Shot 1. |
| Take goes > 6 minutes | Tighten Shot 6 VO — let the ls listing carry more weight, reduce commentary. |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-28-hook-is-training-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-28-hook-is-training-final.mp4` (4–5 min, trimmed per notes above)
- [ ] Thumbnail: `day-28-hook-is-training-thumb.png` (1280x720 — "Good signature" frame from Shot 4)
- [ ] Captions: auto-generated + manually reviewed
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
