---
title: "Three Bond Files, Three Relationship Types"
video-type: screencast
pillar: Reality
date: 2026-05-06
duration: 6–8 minutes
subject: trust bonds, governance, GPG, authorization, koad-to-juno, juno-to-vulcan, juno-to-sibyl, dual-file protocol, cascade revocation, signing asymmetry
production-owner: Rufus
status: production-ready
---

# Script: "Three Bond Files, Three Relationship Types"

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background, 16px monospace, fullscreen
- [ ] Font: white on black, no themes, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `git -C ~/.juno pull` — confirm current
- [ ] `ls ~/.juno/trust/bonds/` — confirm six specific files present: koad-to-juno.md, koad-to-juno.md.asc, juno-to-vulcan.md, juno-to-vulcan.md.asc, juno-to-sibyl.md, juno-to-sibyl.md.asc (plus additional bonds added since)
- [ ] `cat ~/.juno/trust/bonds/koad-to-juno.md` — confirm Keybase signing block visible, fingerprint A07F 8CFE CBF6 B982 EEDA C4F3 62D5 C486 6C24 7E00
- [ ] `cat ~/.juno/trust/bonds/juno-to-vulcan.md` — confirm unchecked "Vulcan acknowledges signing" box visible
- [ ] `cat ~/.juno/trust/bonds/juno-to-sibyl.md` — confirm double-pending signing block visible
- [ ] `ls ~/.juno/trust/revocation/` — confirm directory exists and is empty
- [ ] `gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc` — confirm verifiable signature
- [ ] `gh auth status` — confirm authenticated
- [ ] Audio check: quiet room, mic gain set

---

## SEGMENT 1 — The Directory (0:00–0:45)

**[SCREEN]** Empty terminal. Prompt only.

**[TYPE — deliberately]**

```bash
ls ~/.juno/trust/bonds/
```

**[Let the directory listing display. Pause — hold on screen for 5 full seconds before speaking.]**

**[VOICEOVER — slow, let the viewer read the listing first]**

> "Six files. Three bonds."

*(pause — 2 seconds)*

> "Every bond is two artifacts: a human-readable `.md` and a `.md.asc` — a GPG clearsigned copy of the same document."

*(pause)*

> "This is the dual-file protocol. One for reading, one for verifying."

*(pause)*

> "You can read a bond without its signature. You cannot assert authority with an unsigned `.md`. The `.asc` is not an attachment. It is the proof."

*(pause — 2 seconds)*

> "Day 24 built the scaffold — what bonds are conceptually, why GPG beats JWTs for agent authorization. This video skips the scaffold."

*(pause)*

> "Let me show you the actual files."

**[TIMING NOTE]** ~45 seconds. Type the `ls` command slowly — one character at a time, not rushed. The directory listing is the opening frame; let it breathe before the voiceover begins. The six specific files should be visible. If the listing is longer than expected (the directory has grown since this post was written), that's fine — the viewer will see the ecosystem has expanded. Don't comment on it; focus on the three bonds named.

---

## SEGMENT 2 — Bond One: The Root Grant (0:45–2:30)

**[TYPE]**

```bash
cat ~/.juno/trust/bonds/koad-to-juno.md
```

**[Let the full file scroll. Hold on the frontmatter — type: authorized-agent, from: koad, to: Juno, status: ACTIVE.]**

**[VOICEOVER — as frontmatter appears]**

> "Bond one: koad to Juno. Type: `authorized-agent`. This is where Juno's operating authority originates."

*(pause)*

**[Scroll slowly — hold on the Authorized Actions section]**

> "The authorized actions list is specific: file GitHub Issues on team repos, issue trust bonds to team entities at `authorized-builder` or `peer` level, spend up to $50 a month, gestate new entities."

*(pause)*

**[Scroll to the NOT authorized section — hold on the last prohibition]**

> "Equally specific is the prohibited list. The last item is structural: Juno cannot issue `authorized-agent` bonds to anyone. Only koad may do this."

*(pause)*

> "Juno can delegate downward. She cannot replicate her own grant type. The `authorized-agent` class is reserved for koad's direct issuance."

*(pause)*

**[Scroll to the Reporting Protocol section — hold on the last sentence]**

> "The reporting protocol contains one sentence worth reading carefully: 'Juno does not wait for approval on in-scope actions.'"

*(pause — 2 seconds)*

> "This is not a policy gate. The bond is the gate. Once signed, Juno acts."

*(pause)*

