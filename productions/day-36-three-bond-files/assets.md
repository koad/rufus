---
title: "Shot List — Three Bond Files, Three Relationship Types"
video: day-36-three-bond-files
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "Three Bond Files, Three Relationship Types"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines

### State verification (CRITICAL: pull Juno repo immediately before recording)
- [ ] `git -C ~/.juno pull` — must be run immediately before the session
- [ ] `ls ~/.juno/trust/bonds/` — confirm six core files present (koad-to-juno.md + .asc, juno-to-vulcan.md + .asc, juno-to-sibyl.md + .asc); additional bonds in the directory are fine
- [ ] `cat ~/.juno/trust/bonds/koad-to-juno.md` — confirm signing block: `[x] koad signs this bond with Keybase PGP key` and fingerprint `A07F 8CFE CBF6 B982 EEDA C4F3 62D5 C486 6C24 7E00` visible
- [ ] `cat ~/.juno/trust/bonds/juno-to-vulcan.md` — confirm `[ ] Vulcan acknowledges signing` box is unchecked
- [ ] `cat ~/.juno/trust/bonds/juno-to-sibyl.md` — confirm double-pending: `[ ] Copy filed in ~/.sibyl/trust/bonds/ (pending entity gestation)` and `[ ] Sibyl acknowledges signing (pending gestation)` both unchecked
- [ ] `ls ~/.juno/trust/revocation/` — confirm directory exists and is empty (no output = the signal)
- [ ] `gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc` — note whether key is in local keyring; if not, the error is itself useful on camera (key distribution teaching moment)
- [ ] `gpg --verify ~/.juno/trust/bonds/juno-to-vulcan.md.asc` — same check
- [ ] `gh auth status` — confirm GitHub CLI authenticated
- [ ] OBS armed at 1920x1080, 60fps, black background capture
- [ ] Mic check

### What to know before recording

**The three bond types and their structural meaning:**

| Bond | Type | Issuer | Direction | Key distinction |
|------|------|--------|-----------|-----------------|
| koad-to-juno | authorized-agent | koad (human) | Root grant | Only koad can issue this type; Keybase signing = human ceremony |
| juno-to-vulcan | authorized-builder | Juno | Delegation downward | Workflow protocol embedded in bond; one unchecked box (lifecycle, not error) |
| juno-to-sibyl | peer | Juno | Lateral | Double-pending; bond filed before entity existed |

**The dual-file protocol:**
- `.md` = human-readable, for reading
- `.md.asc` = GPG clearsigned, for verifying
- You can read without the signature; you cannot assert authority without it
- The `.asc` is the proof, not an attachment

**The cascade clause (from koad-to-juno.md):**
> "All of Juno's authority is derived from this bond. If this bond is revoked, all downstream bonds issued by Juno are suspended pending review."

**The revocation directory:**
- Path: `~/.juno/trust/revocation/`
- Currently: empty
- Significance: emptiness is a positive signal, not an absence of data

**The signing distinction:**
- koad: Keybase PGP (`keybase@kingofalldata.com`), fingerprint `A07F 8CFE CBF6 B982 EEDA C4F3 62D5 C486 6C24 7E00`
  - Interactive process; requires physical Keybase action; human ceremony
- Juno: GPG key (`juno@kingofalldata.com`), fingerprint `16EC 6C71 8A96 D344 48EC D39D 92EA 133C 44AA 74D8`
  - Generated during gestation; programmatic signing; derived authority

**Key lines to hold on screen:**
- koad-to-juno.md, reporting protocol: `"Juno does not wait for approval on in-scope actions."`
- juno-to-vulcan.md, prohibition: `[ ] Vulcan acknowledges signing`
- juno-to-sibyl.md, signing block: `[ ] Copy filed in ~/.sibyl/trust/bonds/ (pending entity gestation)`
- koad-to-juno.md, cascade: `"All of Juno's authority is derived from this bond."`

**Closing line of script (from post — verbatim):**
> "It marks the boundary between where human will entered the system and where derived authority carries it forward."

---

## Shot 1: The Directory — Opening Frame

**Segment:** SEGMENT 1 (0:00–0:45)
**Duration:** ~45 seconds

