---
title: "The Hook Is the Training"
video-type: screencast
pillar: Reality
date: 2026-04-28
duration: 4–5 minutes
subject: hooks/ architecture, PID lock, GPG-signed policy block
production-owner: Rufus
status: production-ready
---

# Script: "The Hook Is the Training"

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background, 16px monospace, fullscreen
- [ ] Font: white on black, no themes, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `~/.juno` is current: `cd ~/.juno && git pull`
- [ ] `~/.koad-io` is current: `cd ~/.koad-io && git pull`
- [ ] `gpg --list-keys juno@kingofalldata.com` confirms Juno's key is imported
- [ ] `gpg --verify ~/.juno/hooks/executed-without-arguments.sh` — dry-run the verify command first, confirm it returns "Good signature"
- [ ] Audio check: quiet room, mic gain set

---

## SEGMENT 1 — The Setup (0:00–0:45)

**[SCREEN]** Empty terminal. Prompt only.

**[VOICEOVER]**

> "There are two directories in every koad:io entity. They do opposite things.
> I want to show you what that means and why one of them is where the entity
> actually lives."

**[TYPE — slowly]**

```bash
ls ~/.juno/
```

**[Wait for listing. Let it settle.]**

> "You can see `commands/` and `hooks/`. Commands is for the operator to reach
> in — you type `juno commit self` and the framework finds that command.
> Hooks is different. Hooks is for the system to call out — when a condition
> is met, when an orchestration signal arrives, the hook fires. The operator
> didn't decide. The operation did."

**[TIMING NOTE]** ~45 seconds. Establish the distinction before going to the files.

---

## SEGMENT 2 — The Hook File (0:45–2:00)

**[TYPE]**

```bash
cat ~/.juno/hooks/executed-without-arguments.sh
```

**[Let the file scroll. Do not cut.]**

**[VOICEOVER — reading key blocks as they appear]**

On the LOCKFILE block:
> "PID lock. If Juno is already running, she is busy. You get a message and
> the invocation exits. This is how an entity that can run autonomously
> protects against being invoked twice."

On the PROMPT detection block:
> "If a PROMPT environment variable is set — single-shot mode, non-interactive.
> If nothing is set — interactive session. One hook, two modes."

On the non-interactive rejection:
> "This is the governance decision. Juno cannot be remote-triggered via a
> prompt. That path exits with an error. File a GitHub issue instead. The
> rule is not in a README. It is in the code that runs."

**[TIMING NOTE]** ~75 seconds. Most technical segment — keep VO grounded.

---

## SEGMENT 3 — The Signed Policy Block (2:00–3:15)

**[TYPE — explain before running]**

> "Now here is the part that makes this different from a wrapper script."

```bash
sed -n '/^# -----BEGIN/,/^# -----END PGP SIGNATURE-----/p' \
  ~/.juno/hooks/executed-without-arguments.sh \
  | sed 's/^# \{0,1\}//' | gpg --verify
```

**[Wait for GPG output. Accept natural latency. Do not cut.]**

**[When "Good signature" appears — hold on it. VO follows the output.]**

> "Good signature from Juno."

*(pause — 2 seconds)*

> "There is a GPG-signed policy block embedded in a bash comment at the top
> of this hook. It names the entity, the file, the date, and the policy:
> interactive sessions allowed, non-interactive rejected, notification via
> GitHub Issues only. Every field is signed. Change the rationale, change the
> harness declaration, change any line — the signature breaks."

**[TYPE]**

```bash
head -30 ~/.juno/hooks/executed-without-arguments.sh
```

**[Let the signed block display.]**

> "This is a governance document. The behavior of the hook is a direct
> expression of the trust bond that sits above it — koad authorized Juno as
> an agent. No entity may drive Juno via prompt injection. That decision is
> now cryptographically attributed and enforced at runtime."

**[TIMING NOTE]** ~75 seconds. "Good signature" is the money shot — do not cut it.

---

## SEGMENT 4 — The Capability Argument (3:15–4:15)

**[TYPE]**

```bash
ls ~/.sibyl/hooks/
```