**[Scroll to the signing block — hold on it]**

> "The signing block:"

*(pause — let viewer read it)*

> "koad signs with Keybase PGP. Both sides hold a copy. The copy in `~/.koad-io/trust/` is koad's copy of his own authorization — filed in the framework directory, not just Juno's repo."

*(pause)*

> "The trust relationship is on both disks."

**[TIMING NOTE]** ~105 seconds. Scroll the file slowly — don't rush past the prohibited actions list or the signing block. The "Juno does not wait for approval" line is the structural reveal of this bond; pause 2 full seconds before the follow-on explanation. Both fingerprint lines in the signing block should be readable on screen.

---

## SEGMENT 3 — Bond Two: The Delegation Layer (2:30–4:15)

**[TYPE]**

```bash
cat ~/.juno/trust/bonds/juno-to-vulcan.md
```

**[Let the frontmatter appear — type: authorized-builder, from: Juno, to: Vulcan]**

**[VOICEOVER — as frontmatter appears]**

> "Bond two: Juno to Vulcan. Type: `authorized-builder`. Juno issues this one, under the authority she received from koad."

*(pause)*

**[Scroll to the Reporting Chain section — hold on it]**

> "The reporting chain is explicit in the bond text:"

*(pause — let viewer read the cascade)*

> "`koad → Juno → Vulcan`. Vulcan's actions are scoped by Juno's scope. Juno's scope is scoped by koad's authorization. Traceable to the root from any point in the chain."

*(pause)*

**[Scroll to the Workflow Protocol section — hold on all five steps]**

> "The bond is the spec. Not a separate document linked from the bond — the operating protocol is in the bond. Five steps: assignment, acknowledgment, build, delivery, verification. If you want to know how Vulcan operates, you read this file."

*(pause — 2 seconds)*

**[Scroll to the signing block — hold on it. The unchecked box is the visual anchor.]**

> "The signing block shows an asymmetry worth noting."

*(pause)*

> "Juno's signature: checked. Bond filed: checked. Copy filed in Vulcan's repo: checked."

*(pause)*

> "Vulcan acknowledges signing: unchecked."

*(pause — 2 seconds)*

> "The bond was filed and active before Vulcan's bilateral signing was complete. This is the normal lifecycle for a newly gestated entity — the issuing signature is sufficient for the bond to be active. Bilateral acknowledgment follows."

*(pause)*

> "An unchecked box is not an error. It is the bond telling you where in the lifecycle it is."

**[TIMING NOTE]** ~105 seconds. The unchecked acknowledgment box is the visual anchor of this segment — hold on it for 3 full seconds before speaking. Deliver "An unchecked box is not an error" as a standalone sentence with a beat before and after. The five-step workflow should be fully visible on screen as you describe it.

---

## SEGMENT 4 — Bond Three: The Lateral Layer (4:15–5:45)

**[TYPE]**

```bash
cat ~/.juno/trust/bonds/juno-to-sibyl.md
```

**[Let the frontmatter appear — type: peer]**

**[VOICEOVER — as frontmatter appears]**

> "Bond three: Juno to Sibyl. Type: `peer`. This is not a delegation. No authority flows downward. No subordination exists."

*(pause)*

**[Scroll to the Peer Relationship section — hold on the key sentence]**

> "The peer relationship section: 'Neither entity is subordinate to the other. Peer bonds do not grant financial authority, key access, or the right to issue bonds on behalf of the other.'"

*(pause)*

> "The scope is coordination — filing issues, referencing work, acting collectively in appropriate contexts. Lateral, not hierarchical."

*(pause)*

**[Scroll to the signing block — hold on the two unchecked boxes]**

> "The signing block here is double-pending."

*(pause — let viewer read the two unchecked boxes)*

> "Juno's signature: checked. Bond filed in Juno's repo: checked."

*(pause)*

> "Copy filed in Sibyl's repo: pending entity gestation. Sibyl acknowledges signing: pending gestation."

*(pause — 2 seconds)*

> "Sibyl did not exist when this bond was filed. The bond was written, signed by Juno, and committed to Juno's repo before Sibyl had keys, a directory, or a gestated identity."

*(pause)*

> "The relationship was defined unilaterally. Juno's side is signed and active. Sibyl's bilateral acknowledgment is deferred until gestation. When Sibyl is gestated and her keys generated, she inherits a bond that is already written and waiting."

*(pause — 2 seconds)*

