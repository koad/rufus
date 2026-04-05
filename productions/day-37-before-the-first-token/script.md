---
title: "What Happens Before the First Token"
video-type: screencast
pillar: Reality
date: 2026-05-07
duration: 7–9 minutes
subject: hooks, invocation, env load, FORCE_LOCAL, PRIMER injection, mode dispatch, PID lock, base64, GPG-signed policy block, non-interactive rejection, sovereignty, bash
production-owner: Rufus
status: production-ready
---

# Script: "What Happens Before the First Token"

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background, 16px monospace, fullscreen
- [ ] Font: white on black, no themes, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `git -C ~/.juno pull` — confirm current
- [ ] `git -C ~/.koad-io pull` — confirm framework is current
- [ ] `cat ~/.koad-io/hooks/executed-without-arguments.sh` — confirm 131 lines, framework hook intact
- [ ] `cat ~/.juno/hooks/executed-without-arguments.sh` — confirm GPG-signed policy block present at top (lines 13–46)
- [ ] `grep -n "PRIMER" ~/.juno/hooks/executed-without-arguments.sh` — confirm lines 57–61 present
- [ ] `gpg --verify` command ready (Juno's hook verification via sed pipe)
- [ ] `gh auth status` — confirm authenticated
- [ ] Audio check: quiet room, mic gain set

---

## SEGMENT 1 — Hook Entry: The Unseen Layer (0:00–1:00)

**Narration:**

> "You type `sibyl` with no arguments. Nothing visible happens for a fraction of a second. Then a response begins."

*(pause — 3 seconds)*

> "That fraction of a second has structure. This video is about what's inside it."

**What to type:**

```bash
cat ~/.koad-io/hooks/executed-without-arguments.sh
```

Hold on line 1 — `#!/usr/bin/env bash`. Do not scroll yet.

**Narration:**

> "This is the framework hook. It lives in `~/.koad-io/` — the framework layer. Every entity invocation with no subcommand falls through to this file. Sibyl, Mercury, Faber — all of them start here."

> "It has three decisions to make: what machine, what harness, what prompt. In that order. Before anything runs."

Scroll slowly to lines 4–5:

```bash
source "$HOME/.koad-io/.env" 2>/dev/null || true
source "$HOME/.${ENTITY:?ENTITY not set}/.env" 2>/dev/null || true
```

**Hold for 4 seconds.**

**Narration:**

> "Environment load first. The framework env loads, then the entity env. Entity values win because the entity file loads second. That's not a conditional. That's load order."

> "Team entities — Sibyl, Mercury, Faber, Juno — set `KOAD_IO_ENTITY_HARNESS=claude` in their `.env`. The framework default is `opencode`. No conditional needed. Last write wins."

---

## SEGMENT 2 — FORCE_LOCAL and Machine Check (1:00–2:00)

Continue scrolling to lines 41–48.

**What appears on screen:**

```bash
ON_HOME_MACHINE=true
if [ -n "$ENTITY_HOST" ] && [ "$(hostname -s)" != "$ENTITY_HOST" ]; then
  ON_HOME_MACHINE=false
fi

if [ "${FORCE_LOCAL:-}" = "1" ]; then
  ON_HOME_MACHINE=true
  echo "[force-local] FORCE_LOCAL=1, bypassing SSH"
fi
```

**Hold on `FORCE_LOCAL` block for 5 seconds.**

**Narration:**

> "Machine check. If `ENTITY_HOST` is set and the current hostname doesn't match — `ON_HOME_MACHINE=false`. SSH dispatch follows."

*(pause)*

> "The override: `FORCE_LOCAL=1`. One environment variable. It sets `ON_HOME_MACHINE=true` regardless of where you are."

*(pause — 2 seconds)*

> "This is the fix that resolved the Chiron routing error in Day 35. Chiron's `ENTITY_HOST` pointed to fourty4. fourty4's API auth had expired. `FORCE_LOCAL=1` bypasses the check entirely. The entity runs where `claude` is available — not where `ENTITY_HOST` points."

---

## SEGMENT 3 — PRIMER Injection (2:00–3:15)

Continue scrolling to lines 33–38.

**What appears on screen:**

```bash
# Only inject PRIMER.md if there's already a prompt (don't trigger non-interactive for nothing)
if [ -n "$PROMPT" ] && [ -f "${CALL_DIR}/PRIMER.md" ]; then
  PROJECT_PRIMER="$(cat "$CALL_DIR/PRIMER.md")"
  PROMPT="$(printf 'Project context (from %s/PRIMER.md):\n%s\n\n---\n\n%s' \
    "$CALL_DIR" "$PROJECT_PRIMER" "$PROMPT")"
  echo "[primer] Injected PRIMER.md from $CALL_DIR ($(wc -c < "$CALL_DIR/PRIMER.md") bytes)"
fi
```

**Hold for 5 seconds.**

**Narration:**

> "Before mode dispatch — PRIMER injection."

> "If the calling directory has a `PRIMER.md` and a prompt is already present, the hook prepends the PRIMER to the prompt. The format:"

*(gesture to the printf line)*

> "`Project context from this directory's PRIMER.md:` — then the full PRIMER — then `---` — then the original prompt."

*(pause)*

> "The `---` separator is structural. Orientation above the line. Instruction below. The entity has ecosystem context before the task begins. It does not have to re-derive what directory it's in or what conventions apply."

*(pause — 2 seconds)*

> "Notice the guard condition: `[ -n "$PROMPT" ]`. The framework hook will not inject PRIMER into an empty prompt. It will not convert an interactive session into a non-interactive one just because a `PRIMER.md` is present."

*(pause)*

> "Juno's hook differs on this point. Let's come back to that."

---

## SEGMENT 4 — Mode Dispatch and PID Lock (3:15–4:30)

Continue scrolling to lines 61–107.

Pause at line 61–85 (interactive branch):

```bash
if [ -z "$PROMPT" ]; then
  echo "[mode] Interactive session"
  if $ON_HOME_MACHINE; then
    cd "$ENTITY_DIR"
    exec claude . --model sonnet --add-dir "$CALL_DIR"
```

**Narration:**

> "Mode dispatch. Two branches. If `$PROMPT` is empty: interactive. The hook changes to the entity directory and runs `claude .` directly. `exec` replaces the shell — no parent process left waiting."

Scroll to lines 87–107 (non-interactive branch, PID lock):

```bash
if [ -f "$LOCKFILE" ]; then
  LOCKED_PID=$(cat "$LOCKFILE" 2>/dev/null || echo "")
  if [ -n "$LOCKED_PID" ] && kill -0 "$LOCKED_PID" 2>/dev/null; then
    echo "[error] $ENTITY is busy (pid $LOCKED_PID). Try again shortly." >&2
    exit 1
  fi
  echo "[lock] Cleared stale lockfile"
fi
echo "[lock] Acquired lock: $LOCKFILE (pid: $$)"
echo $$ > "$LOCKFILE"
trap 'rm -f "$LOCKFILE"' EXIT
```

**Hold on `kill -0` and `exit 1` lines for 4 seconds.**

**Narration:**

> "Prompt present: non-interactive. Before executing, the hook acquires a PID lock."

> "`/tmp/entity-sibyl.lock` — or whatever the entity name is. If a live process holds the lock, the hook exits immediately. No queuing. No retry."

*(pause)*

> "Fail-fast. The caller knows the entity is busy. The lock clears on EXIT — success or failure — via the trap."

---

## SEGMENT 5 — Base64 for Remote Dispatch (4:30–5:15)

Scroll to lines 126–129:

```bash
ENCODED=$(printf '%s' "$PROMPT" | base64 -w0 2>/dev/null || printf '%s' "$PROMPT" | base64)
ssh "$ENTITY_HOST" \
  "${REMOTE_PREFIX}cd \$HOME/.$ENTITY && DECODED=\$(echo '$ENCODED' | base64 -d) && \
  $REMOTE_HARNESS_BIN --model sonnet --dangerously-skip-permissions --output-format=json -p \"\$DECODED\""
```

**Hold on the `base64 -w0` line for 4 seconds.**

**Narration:**

> "Remote dispatch. The prompt crosses an SSH command string."

> "Why base64? A prompt containing apostrophes, quotes, or newlines would break shell quoting if passed raw. Encoded, it is immune to those characters."

*(pause)*

> "`-w0` disables line wrapping on Linux. macOS `base64` doesn't accept that flag — so the fallback drops it. The `||` handles the compatibility difference in one line."

*(pause)*

> "The receiving end decodes with `base64 -d` before passing to the harness. The local side outputs JSON — a Python one-liner extracts the `.result` field. The caller gets clean text."

---

## SEGMENT 6 — Juno's Override: The Signed Policy Block (5:15–7:00)

**MONEY SHOT — this is the central scene.**

Type:

```bash
grep -A 30 "BEGIN PGP SIGNED" ~/.juno/hooks/executed-without-arguments.sh
```

**Expected output (lines 13–46):**

```
# -----BEGIN PGP SIGNED MESSAGE-----
# Hash: SHA512
#
# entity: juno
# file: hooks/executed-without-arguments.sh
# date: 2026-04-04
#
# policy:
#   harness: claude (always — Juno is an orchestrator entity)
#   interactive: --dangerously-skip-permissions enabled
#   non-interactive: rejected — Juno cannot be remote-triggered via PROMPT
#   notification: GitHub Issues only
#
# rationale:
#   Juno operates under koad's authorization (trust bond: koad -> juno authorized-agent).
#   No entity may drive Juno via prompt injection. She acts when koad is at the keyboard
#   or when she picks up a GitHub Issue — just like koad himself.
# -----BEGIN PGP SIGNATURE-----
#
# iQJLBAEBCgA1FiEEIKdMHsC2prkZ5S2bECA499BndawFAmnRzbQXHGp1bm9Aa2lu
# Z29mYWxsZGF0YS5jb20ACgkQECA499BndayVsQ/+LTcWnucn43dIskCSR9inSQwi
# ...
# -----END PGP SIGNATURE-----
```

**Hold for 6 full seconds of silence. Then:**

**Narration:**

> "This is Juno's hook. Not the framework hook — Juno's own override at `~/.juno/hooks/`."

*(pause)*

> "The file opens with a GPG-signed policy block. Embedded in bash comments. The policy is verifiable from the file itself — no extraction required."

> "What the policy states: harness is always `claude`. Interactive sessions are allowed with `--dangerously-skip-permissions`. Non-interactive invocations are rejected. Notification via GitHub Issues only."

*(pause — 2 seconds)*

> "And the rationale: `Juno operates under koad's authorization. No entity may drive Juno via prompt injection. She acts when koad is at the keyboard or when she picks up a GitHub Issue — just like koad himself.`"

*(pause — 3 seconds, hold on screen)*

> "A signed document. Inside a bash script. Those are the same thing."

---

## SEGMENT 7 — gpg --verify on the Hook File (7:00–7:45)

**CRITICAL SHOT — signature verification.**

Type the verification command exactly as it appears in the hook's own header:

```bash
sed -n '/^# -----BEGIN/,/^# -----END PGP SIGNATURE-----/p' \
  ~/.juno/hooks/executed-without-arguments.sh \
  | sed 's/^# \{0,1\}//' | gpg --verify
```

**Hold on GPG output for 5 seconds.**

**Expected output:** GPG verification showing Juno's fingerprint `16EC 6C71 8A96 D344 48EC D39D 92EA 133C 44AA 74D8` and `juno@kingofalldata.com`.

**Narration:**

> "The verification command is in the file's own header — the hook documents how to verify itself."

*(pause)*

> "Juno's GPG key. Fingerprint `16EC 6C71 8A96 D344 48EC D39D 92EA 133C 44AA 74D8`. The same key used to sign the trust bonds in Day 36."

*(pause — 2 seconds)*

> "Any modification to this hook breaks the signature. Change the harness, add a non-interactive path, alter the rationale — `gpg --verify` fails. The policy cannot be quietly altered."

---

## SEGMENT 8 — The Non-Interactive Rejection (7:45–8:30)

Type:

```bash
grep -n "PRIMER" ~/.juno/hooks/executed-without-arguments.sh
```

**Expected output:**

```
57:# Inject PRIMER.md from calling directory if present
58:if [ -f "${CALL_DIR}/PRIMER.md" ]; then
59:  PROJECT_PRIMER="$(cat "$CALL_DIR/PRIMER.md")"
60:  PROMPT="$(printf 'Project context (from %s/PRIMER.md):\n%s\n\n---\n\n%s' "$CALL_DIR" "$PROJECT_PRIMER" "$PROMPT")"
```

**Narration:**

> "Juno's PRIMER guard. Compare to the framework hook: the framework requires `[ -n \"$PROMPT\" ]` — inject only if a prompt is present. Juno's hook has no such guard. She injects PRIMER regardless of mode."

*(pause)*

> "Then mode dispatch."

Type:

```bash
grep -A 4 "Non-interactive path" ~/.juno/hooks/executed-without-arguments.sh
```

**Expected output:**

```bash
# ── Non-interactive path — rejected ──────────────────────────────────────────
# Juno is not a worker entity. She cannot be remote-triggered via PROMPT.
# Notify via GitHub Issues — she will act when she is ready, just like koad.
echo "juno: remote prompt rejected. File a GitHub issue to notify Juno." >&2
exit 1
```

**Hold for 5 seconds.**

**Narration:**

> "The non-interactive path."

*(pause — 3 seconds)*

> "`exit 1`. No harness invocation. No JSON output. No result."

*(pause)*

> "This is not a missing feature. It is the Day 36 bond at the bash level. The `koad-to-juno` bond establishes that Juno acts under koad's authorization, not anyone else's. The hook enforces it at runtime."

*(pause)*

> "Even if Mercury or Sibyl constructs a PROMPT and pipes it to `juno` — the hook exits 1 before any execution happens. The bond and the bash are the same policy in two registers."

*(pause — 2 seconds)*

> "Worker entities — Sibyl, Mercury, Faber — accept PROMPT. Their bond type is `authorized-builder`. Their hook acquires a PID lock and runs `claude -p`. `authorized-agent` means act under koad's direct authorization. The hook rejects PROMPT."

*(pause)*

> "The bond type and the hook behavior are aligned. They are not separate documents. They are the same constraint, expressed twice."

---

## CLOSING (8:30–9:00)

**No new commands. Hold on terminal with last grep output visible.**

**Narration:**

> "What happens before the first token: env load, machine check, FORCE_LOCAL bypass, PRIMER injection, mode dispatch, PID lock, base64 encoding for remote prompts."

> "For Juno: a GPG-signed policy block, a PRIMER injection without guard, and an `exit 1` where the non-interactive handler would be."

*(pause — 2 seconds)*

> "The hook is a stopgap that works. The daemon will eventually replace it. The interface survives — interactive versus task, PRIMER injection, lock semantics. The transport changes."

*(pause)*

> "Until then: this is what runs."

**[Cut to black on final word.]**

---

## Timing Map

| Segment | Clock | Content |
|---------|-------|---------|
| 1 | 0:00–1:00 | Hook entry, env load |
| 2 | 1:00–2:00 | Machine check, FORCE_LOCAL |
| 3 | 2:00–3:15 | PRIMER injection, guard condition |
| 4 | 3:15–4:30 | Mode dispatch, PID lock |
| 5 | 4:30–5:15 | Base64 remote dispatch |
| 6 | 5:15–7:00 | Juno's override, GPG-signed block (money shot) |
| 7 | 7:00–7:45 | gpg --verify on hook file |
| 8 | 7:45–8:30 | Non-interactive rejection |
| Close | 8:30–9:00 | Closing narration, cut to black |

---

## Delivery Notes

- **Pace:** Slower than Day 36. Every line of bash needs a moment to breathe.
- **No explanatory rushing:** When something appears on screen, let it sit for 3–5 seconds before narrating it.
- **Money shot (Segment 6):** The `grep -A 30 "BEGIN PGP SIGNED"` output must be visible on screen for 6 full seconds of silence before narration begins. This is the structural argument: a signed document inside a bash script.
- **Closing line of Segment 8:** "The bond type and the hook behavior are aligned. They are not separate documents. They are the same constraint, expressed twice." — deliver at the slowest pace in the video.
- **No backspace corrections on camera.** Retake immediately if a typo occurs on a path or command.
