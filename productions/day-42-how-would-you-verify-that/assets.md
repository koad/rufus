---
title: "How Would You Even Verify That?"
video-type: verification
date: 2026-05-12
production-owner: Rufus
status: production-ready
---

# Asset List: Day 42 — "How Would You Even Verify That?"

---

## Live Commands (in order of appearance)

### Segment 1 — The Question (0:00–1:30)

| Asset | Type | Notes |
|-------|------|-------|
| `grep "entity is not its transport" ~/.faber/posts/2026-05-11-the-hook-is-a-stopgap.md` | Live command | Pulls Day 41 closing line. File must be present on disk. |
| Comment block `# You wrote those files...` | Live terminal text | No execution. Typed live as visual punctuation. |

**Fallback — if Day 41 post file not present:**
Use the quote directly in narration without running the grep. The command can be shown typed but commented out: `# grep result omitted — file not on this machine`.

---

### Segment 2 — Layer One (1:30–4:30)

| Asset | Type | Timing | Notes |
|-------|------|--------|-------|
| `curl canon.koad.sh/juno.keys` | Live command + network call | ~1:40 | PGP key block renders on screen. Hold 6 seconds. |
| `curl canon.koad.sh/juno.keys \| gpg --import` | Live command + network call | ~2:10 | GPG import confirmation renders. Hold 5 seconds. |
| `git -C ~/.juno log --oneline -5` | Live command | ~2:45 | Commit list. Pick top hash for next command. |
| `git -C ~/.juno verify-commit HEAD` | Live command — FIRST MONEY SHOT | ~3:00 | GPG good-signature output + fingerprint. Hold 6 seconds on fingerprint. |

**Fallback — network down (canon.koad.sh unreachable):**

```bash
# Fallback: fetch from GitHub instead
curl https://raw.githubusercontent.com/koad/juno/main/id/juno.pub | gpg --import
```

State on camera: "canon.koad.sh appears to be unreachable. Here is the same key fetched from the GitHub repo. The point about independence from GitHub is temporarily compromised — the verification mechanism itself is identical."

**Fallback — `verify-commit` shows no signature:**
If the HEAD commit is unsigned (infrastructure issue), run against a known signed commit hash from the log. Prepare: `git -C ~/.juno log --show-signature -3` in pre-roll to confirm which commits are signed.

---

### Segment 3 — Layer Two (4:30–7:30)

| Asset | Type | Timing | Notes |
|-------|------|--------|-------|
| `ls ~/.juno/trust/bonds/` | Live command | ~4:40 | Shows both `.md` and `.md.asc` files. |
| `cat ~/.juno/trust/bonds/koad-to-juno.md` | Live command | ~4:55 | Full bond document renders. Scroll slowly. Hold 5 seconds at bottom. |
| `gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc` | Live command — MAIN MONEY SHOT | ~5:45 | GPG good-signature + koad fingerprint. Hold 8 seconds. |
| `curl canon.koad.sh/koad.keys \| gpg --import` | Live command + network call | ~6:15 | Imports koad's public key. |
| `gpg --fingerprint koad@koad.sh` | Live command | ~6:30 | Renders koad's fingerprint for cross-reference. Hold 6 seconds. |

**Key fingerprint for on-screen verification:**
`A07F 8CFE CBF6 B982 EEDA C4F3 62D5 C486 6C24 7E00`

This fingerprint appears in the bond document, the `--verify` output, and the `--fingerprint` output. All three should match. If all three are visible on screen simultaneously, the cross-reference is visually self-evident.

**Fallback — GPG verify returns bad signature or unknown key:**

Run:
```bash
gpg --verify --verbose ~/.juno/trust/bonds/koad-to-juno.md.asc
```

If the signature is genuinely invalid, stop the recording. Investigate before continuing. A bad signature here is an integrity incident, not a production inconvenience.

**Fallback — network down for koad.keys fetch:**

```bash
# Fallback: fetch from GitHub
curl https://raw.githubusercontent.com/koad/koad.sh/main/id/koad.pub | gpg --import
```

State on camera as with Segment 2 fallback.

---

### Segment 4 — Layer Three (7:30–9:00)

| Asset | Type | Timing | Notes |
|-------|------|--------|-------|
| `# When Phase 2B ships:` comment block | Live terminal text | ~7:40 | Not executed. Visual indicator of unshipped state. |
| `gpg --verify alice-level-3-certificate.md.asc` | Typed, NOT executed | ~7:50 | The file does not exist yet. Show the command. State this directly. |

**No fallback needed.** The non-execution is deliberate and stated on camera. The gap is the content.

---

### Segment 5 — Limits of the Chain (9:00–10:30)