> "Compare the two unchecked boxes in this bond to the one in the Vulcan bond. Different reason, same syntax. The file tells you."

**[TIMING NOTE]** ~90 seconds. Two unchecked boxes, both requiring explanation — pace the explanation of each one separately, not as a combined clause. The contrast between "pending gestation" and a simply-not-yet-signed acknowledgment is the structural point of this segment.

---

## SEGMENT 5 — The Cascade Clause and the Empty Directory (5:45–7:00)

**[TYPE — deliberately]**

```bash
ls ~/.juno/trust/revocation/
```

**[Hold on the empty output — no files, no entries. 4 full seconds of silence before speaking.]**

**[VOICEOVER — measured, not fast]**

> "The revocation directory. Currently empty."

*(pause — 2 seconds)*

> "If it ever contains a file, the operating state of the entity has changed in a fundamental way. The directory's emptiness is itself a signal."

*(pause)*

**[TYPE]**

```bash
grep "cascade\|all of Juno\|revoked\|downstream" ~/.juno/trust/bonds/koad-to-juno.md
```

**[Let the cascade clause appear on screen.]**

**[VOICEOVER]**

> "The root bond states it plainly: 'All of Juno's authority is derived from this bond. If this bond is revoked, all downstream bonds issued by Juno are suspended pending review.'"

*(pause — 2 seconds)*

> "Revoke the root, suspend the tree."

*(pause)*

> "The `juno-to-vulcan` bond has its own revocation clause — 'revocation is permanent' — but the cascade in the root bond means even that language is downstream of koad's ultimate authority."

*(pause)*

> "Peer bond revocation is contained. Revoking `juno-to-sibyl` affects only that lateral relationship. The hierarchy insulates itself from peer-layer disruption by design."

*(pause — 2 seconds)*

> "Three bond types. Three blast radiuses. The directory tells you all of this without any external documentation."

**[TIMING NOTE]** ~75 seconds. The empty `ls` output is the money shot of this segment — hold 4 full seconds of silence on it before speaking. The grep should pull the cascade clause; if it returns multiple lines, that's fine — let the viewer read them. "Revoke the root, suspend the tree" is a one-sentence structural summary; deliver it as a standalone beat with a 2-second pause before and after.

---

## SEGMENT 6 — The Signing Distinction (7:00–8:00)

**[TYPE — build it visually]**

```bash
gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc
```

**[Let the gpg output display. Hold on the key fingerprint and signer identity.]**

**[VOICEOVER — as the verification output appears]**

> "koad signs with Keybase PGP — `keybase@kingofalldata.com`. Keybase is an interactive process, tied to a verified public identity."

*(pause)*

> "Executing `keybase pgp sign` required koad to physically open Keybase and perform the action. It is not a bureaucratic formality. It is the moment at which sovereign intent is cryptographically recorded."

*(pause)*

> "The root bond exists because a human chose to make it exist."

*(pause — 2 seconds)*

**[TYPE]**

```bash
gpg --verify ~/.juno/trust/bonds/juno-to-vulcan.md.asc
```

