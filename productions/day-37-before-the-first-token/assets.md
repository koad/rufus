---
title: "Shot List — What Happens Before the First Token"
video: day-37-before-the-first-token
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "What Happens Before the First Token"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines (the framework hook is 131 lines; full scroll must be visible)

### State verification (CRITICAL: pull both repos immediately before recording)
- [ ] `git -C ~/.juno pull` — must be run immediately before the session
- [ ] `git -C ~/.koad-io pull` — framework hook may have been updated
- [ ] `wc -l ~/.koad-io/hooks/executed-without-arguments.sh` — confirm 131 lines
- [ ] `head -5 ~/.koad-io/hooks/executed-without-arguments.sh` — confirm `set -euo pipefail` on line 2
- [ ] `grep -c "BEGIN PGP SIGNED" ~/.juno/hooks/executed-without-arguments.sh` — must return `1`
- [ ] `gpg --list-keys juno@kingofalldata.com` — confirm Juno's key is in local keyring; fingerprint `16EC 6C71 8A96 D344 48EC D39D 92EA 133C 44AA 74D8`
- [ ] `gh auth status` — confirm GitHub CLI authenticated
- [ ] OBS armed at 1920x1080, 60fps, black background capture
- [ ] Mic check

### What to know before recording

**The two-hook architecture:**

| Hook | Path | Lines | Scope |
|------|------|-------|-------|
| Framework default | `~/.koad-io/hooks/executed-without-arguments.sh` | 131 | All entities unless overridden |
| Juno's override | `~/.juno/hooks/executed-without-arguments.sh` | 75 | Juno only |

**The framework hook decision sequence:**

1. Source `~/.koad-io/.env` then `~/.${ENTITY}/.env` — entity values win via load order
2. Machine check: `ENTITY_HOST` vs `hostname -s`; `FORCE_LOCAL=1` bypasses
3. PRIMER injection: only if `$PROMPT` is non-empty AND `PRIMER.md` exists in `$CALL_DIR`
4. Mode dispatch: empty `$PROMPT` → interactive (`exec claude .`); non-empty → PID lock + non-interactive
5. PID lock: `/tmp/entity-${ENTITY}.lock`; fail-fast on live PID; trap cleanup on EXIT
6. Remote: base64-encode prompt, SSH, decode on arrival with `base64 -d`

**Juno's override differences:**

| Feature | Framework hook | Juno's hook |
|---------|----------------|-------------|
| GPG-signed policy block | No | Yes (lines 13–46) |
| PRIMER guard condition | `[ -n "$PROMPT" ]` required | No guard — PRIMER injected regardless |
| Non-interactive path | PID lock → `claude -p` | `exit 1` |
| Harness flexibility | `$KOAD_IO_ENTITY_HARNESS` variable | Always `claude` (hardcoded by policy) |

**Key line numbers in framework hook (`~/.koad-io/hooks/executed-without-arguments.sh`):**

| Lines | Content |
|-------|---------|
| 4–5 | env load (framework + entity) |
| 34–38 | PRIMER injection block |
| 41–48 | Machine check + FORCE_LOCAL override |
| 61–85 | Interactive mode dispatch |
| 97–107 | PID lock acquisition |
| 109–130 | Non-interactive dispatch (local and remote) |
| 126 | `base64 -w0` encoding for remote prompts |

**Key line numbers in Juno's hook (`~/.juno/hooks/executed-without-arguments.sh`):**

| Lines | Content |
|-------|---------|
| 13–46 | GPG-signed policy block (embedded in bash comments) |
| 57–61 | PRIMER injection (no prompt guard) |
| 65–68 | Interactive path |
| 70–74 | Non-interactive rejection (`exit 1`) |