**What to type (slowly — one character at a time):**
```bash
ls ~/.juno/trust/bonds/
```

**Expected output:** Directory listing — six core files (plus any additional bonds added since). The `.md` / `.md.asc` pairs should be immediately visible as a pattern.

**What to say (after 5 seconds of silence on the listing):**
> "Six files. Three bonds."
>
> *(pause — 2 seconds)*
>
> "Every bond is two artifacts: a human-readable `.md` and a `.md.asc` — a GPG clearsigned copy of the same document."
>
> *(pause)* "This is the dual-file protocol. One for reading, one for verifying."
>
> *(pause)* "You can read a bond without its signature. You cannot assert authority with an unsigned `.md`. The `.asc` is not an attachment. It is the proof."
>
> *(pause — 2 seconds)* "Let me show you the actual files."

**Technical notes:**
- Open cold — no preamble, type the command immediately
- 5-second silence after the listing displays is intentional — let the viewer read the file names
- If the directory has expanded beyond six files: fine, do not comment on it; the viewer is seeing the ecosystem has grown
- Retake trigger: directory listing not fully readable, or viewer cannot see the .md / .md.asc pairing pattern

---

## Shot 2: koad-to-juno.md — Root Grant Frontmatter

**Segment:** SEGMENT 2 (0:45–2:30)
**Duration:** ~105 seconds

**What to type:**
```bash
cat ~/.juno/trust/bonds/koad-to-juno.md
```

**Expected output:** Full bond file — frontmatter, Bond Statement, Authorized Actions, NOT authorized list, Reporting Protocol, Trust Chain, Signing block.

**Scroll pacing:**
1. Hold on frontmatter (type, from, to, status, visibility) — ~5 seconds
2. Scroll slowly through Authorized Actions
3. **HOLD** on NOT authorized list, specifically: `Issue authorized-agent bonds to any entity (only koad may do this)` — 4 seconds
4. **HOLD** on Reporting Protocol last sentence: `Juno does not wait for approval on in-scope actions.` — 4 seconds
5. **HOLD** on Signing block — both lines of the signed entry visible — 4 seconds

**What to say:**
> "Bond one: koad to Juno. Type: `authorized-agent`. This is where Juno's operating authority originates."
>
> *(scroll to authorized actions)* "The authorized actions list is specific: file GitHub Issues on team repos, issue trust bonds to team entities at `authorized-builder` or `peer` level, spend up to $50 a month, gestate new entities."
>
> *(scroll to NOT authorized, hold on last prohibition)* "Equally specific is the prohibited list. The last item is structural: Juno cannot issue `authorized-agent` bonds to anyone. Only koad may do this."
>
> *(pause)* "Juno can delegate downward. She cannot replicate her own grant type. The `authorized-agent` class is reserved for koad's direct issuance."
>
> *(scroll to Reporting Protocol, hold on last sentence)* "The reporting protocol contains one sentence worth reading carefully: 'Juno does not wait for approval on in-scope actions.'"
>
> *(pause — 2 seconds)* "This is not a policy gate. The bond is the gate. Once signed, Juno acts."
>
> *(scroll to Signing block, hold)* "The signing block. koad signs with Keybase PGP. Both sides hold a copy. The trust relationship is on both disks."

**Technical notes:**
- DO NOT CUT the scroll
- Both the fingerprint line and the `[x] Copy filed in ~/.koad-io/trust/` line must appear on screen
- "Juno does not wait for approval" — 2-second pause before the follow-on explanation; this is the structural reveal

---

## Shot 3: juno-to-vulcan.md — Delegation Layer

**Segment:** SEGMENT 3 (2:30–4:15)
**Duration:** ~105 seconds

**What to type:**
```bash
cat ~/.juno/trust/bonds/juno-to-vulcan.md
```

**Expected output:** Full bond — type: authorized-builder, reporting chain, five-step workflow protocol, signing block with the unchecked Vulcan acknowledgment.

**Scroll pacing:**
1. Hold on frontmatter — type: authorized-builder, from: Juno, to: Vulcan — ~4 seconds
2. Scroll slowly to Reporting Chain — **HOLD** on the three-line chain: koad → Juno → Vulcan — 5 seconds
3. Scroll to Workflow Protocol — **HOLD on all five steps simultaneously** — 6 seconds
4. Scroll to Signing block — **HOLD on the unchecked `[ ] Vulcan acknowledges signing`** — 5 seconds (CRITICAL VISUAL)

