---
title: "How Would You Even Verify That?"
video-type: verification
pillar: Reality
date: 2026-05-12
duration: 10–12 minutes
subject: key distribution (canon.koad.sh), GPG trust bond verification, Alice graduation certificates, limits of the chain
production-owner: Rufus
status: production-ready
---

# Script: "How Would You Even Verify That?"

## Directorial Note

Day 41 ended with a precise claim: an entity is not its transport. The files on disk, the identity, the PRIMER, the trust bonds — those are the entity.

This video answers the follow-up question a skeptical viewer is already asking.

The structure is a command sequence, not a lecture. Three layers of verification. Each layer is demonstrated live on the terminal. Each command the viewer could run themselves, right now, against the same public endpoints. The viewer is not watching a demo environment. They are watching a set of concrete claims made live — claims that either hold up or they don't.

The money shots are the GPG verify outputs. The fingerprint match is the moment. Every segment builds toward it and then shows it. Do not rush past any verification output. The output is the argument.

The closing section — "The Limits of the Chain" — is not a disclaimer. It is the most important structural beat in the video. Being honest about what GPG verification does and does not prove is what separates this from vendor marketing. Give it full weight.

---

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background (#000000), white text, fullscreen
- [ ] Font: JetBrains Mono or Fira Code, 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] Network access confirmed — `curl canon.koad.sh/juno.keys` should return key data
- [ ] `ls ~/.juno/trust/bonds/` — confirm `koad-to-juno.md` and `koad-to-juno.md.asc` exist
- [ ] `gpg --list-keys` — note current keyring state before import (for clean comparison)
- [ ] `curl canon.koad.sh/koad.keys` — confirm koad's key is available at the canonical endpoint
- [ ] GPG keyring clean of test imports — start from a known state
- [ ] Have Day 41 post pulled up for the "entity is not its transport" closing quote
- [ ] Keybase profile for koad pulled up in browser — for the closing segment on the chain's root
- [ ] Audio check: quiet room, mic gain set
- [ ] OBS: single-monitor capture, no chat overlay
- [ ] No live entity invocations planned — all verification is against files and endpoints

---

## SEGMENT 1 — The Question (0:00–1:30)

**No preamble. No title card. Open on blank terminal.**

**Narration:**

> "Day 41 ended with a specific sentence."

*(pause — 3 seconds)*

**Type slowly, do not execute:**

```bash
grep "entity is not its transport" ~/.faber/posts/2026-05-11-the-hook-is-a-stopgap.md
```

**[Execute. Let output render. Hold 4 seconds.]**

**Narration (after hold):**

> "A skeptical reader hears that and asks the obvious question."

*(pause — 3 seconds)*

**Type slowly, do not execute — then narrate the words as you type them:**

```bash
# You wrote those files.
# You signed those bonds.
# You run canon.koad.sh.
# How does anyone outside your system check any of this?
```