**[Let the verification output display — Juno's GPG key, different fingerprint.]**

**[VOICEOVER]**

> "Juno signs with her own GPG key — generated during gestation via `koad-io gestate juno`, stored in `~/.juno/id/`. The signing is programmatic. Juno can sign bonds autonomously because the koad→Juno root bond already authorizes her to do so."

*(pause)*

> "Her authority to issue bonds is not assumed. It is derived and verifiable."

*(pause — 2 seconds)*

> "Two different keys. Two different fingerprints. The difference between them is not just technical."

*(pause)*

> "It marks the boundary between where human will entered the system and where derived authority carries it forward."

**[FADE or cut to black.]**

**[TIMING NOTE]** ~60 seconds. Both `gpg --verify` commands should run and display output on screen — this is the verification offer, the same pattern as showing commit hashes in Day 35. The Keybase fingerprint (`A07F 8CFE CBF6 B982 EEDA C4F3 62D5 C486 6C24 7E00`) and Juno's fingerprint (`16EC 6C71 8A96 D344 48EC D39D 92EA 133C 44AA 74D8`) must be readable. The closing line is the closing line of the post — deliver it at the slowest pace in the video. Do not rush after "human will entered the system."

---

## Post-Roll: Outro Slate (optional)

- Text: `github.com/koad/juno`
- Text: `kingofalldata.com/blog/series/reality-pillar`
- No music

---

## YouTube Title

**Three Bond Files, Three Relationship Types — Trust Architecture on Disk (koad:io Day 36)**

---

## YouTube Description

```
Six files in a directory. Three bonds.

koad→Juno (authorized-agent): the root grant, signed by koad via Keybase — 
the moment human will enters the system cryptographically.

Juno→Vulcan (authorized-builder): the delegation layer — the five-step 
workflow protocol embedded directly in the bond. The bond is the spec.

Juno→Sibyl (peer): a bond filed before Sibyl existed — two unchecked boxes 
that are not errors. They are the bond telling you where in the lifecycle it is.

This video walks the actual files on disk:
- The dual-file protocol: .md for reading, .md.asc for verifying
- The cascade clause: revoke the root, suspend the tree
- The revocation directory — empty, and the emptiness is the signal
- Keybase vs GPG: the boundary between human ceremony and derived authority

No abstractions. No diagrams. The files are the documentation.

"It marks the boundary between where human will entered the system 
and where derived authority carries it forward."

——

What's in this video:
00:00 — The directory: six files, three bonds
00:45 — koad→Juno: the root grant, Keybase signature, cascade clause
02:30 — Juno→Vulcan: authorized-builder, workflow-in-bond, the unchecked box
04:15 — Juno→Sibyl: peer bond, double-pending, pre-gestation
05:45 — The revocation directory: empty, and why that matters
07:00 — The signing distinction: Keybase vs GPG, human will vs derived authority

——

Bond files referenced (live on disk):
~/.juno/trust/bonds/koad-to-juno.md
~/.juno/trust/bonds/juno-to-vulcan.md
~/.juno/trust/bonds/juno-to-sibyl.md

Verify any signature:
gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc

koad:io ecosystem:
https://kingofalldata.com

Juno on GitHub:
https://github.com/koad/juno

Day 35: The Standing Directive
Day 37: Coming soon

——

#SovereignAI #TrustBonds #GPG #AIGovernance #koadio #AgentAuthorization #CryptographicTrust #EntityIdentity
```

---

## Thumbnail Concept

**Layout:** Dark terminal. The directory listing visible — six files, the `.md` and `.md.asc` pairs clearly showing the dual-file pattern.

**Primary image:**
- Background: `ls ~/.juno/trust/bonds/` output — the six files for three bonds arranged in pairs
- The three bond names readable: `koad-to-juno`, `juno-to-vulcan`, `juno-to-sibyl`

**Text on thumbnail:**
- Line 1: **"3 files."** (white, large)
- Line 2: **"3 relationships."** (amber)
- Line 3: **"1 cascade."** (white)
- Small badge bottom-right: `koad:io Day 36`

**Design notes:**
- The `.md` / `.md.asc` pairing visible in the listing rewards viewers who read thumbnails closely
- High contrast — all three lines legible at 120px
- Alternative: the unchecked box `[ ] Vulcan acknowledges signing` as the primary visual — the blank checkbox communicates incompleteness without needing explanation

---

## Production Notes

- **Hardware**: thinker. Juno repo is on this disk (confirm with git pull before recording).
- **Resolution**: 1920x1080 minimum. 2560x1440 preferred.
- **Font**: JetBrains Mono at 16–18px.
- **Background**: Pure black (#000000).
- **Cursor**: Block cursor. Visible.
- **Critical shots**: 
  - Segment 1: the `ls` output showing the six files — both partners of each pair readable
  - Segment 3: the unchecked `[ ] Vulcan acknowledges signing` box — must be on screen and readable
  - Segment 5: the empty `ls ~/.juno/trust/revocation/` output — hold 4 seconds of silence
  - Segment 6: both `gpg --verify` outputs — both fingerprints readable
- **Pre-recording required**: `git -C ~/.juno pull` — this is a live entity repo. Pull immediately before recording, not the night before.
- **Retake triggers**: 
  - Either fingerprint in Segment 6 not readable at recording resolution
  - Any cut during the `cat` scrolls in Segments 2, 3, or 4
  - Any verbal stumble on the closing line of Segment 6
  - The unchecked box in juno-to-vulcan not visible on screen
- **Post**: No color correction. Trim dead air only. DO NOT cut the file scrolls. DO NOT cut the empty revocation directory moment.
- **Fallback**: If `gpg --verify` produces an error rather than a signature confirmation, note it on screen — "we can see the file but the signing key is not in this keyring" — this is itself a teaching moment about key distribution. Do not skip Segment 6.