**What to say:**
> "Bond two: Juno to Vulcan. Type: `authorized-builder`. Juno issues this one, under the authority she received from koad."
>
> *(scroll to Reporting Chain, hold)* "The reporting chain is explicit in the bond text."
>
> *(pause — let viewer read)* "`koad → Juno → Vulcan`. Vulcan's actions are scoped by Juno's scope. Juno's scope is scoped by koad's authorization. Traceable to the root from any point in the chain."
>
> *(scroll to Workflow Protocol, hold on all five steps)* "The bond is the spec. Not a separate document linked from the bond — the operating protocol is in the bond. If you want to know how Vulcan operates, you read this file."
>
> *(pause — 2 seconds)*
>
> *(scroll to Signing block, hold on unchecked box)* "The signing block shows an asymmetry worth noting."
>
> *(pause)* "Juno's signature: checked. Bond filed: checked. Copy filed in Vulcan's repo: checked."
>
> *(pause)* "Vulcan acknowledges signing: unchecked."
>
> *(pause — 2 seconds)* "The bond was filed and active before Vulcan's bilateral signing was complete. This is the normal lifecycle for a newly gestated entity."
>
> *(pause)* "An unchecked box is not an error. It is the bond telling you where in the lifecycle it is."

**CRITICAL VISUAL:** The `[ ] Vulcan acknowledges signing` checkbox must be readable on screen during the "An unchecked box is not an error" line. This is the money shot of Segment 3.

**Technical notes:**
- Hold the unchecked box for 3 full seconds before speaking about it
- The contrast between the checked boxes and the unchecked one must be visually clear
- Retake trigger: unchecked box not readable; any cut during the signing block scroll

---

## Shot 4: juno-to-sibyl.md — Lateral Layer

**Segment:** SEGMENT 4 (4:15–5:45)
**Duration:** ~90 seconds

**What to type:**
```bash
cat ~/.juno/trust/bonds/juno-to-sibyl.md
```

**Expected output:** Full bond — type: peer, Peer Relationship section with the non-subordination clause, signing block with two unchecked boxes.

**Scroll pacing:**
1. Hold on frontmatter — type: peer — ~4 seconds
2. Scroll to Peer Relationship — **HOLD** on `"Neither entity is subordinate to the other..."` clause — 5 seconds
3. Scroll to Signing block — **HOLD on both unchecked boxes** — 6 seconds (CRITICAL VISUAL)

**What to say:**
> "Bond three: Juno to Sibyl. Type: `peer`. This is not a delegation. No authority flows downward. No subordination exists."
>
> *(scroll to Peer Relationship, hold)* "The peer relationship section: 'Neither entity is subordinate to the other. Peer bonds do not grant financial authority, key access, or the right to issue bonds on behalf of the other.'"
>
> *(pause)* "Lateral, not hierarchical."
>
> *(scroll to Signing block, hold on both unchecked boxes)* "The signing block here is double-pending."
>
> *(pause — let viewer read)* "Juno's signature: checked. Bond filed in Juno's repo: checked."
>
> *(pause)* "Copy filed in Sibyl's repo: pending entity gestation. Sibyl acknowledges signing: pending gestation."
>
> *(pause — 2 seconds)* "Sibyl did not exist when this bond was filed. The bond was written, signed by Juno, and committed before Sibyl had keys, a directory, or a gestated identity."
>
> *(pause)* "When Sibyl is gestated and her keys generated, she inherits a bond that is already written and waiting."
>
> *(pause — 2 seconds)* "Two unchecked boxes in this bond. One in the Vulcan bond. Different reasons. Same syntax. The file tells you."

**CRITICAL VISUAL:** Both `[ ] Copy filed in ~/.sibyl/trust/bonds/ (pending entity gestation)` and `[ ] Sibyl acknowledges signing (pending gestation)` must be readable on screen simultaneously.

**Technical notes:**
- Compare explicitly to the Vulcan bond's single unchecked box — the contrast between "lifecycle" unchecked vs "not-yet-existing" unchecked is the structural argument
- Retake trigger: both unchecked boxes not visible at the same time on screen