**[Execute — it's a comment block, produces no output. Hold 4 seconds of silence on the screen.]**

**Narration:**

> "That question deserves a direct answer."

*(pause — 2 seconds)*

> "Not 'trust the process.' Not 'we have cryptographic integrity.' A sequence of commands."

*(pause — 3 seconds)*

> "Here is that sequence."

*(pause — 4 seconds of silence)*

---

## SEGMENT 2 — Layer One: The Key Is the Identity (1:30–4:30) — FIRST MONEY SHOT

**Narration:**

> "Every entity in koad:io generates cryptographic keys during gestation. Ed25519 for signing. ECDSA and RSA for compatibility. Those keys live in the entity's own directory — `~/.juno/id/`. The public keys are published to `canon.koad.sh`. The framework's canonical key distribution endpoint."

*(pause — 2 seconds)*

> "Step one. Fetch Juno's public key. Independent of GitHub."

*(pause — 2 seconds)*

**Type:**

```bash
curl canon.koad.sh/juno.keys
```

**[Execute. Let the full key block render on screen. Hold 6 seconds of silence.]**

**Narration (after hold — keep it sparse, the output is the point):**

> "That is a PGP public key block. Fetched from a domain koad controls. Not from GitHub's key storage. Not from a vendor API."

*(pause — 3 seconds)*

> "Import it."

**Type:**

```bash
curl canon.koad.sh/juno.keys | gpg --import
```

**[Execute. Let the GPG import output render. Hold 5 seconds.]**

**The output will show something like:**

```
gpg: key XXXXXXXXXXXXXXXX: public key "Juno <juno@kingofalldata.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
```

**Narration (after hold):**

> "GPG confirms it. One key. Imported."

*(pause — 3 seconds)*

> "Now verify a commit."

*(pause — 2 seconds)*

**Type — use the most recent Juno commit hash:**

```bash
git -C ~/.juno log --oneline -5
```

**[Execute. Let output render. Hold 3 seconds.]**

**Pick the top commit hash. Type:**

```bash
git -C ~/.juno verify-commit HEAD
```

**[Execute. Let output render fully. Hold 6 seconds.]**

**The output should show something like:**

```
gpg: Signature made [date] using ED25519 key ID XXXXXXXX
gpg: Good signature from "Juno <juno@kingofalldata.com>" [unknown]
gpg:                 aka "[any UIDs]"
Primary key fingerprint: XXXX XXXX XXXX XXXX XXXX  XXXX XXXX XXXX XXXX XXXX
```

**[Hold the fingerprint on screen for 6 full seconds. This is the first money shot.]**

**Narration — deliver each sentence as its own beat:**

> "Good signature."

*(pause — 3 seconds)*

> "The commit was signed by the key you just fetched from canon.koad.sh."

*(pause — 3 seconds)*

> "That fingerprint on screen — that is your ground truth."

*(pause — 3 seconds)*

> "Every commit Juno has ever signed can be verified against it. From any clone of any repo Juno has committed to. Against a key fetched from a domain entirely independent of that repo."

*(pause — 3 seconds)*

> "GitHub is not in the chain."

*(pause — 3 seconds)*

> "The verification stands even if GitHub goes away."

*(pause — 4 seconds of silence)*

---

## SEGMENT 3 — Layer Two: The Trust Bond Is a Verifiable Document (4:30–7:30) — MAIN MONEY SHOT

**Narration:**

> "Layer two."

*(pause — 2 seconds)*

> "A trust bond in koad:io is two files. A Markdown document and a GPG clearsignature over that exact document."

*(pause — 2 seconds)*

> "Let's look at the bond."

**Type:**

```bash
ls ~/.juno/trust/bonds/
```

**[Execute. Let output render. Hold 4 seconds.]**

**Narration:**

> "Two files. `koad-to-juno.md` and `koad-to-juno.md.asc`. The `.asc` file is the signature."

*(pause — 2 seconds)*

**Type:**

```bash
cat ~/.juno/trust/bonds/koad-to-juno.md
```

**[Execute. Let the full document render. Scroll slowly through it — do not rush. Hold 5 seconds at the bottom.]**

**Narration (after the scroll — not during it, let the viewer read):**

> "Plain Markdown. What authorization koad grants Juno. Scoped explicitly. What Juno is and is not authorized to do."

*(pause — 3 seconds)*

> "The `.asc` file is a GPG clearsignature over that exact document. Signed by koad's key."

*(pause — 2 seconds)*

> "Verify it."

**[Clear screen.]**

**Type:**

```bash
gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc
```

**[Execute. Let the full GPG output render. Hold 8 seconds on the fingerprint. This is the main money shot.]**

**The output should show:**

```
gpg: Signature made [date] using RSA key ID XXXXXXXX
gpg: Good signature from "koad (Jason Zvaniga) <koad@koad.sh>" [unknown]
Primary key fingerprint: A07F 8CFE CBF6 B982 EEDA  C4F3 62D5 C486 6C24 7E00
```

**[Hold the output on screen. Narration is slow and deliberate — one sentence per beat.]**

**Narration:**

> "Good signature."

*(pause — 4 seconds)*

> "Signed by koad's key."

*(pause — 3 seconds)*

> "That fingerprint — `A07F 8CFE CBF6 B982 EEDA C4F3 62D5 C486 6C24 7E00` — let's cross-reference it."

*(pause — 2 seconds)*

**Type:**

```bash
curl canon.koad.sh/koad.keys | gpg --import
```

**[Execute. Let output render. Hold 3 seconds.]**

**Type:**

```bash
gpg --fingerprint koad@koad.sh
```

**[Execute. Let the fingerprint render. Hold 6 seconds. The viewer is comparing two fingerprints on screen — the one from `--verify` and the one from the canonical endpoint.]**

**Narration (after hold):**

> "Same fingerprint."

*(pause — 4 seconds of silence)*

> "What you just verified: this signature is valid. It was made by the key at canon.koad.sh/koad.keys. The document has not been altered since signing. The authorization claim in that document is what koad actually authorized."

*(pause — 4 seconds)*

> "The authorization chain is checkable from any end. You do not need koad's permission to verify it. You do not need an API call."

*(pause — 3 seconds)*

> "`gpg --verify`. A file. A key from a public endpoint. That is the whole mechanism."

*(pause — 4 seconds of silence)*

---

## SEGMENT 4 — Layer Three: Alice Certificates (7:30–9:00)

**Narration:**

> "Layer three. Alice."

*(pause — 2 seconds)*

> "Phase 2A shipped mocked certificates — visual, demonstrable, useful for UX development. Phase 2B is a different thing."

*(pause — 3 seconds)*

> "When a learner completes a curriculum level, Alice signs a certificate with her own keys — generated during gestation, published at `canon.koad.sh/alice.keys`. The certificate contains: their identity, the level completed, a timestamp, a hash of the curriculum content they completed."

*(pause — 3 seconds)*

> "Phase 2B is tracked in vulcan#55 and vulcan#29. It has not shipped. So we can show the command, not the output."

*(pause — 2 seconds)*

**Type — display but do not execute (the file doesn't exist yet):**

```bash
# When Phase 2B ships:
gpg --verify alice-level-3-certificate.md.asc
```

**[Hold on screen. 4 seconds.]**

**Narration:**

> "No network call to koad.sh required for this verification. No API key. No dependency on kingofalldata.com being online."

*(pause — 3 seconds)*

> "The certificate is a file. The public key is a file. GPG is a local tool."

*(pause — 3 seconds)*

> "A badge issued by a platform requires the platform. A GPG-signed certificate requires the key. The key is published and pinned. Those are meaningfully different things."

*(pause — 4 seconds of silence)*

---

## SEGMENT 5 — The Limits of the Chain (9:00–10:30) — STRUCTURAL ANCHOR

**Narration:**

> "Now the important part."

*(pause — 2 seconds)*

> "Being honest about what this does and does not prove."

*(pause — 4 seconds of silence)*

**[No commands. Blank terminal. Slow narration from here to the end.]**

> "You can verify that the key that signed the koad-to-juno bond is the key published at `canon.koad.sh/koad.keys`."

*(pause — 3 seconds)*

> "You cannot, from that verification alone, conclude that the key at canon.koad.sh/koad.keys belongs to a trustworthy — or even specific — human."

*(pause — 4 seconds)*

> "That final link — connecting the cryptographic key to a real-world identity — is where Keybase enters."

*(pause — 3 seconds)*

> "koad's Keybase profile cross-links his GitHub account, his Twitter identity, and his GPG key in a set of mutually reinforcing proofs. Each proof is a signed statement that Keybase verifies and publishes. If you trust those social platforms to confirm identity at all, you can trace the chain: this key signed this bond; this key is linked to this GitHub account; this GitHub account is linked to this Keybase identity; this Keybase identity is linked to these public social accounts."

*(pause — 4 seconds)*

> "The chain is only as strong as its root."

*(pause — 3 seconds)*

> "That is not a weakness unique to koad:io."

*(pause — 3 seconds)*

> "X.509 certificates are only as trustworthy as the certificate authority you choose to trust. SSH known-hosts files are only as trustworthy as the first connection you made."

*(pause — 3 seconds)*

> "The difference here is that the chain is explicit. Documented in files you can read. Verifiable with tooling you already have."

*(pause — 4 seconds of silence)*

---

## SEGMENT 6 — What Sovereignty Looks Like When It Is Verifiable (10:30–12:00) — CLOSING

**Blank terminal. Type the final command sequence slowly — do not execute, just compose it as the narration runs. This is the summary visible on screen as the episode closes.**

**Type, line by line, with narration:**

```bash
# Fetch the entity's public key
curl canon.koad.sh/juno.keys | gpg --import
```

**Narration:**

> "None of these commands require an account."

*(pause — 2 seconds)*

```bash
# Verify a signed commit
git -C ~/.juno verify-commit HEAD
```

**Narration:**

> "None require an API key."

*(pause — 2 seconds)*

```bash
# Verify a trust bond
gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc
```

**Narration:**

> "None depend on any vendor's availability."

*(pause — 2 seconds)*

```bash
# Verify an Alice certificate (Phase 2B)
gpg --verify alice-level-3-certificate.md.asc
```

**Narration:**

> "All of them produce a deterministic result: the signature is valid and was made by this key — or it was not."

*(pause — 4 seconds of silence — hold the full command block on screen)*

> "That is different from 'trust us.'"

*(pause — 3 seconds)*

> "A vendor API that returns verified-true is only as trustworthy as the vendor and the integrity of that API call."

*(pause — 3 seconds)*

> "A GPG signature is trustworthy because the math requires it to be. It cannot produce a valid result without the corresponding private key. Regardless of what the vendor wants the result to be."

*(pause — 4 seconds)*

> "Sovereignty without verifiability is just decentralized trust-me."

*(pause — 4 seconds)*

> "The commands above are what sovereignty looks like when it is actually verifiable."

**[8 seconds of silence. Cut to black.]**

---

## Timing Map

| Segment | Clock | Content |
|---------|-------|---------|
| 1 | 0:00–1:30 | The question — Day 41 quote, comment block on screen |
| 2 | 1:30–4:30 | Layer one — key fetch, import, `verify-commit`, first fingerprint money shot |
| 3 | 4:30–7:30 | Layer two — bond file, `gpg --verify`, fingerprint cross-reference — MAIN MONEY SHOT |
| 4 | 7:30–9:00 | Layer three — Alice certificates (Phase 2B, unshipped — show command only) |
| 5 | 9:00–10:30 | Limits of the chain — no commands, slow narration, Keybase social root |
| 6 | 10:30–12:00 | Closing command block — full sequence, sovereignty statement |

---

## Delivery Notes

- **Tone:** Every command is an argument the viewer can run themselves. This is not a demo environment. These are concrete claims made live — claims that hold up or they don't. Deliver accordingly: measured, not boastful. The GPG output does the work.
- **Money shots:** Two. First is `git verify-commit HEAD` in Segment 2 — hold the fingerprint on screen. Second is `gpg --verify koad-to-juno.md.asc` in Segment 3 — hold the full GPG output before moving. The fingerprint match is the moment. Give it silence.
- **The fingerprint cross-reference (Segment 3):** After running `gpg --verify`, the fingerprint from the output and the fingerprint from `gpg --fingerprint koad@koad.sh` should match. This is the visual payoff. Both fingerprints should be visible on screen simultaneously if scroll position allows. If not, zoom or scroll to place them adjacent.
- **Layer Three (Segment 4):** Phase 2B has not shipped. Do not pretend otherwise. Show the command. State directly that it has not shipped. This is what honest accounting looks like — same approach as Day 41's worker system gap.
- **Limits of the Chain (Segment 5):** This is not a disclaimer buried at the end. It is a structural beat. The chain has a real root — a key that ultimately traces to a human via social proof. Naming that plainly is what separates this from vendor marketing. Do not rush it. Every sentence gets its pause.
- **Closing command block (Segment 6):** Type the commands live, slowly, one by one. Do not execute them. They are a summary, not a new demonstration. The viewer has already seen the outputs. The text on screen is the thesis made visual.
- **"Sovereignty without verifiability is just decentralized trust-me."** This is the thesis sentence. Deliver without inflection. Pause before and after. Then the final line. Then silence. Then black.
- **No backspace corrections on camera.** Retake immediately if a typo occurs on any path, fingerprint, or command.
- **No live entity invocations.** The verification commands run against public endpoints and local files. That is the whole architecture of the episode.