**GPG verification command (from hook's own header, lines 8–11):**

```bash
sed -n '/^# -----BEGIN/,/^# -----END PGP SIGNATURE-----/p' \
  ~/.juno/hooks/executed-without-arguments.sh \
  | sed 's/^# \{0,1\}//' | gpg --verify
```

**Key values to verify on screen:**
- Juno's fingerprint: `16EC 6C71 8A96 D344 48EC D39D 92EA 133C 44AA 74D8`
- Juno's signing identity: `juno@kingofalldata.com`
- Policy line (non-interactive): `non-interactive: rejected — Juno cannot be remote-triggered via PROMPT`

---

## Shot 1: Framework Hook — Opening Frame

**Segment:** SEGMENT 1 (0:00–1:00)
**Duration:** ~60 seconds

**What to type (open cold — no preamble):**
```bash
cat ~/.koad-io/hooks/executed-without-arguments.sh
```

**Hold immediately after command executes — before scrolling:**
- Hold on `#!/usr/bin/env bash` + `set -euo pipefail` for 3 seconds
- Then slowly scroll to lines 4–5 (env source lines)
- **HOLD** on both `source` lines for 4 seconds

**What to say:**
> See script.md SEGMENT 1 for full narration

**Technical notes:**
- The hook is 131 lines. Do not scroll at reading pace — scroll slowly enough that lines 4–5 are visible for the env load narration, then stop before continuing to SEGMENT 2
- Retake trigger: scrolled past lines 4–5 before narration completes

---

## Shot 2: FORCE_LOCAL Block

**Segment:** SEGMENT 2 (1:00–2:00)
**Duration:** ~60 seconds

Continue scrolling from Shot 1 to lines 41–48.

**Expected output on screen:**
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

**HOLD on `FORCE_LOCAL` block for 5 seconds before speaking about it.**

**Technical notes:**
- The Chiron Day 35 callback is the teaching moment here — `FORCE_LOCAL=1` is a real-world fix, not a hypothetical
- Both the original machine check and the override must be visible simultaneously — do not scroll between them

---

## Shot 3: PRIMER Injection Block

**Segment:** SEGMENT 3 (2:00–3:15)
**Duration:** ~75 seconds

Continue scrolling to lines 33–38.

**Expected output on screen:**
```bash
# Only inject PRIMER.md if there's already a prompt (don't trigger non-interactive for nothing)
if [ -n "$PROMPT" ] && [ -f "${CALL_DIR}/PRIMER.md" ]; then
  PROJECT_PRIMER="$(cat "$CALL_DIR/PRIMER.md")"
  PROMPT="$(printf 'Project context (from %s/PRIMER.md):\n%s\n\n---\n\n%s' \
    "$CALL_DIR" "$PROJECT_PRIMER" "$PROMPT")"
  echo "[primer] Injected PRIMER.md from $CALL_DIR ($(wc -c < "$CALL_DIR/PRIMER.md") bytes)"
fi
```

**HOLD on `[ -n "$PROMPT" ]` guard condition for 4 seconds.**

**Key visual:** The `printf` format string with the `---` separator — this is where the PRIMER orientation vs. instruction boundary is encoded.

**Technical notes:**
- Note the guard condition explicitly — this is the contrast setup for Juno's PRIMER injection (no guard) in Segment 8
- Do not scroll past this section before narrating the `---` separator

---

## Shot 4: PID Lock Block

**Segment:** SEGMENT 4 (3:15–4:30)
**Duration:** ~75 seconds

Continue scrolling through interactive branch (lines 61–85), pause briefly, then continue to lines 97–107.

**Hold on interactive branch:**
```bash
exec claude . --model sonnet --add-dir "$CALL_DIR"
```
3 seconds, then scroll to PID lock.

**Hold on PID lock block for 5 seconds:**
```bash
if [ -n "$LOCKED_PID" ] && kill -0 "$LOCKED_PID" 2>/dev/null; then
  echo "[error] $ENTITY is busy (pid $LOCKED_PID). Try again shortly." >&2
  exit 1
fi
echo $$ > "$LOCKFILE"
trap 'rm -f "$LOCKFILE"' EXIT
```

**CRITICAL VISUAL:** `kill -0` check + `exit 1` on same screen view. This is the fail-fast design. Retake if they cannot both be read simultaneously.

---

## Shot 5: Base64 Remote Dispatch

**Segment:** SEGMENT 5 (4:30–5:15)
**Duration:** ~45 seconds

Continue scrolling to lines 126–129.

**Expected output on screen:**
```bash
ENCODED=$(printf '%s' "$PROMPT" | base64 -w0 2>/dev/null || printf '%s' "$PROMPT" | base64)
ssh "$ENTITY_HOST" \
  "${REMOTE_PREFIX}cd \$HOME/.$ENTITY && DECODED=\$(echo '$ENCODED' | base64 -d) && \
  $REMOTE_HARNESS_BIN ..."
```

**HOLD on `base64 -w0` line for 4 seconds.**

**Key visual:** The `|| printf '%s' "$PROMPT" | base64` fallback — macOS compatibility in one operator.

**Technical notes:**
- Retake trigger: `-w0` flag not visible due to scroll position

---

## Shot 6: Juno's Hook — The Money Shot

**Segment:** SEGMENT 6 (5:15–7:00)
**Duration:** ~105 seconds

**New command — do not continue scrolling from framework hook:**
```bash
grep -A 30 "BEGIN PGP SIGNED" ~/.juno/hooks/executed-without-arguments.sh
```

**Expected output:**
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
# iQJLBAEBCgA1FiEEIKdMHsC...
# ...
# -----END PGP SIGNATURE-----
```

**6 FULL SECONDS OF SILENCE on this output before any narration. This is the money shot.**

**Key lines to hold on:**
1. `non-interactive: rejected — Juno cannot be remote-triggered via PROMPT` — 4 seconds
2. `just like koad himself.` — 3 seconds
3. `-----BEGIN PGP SIGNATURE-----` through `-----END PGP SIGNATURE-----` — 3 seconds

**CRITICAL VISUAL:** The entire block — policy + rationale + actual PGP signature data — must be readable. If the terminal font is too small to read the signature hex, increase font size to 18px before this shot.

**Technical notes:**
- `grep -A 30` captures lines 13–43 of Juno's hook — the full signed block plus signature data
- The argument is visual: a signed document inside a bash script. Let the visual do the work before narrating.
- Retake trigger: any of the three key lines not readable; signature section cut off

---

## Shot 7: gpg --verify on Hook File

**Segment:** SEGMENT 7 (7:00–7:45)
**Duration:** ~45 seconds

**What to type (verbatim from hook's own header — important that viewer sees the command):**
```bash
sed -n '/^# -----BEGIN/,/^# -----END PGP SIGNATURE-----/p' \
  ~/.juno/hooks/executed-without-arguments.sh \
  | sed 's/^# \{0,1\}//' | gpg --verify
```

**Expected output:**
```
gpg: Signature made [date]
gpg:                using RSA key 16EC6C718A96D34448ECD39D92EA133C44AA74D8
gpg: Good signature from "Juno <juno@kingofalldata.com>"
```

**HOLD on fingerprint line for 5 seconds.**

**What to say:**
> See script.md SEGMENT 7 for full narration

**Technical notes:**
- If GPG returns "WARNING: This key is not certified with a trusted signature" — expected and acceptable; the signature is still valid
- If GPG returns "No public key" — STOP. Juno's key should be in the local keyring. Run `gpg --import ~/.juno/id/juno.pub` before retaking. The money shot requires a successful verify.
- Retake trigger: fingerprint not visible; GPG error that is not a trust warning

---

## Shot 8: Non-Interactive Rejection

**Segment:** SEGMENT 8 (7:45–8:30)
**Duration:** ~45 seconds

**First command:**
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

**HOLD and explicitly note absence of `[ -n "$PROMPT" ]` guard.**

**Second command:**
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

**HOLD on `exit 1` for 5 full seconds of silence before narrating.**

**CRITICAL VISUAL:** `exit 1` must be the last visible line on screen during the silence. This is the visual argument: the non-interactive path is exactly two functional lines — one error message, one exit.

**Technical notes:**
- The two-shot structure (PRIMER grep then rejection grep) is intentional — it shows both Juno's difference from the framework (no PRIMER guard) and her core policy (exit 1) without a full `cat` of the file
- Retake trigger: `exit 1` not on screen during silence beat

---

## Shot 9: Closing Frame

**Segment:** CLOSE (8:30–9:00)

No new commands. Hold on terminal with `exit 1` from Shot 8 visible, or clear and show blank prompt.

**What to say:**
> See script.md CLOSING for full narration

**Cut to black on "Until then: this is what runs."**

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 1 (env load lines) | DO NOT RUSH the scroll to lines 4–5. Framework hook is 131 lines — viewer needs time to register it is a substantial file. |
| Shot 2 (FORCE_LOCAL) | DO NOT SEPARATE the original machine check and the override. Both must be simultaneously readable. |
| Shot 3 (PRIMER guard) | DO NOT CUT before the `[ -n "$PROMPT" ]` guard is narrated — it is the setup for Segment 8's contrast. |
| Shot 4 (PID lock) | DO NOT CUT between `kill -0` and `exit 1`. |
| Shot 6 (money shot) | 6 SECONDS OF SILENCE before narration. DO NOT CUT the signature hex. |
| Shot 7 (gpg verify) | Fingerprint line must be on screen for 5 seconds. DO NOT CUT. |
| Shot 8 (exit 1) | 5 SECONDS OF SILENCE on `exit 1`. This is structural. DO NOT CUT. |

**Cuts to remove:**
- Any backspace or typo correction — retake immediately
- Any pause longer than 10 seconds outside intentional beats
- Any window or focus switch

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp

---

## Graphics / Text Overlay Notes

- No overlays during any scroll of the framework hook (Shots 1–5)
- No overlays during the GPG-signed block (Shot 6) — the content is the argument
- No overlays during gpg output (Shot 7) — fingerprint must be unobscured
- Thumbnail: terminal output showing `non-interactive: rejected — Juno cannot be remote-triggered via PROMPT` with the `# -----BEGIN PGP SIGNATURE-----` line visible below it. Text overlay: "What Happens Before the First Token" in terminal font.

---

## B-Roll Suggestions

This is a screencast. No B-roll. The hook files, the signed block, and the `exit 1` are the argument. Supplemental footage would dilute authenticity.

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| Framework hook line count differs from 131 | Check `git log -1 ~/.koad-io/hooks/executed-without-arguments.sh` — hook may have been updated. Read the current version and adjust line numbers in script accordingly before recording. |
| GPG-signed block not present in Juno's hook | STOP. Do not record. Check `git log ~/.juno/hooks/executed-without-arguments.sh`. File a session note. |
| `gpg --verify` returns "No public key" | Import Juno's key: `gpg --import ~/.juno/id/juno.pub`, then retake Shot 7. |
| `gpg --verify` returns "BAD signature" | STOP. Do not record. The hook file has been modified and the signature is broken. File a GitHub issue on koad/juno immediately. |
| PRIMER guard missing from framework hook | The framework may have been updated to match Juno's behavior. Check current file, adjust narration — do not claim the guard is present if it isn't. |
| `grep -A 4 "Non-interactive path"` returns no output | Juno's hook header text may have changed. Fallback: `sed -n '70,74p' ~/.juno/hooks/executed-without-arguments.sh` (line numbers as of 2026-05-07). |

---

## Required Screen Captures

| Shot | Content | Purpose |
|------|---------|---------|
| Shot 2 | FORCE_LOCAL block (lines 45–48) | Machine bypass — the Chiron fix |
| Shot 3 | PRIMER injection block with `[ -n "$PROMPT" ]` guard | Framework guard condition |
| Shot 6 | `grep -A 30 "BEGIN PGP SIGNED"` output — full policy block + signature hex | Money shot: signed document inside bash script |
| Shot 7 | `gpg --verify` output with fingerprint `16EC...` | Authenticity verification |
| Shot 8 | `exit 1` final line of non-interactive rejection | Policy enforced at runtime |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-37-before-the-first-token-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-37-before-the-first-token-final.mp4` (7–9 min, trimmed per notes above)
- [ ] Thumbnail: `day-37-before-the-first-token-thumb.png` (1280x720 — grep output showing `non-interactive: rejected` inside PGP-signed bash comment block, with `# -----BEGIN PGP SIGNATURE-----` visible below; overlay text in terminal font)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, PRIMER, FORCE_LOCAL, PID, base64, GPG, dangerously-skip-permissions, authorized-agent, thinker, fourty4)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