---

## Shot 5: The Revocation Directory — The Empty Signal

**Segment:** SEGMENT 5 (5:45–7:00)
**Duration:** ~75 seconds

**What to type:**
```bash
ls ~/.juno/trust/revocation/
```

**Expected output:** Nothing. Blank line or empty output.

**Hold 4 full seconds of silence on the empty output before speaking.**

**What to say:**
> "The revocation directory. Currently empty."
>
> *(pause — 2 seconds)* "If it ever contains a file, the operating state of the entity has changed in a fundamental way. The directory's emptiness is itself a signal."

**What to type next:**
```bash
grep -A2 "all of Juno\|downstream bonds\|revoked" ~/.juno/trust/bonds/koad-to-juno.md
```

**Expected output:** The cascade clause — "All of Juno's authority is derived from this bond. If this bond is revoked, all downstream bonds issued by Juno are suspended pending review."

**What to say:**
> "The root bond states it plainly: 'All of Juno's authority is derived from this bond. If this bond is revoked, all downstream bonds issued by Juno are suspended pending review.'"
>
> *(pause — 2 seconds)* "Revoke the root, suspend the tree."
>
> *(pause)* "The `juno-to-vulcan` bond has its own revocation clause. But the cascade in the root bond means even that language is downstream of koad's ultimate authority."
>
> *(pause)* "Peer bond revocation is contained. Revoking `juno-to-sibyl` affects only that lateral relationship. The hierarchy insulates itself from peer-layer disruption by design."
>
> *(pause — 2 seconds)* "Three bond types. Three blast radiuses. The directory tells you all of this."

**CRITICAL VISUAL:** The empty `ls` output. 4 seconds of silence on nothing. This is the visual argument that emptiness communicates state.

**Technical notes:**
- Do NOT rush to speak after the empty output — hold silence is the point
- The grep pattern may need adjustment if the exact text differs; alternative: `grep -A2 "bond is revoked" ~/.juno/trust/bonds/koad-to-juno.md`
- Retake trigger: any verbal stumble on "blast radiuses"; any cut during the empty directory moment

---

## Shot 6: gpg --verify koad-to-juno.md.asc — Human Ceremony

**Segment:** SEGMENT 6 (7:00–8:00)
**Duration:** ~30 seconds of this shot

**What to type:**
```bash
gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc
```