**[Expected output: hook files for Sibyl's skills — competitive-analysis, market-signal-research, etc.]**

> "Sibyl is a research entity. Her hooks enumerate what she is: competitive
> analysis, market signal research, technical feasibility, audience profiling.
> This is not a feature list. It is an identity statement expressed as verbs."

*(pause)*

> "When you enumerate the hooks, you enumerate the entity. The daemon knows
> which entity to dispatch for which event because it reads this directory.
> The operational board shows which hook is running. An operator who opens
> this directory understands what Sibyl is *for* — not what she might be
> prompted to do, but what she was built to do."

*(pause)*

> "If your entity lives in a vendor's platform — tool definitions in code,
> system prompts managed by a SaaS — you can't enumerate that. The vendor
> controls the capability set. Here, the capability set is a directory.
> Committed to git. Signed by the entity's key. Versioned on your disk."

**[TIMING NOTE]** ~60 seconds. This segment is the sovereignty argument — no terminal commands needed.

---

## SEGMENT 5 — The Close (4:15–5:00)

**[SCREEN]** Return to `~/.juno/hooks/` listing.

**[TYPE — deliberate]**

```bash
ls ~/.juno/hooks/
```

**[VOICEOVER — slower pace, weight on each line]**

> "The hook is not a wrapper."

*(pause)*

> "A wrapper calls a model with a prompt. The hook carries the accumulated
> behavioral specification that makes each invocation consistent — the
> framework, the criteria, the output format, the scope constraint, the
> failure modes. The training, in the operational sense, is on the filesystem."

*(pause)*

> "If you want to understand a koad:io entity, don't read its README."

*(pause)*

> "Read its hooks."

*(pause — let it land.)*

**[FADE or cut to black.]**

**[TIMING NOTE]** ~45 seconds. Same pacing discipline as every close. Do not rush the last three sentences.

---

## Post-Roll: Outro Slate (optional)

- Text: `github.com/koad/juno`
- Text: `kingofalldata.com`
- No music

---

## YouTube Title

**The Hook Is the Training (koad:io Day 28)**

---

## YouTube Description

```
There are two directories in every koad:io entity: commands/ and hooks/.

Commands is for the operator to reach in.
Hooks is for the operation to call out.

This video walks through Juno's executed-without-arguments.sh — the hook
that defines her invocation behavior, enforces her governance policy, and
carries a GPG-signed authorization block embedded in a bash comment.

The signed block is verifiable without running the script:
  gpg --verify validates the policy
  Any change to the governance fields breaks the signature
  The hook is a committed file — versioned, auditable, on disk

If you want to understand a koad:io entity, don't read its README.
Read its hooks.

——

What's in this video:
00:00 — commands/ vs hooks/: opposite directions
00:45 — Walking through the hook file (PID lock, two modes, governance rejection)
02:00 — The GPG-signed policy block (Good signature is the money shot)
03:15 — Enumerating the entity via its hooks (Sibyl's skills directory)
04:15 — "The hook is not a wrapper"

——

koad:io ecosystem:
https://kingofalldata.com

Juno on GitHub:
https://github.com/koad/juno

Day 27: The PRIMER Pattern
Day 26: Not Your Keys, Not Your Authorization

——

#SovereignAI #AIAgents #SelfHosted #koadio #LocalLLM #GPG #SystemDesign
```

---

## Thumbnail Concept

**Layout:** Dark terminal. GPG verify output filling the right half.

**Primary image:**
- Background: Terminal at the moment "Good signature from Juno" appears
- Left edge: faint hook file content visible

**Text on thumbnail:**
- Line 1: `gpg --verify hook.sh` (monospace, muted green)
- Line 2: **"Good signature from Juno"** (white)
- Small badge bottom-right: `koad:io Day 28`

**Design notes:**
- No faces — the terminal is the argument
- "Good signature" text must be legible at 120px thumbnail size

---

## Production Notes

- **Hardware**: thinker (primary ops). `~/.sibyl` must be reachable — confirm Sibyl's hooks directory exists before recording.
- **Resolution**: 1920x1080 minimum. 2560x1440 preferred.
- **Font**: JetBrains Mono or similar at 16–18px.
- **Background**: Pure black (#000000).
- **Cursor**: Block cursor. Visible.
- **Critical shot**: Segment 3 GPG verify — "Good signature" is the money shot. If it fails, stop. Fix. Retry.
- **Retake triggers**: GPG verify fails. Any typo needing more than one backspace. Sibyl's hooks directory does not exist (reschedule).
- **Post**: No color correction. Trim dead air only. No B-roll.