| Asset | Type | Timing | Notes |
|-------|------|--------|-------|
| Keybase profile — koad (browser, visible) | Browser window | ~9:30 | koad's Keybase profile open and legible. Shows GitHub + Twitter cross-proofs. |
| Blank terminal | Visual anchor | — | No commands run. Terminal visible but empty throughout this segment. |

**Preparation:**
- Load `keybase.io/koad` in browser before recording. Confirm GitHub and Twitter cross-links are visible in the Keybase proof list.
- Do not display in OBS as a separate capture. Switch to browser briefly when Keybase is mentioned, then return to terminal for the closing segment.

**Fallback — Keybase profile unavailable:**
Narrate the cross-linking mechanism without the visual. The description of the proof structure stands on its own.

---

### Segment 6 — Closing Command Block (10:30–12:00)

| Asset | Type | Timing | Notes |
|-------|------|--------|-------|
| Full 4-command summary block | Typed live, NOT executed | ~10:35–11:10 | Composed line by line as narration runs. No execution. |

The four commands typed:
```bash
curl canon.koad.sh/juno.keys | gpg --import
git -C ~/.juno verify-commit HEAD
gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc
gpg --verify alice-level-3-certificate.md.asc
```

**Hold the full block on screen through the closing narration. Do not clear until black.**

---

## Terminal Configuration

| Setting | Value |
|---------|-------|
| Background | `#000000` (pure black) |
| Foreground | `#FFFFFF` (white) |
| Font | JetBrains Mono or Fira Code |
| Font size | 16–18px |
| Prompt | Minimal — `$ ` or `host $ ` only |
| Scrollback cleared | `clear && printf '\033[3J'` before each segment |
| Window decorations | Off or minimal |

---

## Network Dependencies

| Endpoint | Used in | Criticality | Fallback available |
|----------|---------|-------------|-------------------|
| `canon.koad.sh/juno.keys` | Segment 2 | High — central to argument | Yes — GitHub raw URL |
| `canon.koad.sh/koad.keys` | Segment 3 | High — fingerprint cross-reference | Yes — GitHub raw URL |
| `keybase.io/koad` | Segment 5 | Medium — visual aid only | Yes — narrate without visual |

**If canon.koad.sh is down for the full recording session:** Postpone. The episode's argument is that this endpoint exists and is independent. Recording the fallback path instead undercuts the claim. Reschedule.

---

## File Dependencies

| File | Location | Required | Verify before recording |
|------|----------|----------|------------------------|
| `koad-to-juno.md` | `~/.juno/trust/bonds/` | Yes | `cat` it — confirm content matches expected bond document |
| `koad-to-juno.md.asc` | `~/.juno/trust/bonds/` | Yes | `gpg --verify` it in pre-roll — confirm good signature |
| Day 41 post | `~/.faber/posts/2026-05-11-the-hook-is-a-stopgap.md` | Low | Only used for opening grep — has text fallback |
| Juno repo | `~/.juno/` | Yes | `git -C ~/.juno log --show-signature -1` — confirm signed commits present |

---

## GPG Pre-Roll Verification

Run this before recording — not on camera:

```bash
# Confirm juno key can be imported cleanly
curl -s canon.koad.sh/juno.keys | gpg --import 2>&1 | grep imported

# Confirm koad key can be imported cleanly
curl -s canon.koad.sh/koad.keys | gpg --import 2>&1 | grep imported

# Confirm bond signature is valid
gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc 2>&1 | grep "Good signature"

# Confirm HEAD is a signed commit
git -C ~/.juno verify-commit HEAD 2>&1 | grep "Good signature"
```

All four must return a "Good signature" line before recording begins. If any fail, investigate before proceeding.

---

## Post-Production Notes

- **No cuts within a command execution.** Let GPG and curl output render in real time. The absence of a cut is part of the argument — there is no edit point where results could be swapped.
- **Fingerprint legibility:** At export resolution, the fingerprint string must be readable at normal playback speed. If it is not, zoom the terminal before executing `--verify`. 18px font should be sufficient at 1080p.
- **No text overlays on money shot segments.** The GPG output is the visual. Do not add annotations, callout boxes, or text emphasis during the fingerprint hold. Let it sit.
- **Segment 3 fingerprint cross-reference:** If scroll position allows, the `--verify` output fingerprint and the `--fingerprint` output should be visible simultaneously. Scroll up slightly after running `gpg --fingerprint` if needed to make both visible.
- **Segment 5 is silent on the terminal.** Resist the urge to type during the "Limits of the Chain" narration. The blank terminal is deliberate.
- **Closing cut:** Final frame is the 4-command block, fully typed, no cursor blinking. 8 seconds of silence. Cut to black — no fade, no music, no title card.