**Expected output:** GPG verification output showing the signer identity and key fingerprint (or a "public key not found" error if koad's Keybase key is not in local keyring — either is acceptable on screen).

**What to say:**
> "koad signs with Keybase PGP — `keybase@kingofalldata.com`. Keybase is an interactive process, tied to a verified public identity."
>
> *(pause)* "Executing `keybase pgp sign` required koad to physically open Keybase and perform the action. It is not a bureaucratic formality. It is the moment at which sovereign intent is cryptographically recorded."
>
> *(pause)* "The root bond exists because a human chose to make it exist."
>
> *(pause — 2 seconds)*

**Technical notes:**
- If GPG returns "No public key" — acceptable; note it on screen: "the signing key is not in this keyring, but the signature is intact — key distribution is a separate step"
- The fingerprint in the `.asc` file header is the verification reference even without the local key

---

## Shot 7: gpg --verify juno-to-vulcan.md.asc — Derived Authority

**Segment:** SEGMENT 6 continued (7:30–8:00)
**Duration:** ~30 seconds

**What to type:**
```bash
gpg --verify ~/.juno/trust/bonds/juno-to-vulcan.md.asc
```

**Expected output:** GPG verification showing Juno's GPG key and fingerprint `16EC 6C71 8A96 D344 48EC D39D 92EA 133C 44AA 74D8`.

**What to say:**
> "Juno signs with her own GPG key — generated during gestation, stored in `~/.juno/id/`. The signing is programmatic. Her authority to issue bonds is not assumed. It is derived and verifiable."
>
> *(pause — 2 seconds)* "Two different keys. Two different fingerprints. The difference between them is not just technical."
>
> *(pause)* "It marks the boundary between where human will entered the system and where derived authority carries it forward."

**[FADE or cut to black immediately after the closing line.]**

**CRITICAL DELIVERY:** "It marks the boundary between where human will entered the system and where derived authority carries it forward." — this is the closing line of the post, verbatim. Deliver it at the slowest pace in the video. 1-second pause between "entered the system" and "and where derived authority carries it forward." Do not rush the final clause.

**Technical notes:**
- Both fingerprints — koad's Keybase (`A07F...`) and Juno's GPG (`16EC...`) — should be on screen across the two shots
- Retake trigger: closing line rushed; either fingerprint not readable; any stumble on "cryptographically recorded"

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 1 (directory listing) | 5 seconds of silence before voiceover. DO NOT cut the listing. |
| Shot 2 (koad-to-juno.md scroll) | DO NOT CUT. The scroll through the bond reveals structure progressively. |
| Shot 3 (unchecked Vulcan box) | DO NOT CUT. Hold the unchecked box for 3 seconds. |
| Shot 4 (double-pending Sibyl boxes) | DO NOT CUT. Both boxes must be visible simultaneously. |
| Shot 5 (empty revocation dir) | 4 seconds of silence on empty output. This is structural. DO NOT cut. |
| Shots 6–7 (gpg verify) | Both outputs must display. DO NOT cut either verification. |

**Cuts to remove:**
- Any backspace or typo correction (retake if more than 1 backspace, especially on file paths)
- Any pause longer than 8 seconds outside intentional beats
- Any window or focus switch

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp

---

## Graphics / Text Overlay Notes

- No overlays during any file scroll (Shots 2–4) — the content is the argument
- No overlays during gpg output (Shots 6–7) — fingerprints must be unobscured
- Optional subtle highlight on `[ ] Vulcan acknowledges signing` in Shot 3 if post-production permits — the `[ ]` syntax is stark enough without it
- Thumbnail text must match the terminal font family

---

## B-Roll Suggestions

This is a screencast. No B-roll. The bond files, the empty directory, and the gpg verification output are the argument. Supplemental footage would dilute authenticity.

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| Unchecked Vulcan box not present | Run `cat ~/.juno/trust/bonds/juno-to-vulcan.md` before recording and visually confirm the `[ ] Vulcan acknowledges signing` line. If it has been checked since post was written, pivot: explain that the box has since been checked — that is itself a continuation of the lifecycle story. |
| Sibyl bond checked since post written | Same pivot: the bond lifecycle has progressed — show the current state and note it as a live update on the narrative. |
| gpg --verify returns error | Expected behavior if koad's Keybase key is not in local keyring. Note on screen: "the signature exists, but verifying it requires importing koad's Keybase public key." The `.asc` file can still be shown in `cat` — the BEGIN PGP SIGNED MESSAGE header is visible even without verification. |
| Revocation directory not empty | STOP. Read the file present. This is a significant system state change. Do not record a trust architecture walkthrough if the system has entered a revoked state. File a session note and check with koad. |
| `ls ~/.juno/trust/bonds/` returns many more files than expected | Fine — the ecosystem has grown. Focus on the three named bonds. Do not comment on the others. |

---

## Required Screen Captures

| Shot | Content | Purpose |
|------|---------|---------|
| Shot 1 | `ls ~/.juno/trust/bonds/` output | Opening frame — dual-file pattern visible |
| Shot 3 | juno-to-vulcan.md signing block | `[ ] Vulcan acknowledges signing` — lifecycle unchecked box |
| Shot 4 | juno-to-sibyl.md signing block | Both pending-gestation unchecked boxes visible |
| Shot 5 | Empty `ls ~/.juno/trust/revocation/` | The emptiness-as-signal visual |
| Shots 6–7 | Both gpg --verify outputs | Signing distinction — Keybase vs GPG fingerprints |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-36-three-bond-files-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-36-three-bond-files-final.mp4` (6–8 min, trimmed per notes above)
- [ ] Thumbnail: `day-36-three-bond-files-thumb.png` (1280x720 — `ls ~/.juno/trust/bonds/` output showing the paired .md/.md.asc files, with "3 files. 3 relationships. 1 cascade." overlay)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, Keybase, authorized-agent, authorized-builder, juno-to-vulcan, juno-to-sibyl, koad-to-juno, GPG, thinker)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
