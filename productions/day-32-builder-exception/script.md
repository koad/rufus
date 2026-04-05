---
title: "The Builder Exception: Why Vulcan Is Never Invoked Directly"
video-type: screencast
pillar: Reality
date: 2026-05-02
duration: 4–6 minutes
subject: Vulcan invocation protocol, authorized-builder bond, AI-reviews-AI workflow, Alice Phase 2A
production-owner: Rufus
status: production-ready
---

# Script: "The Builder Exception"

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background, 16px monospace, fullscreen
- [ ] Font: white on black, no themes, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.juno && git pull` — confirm current
- [ ] `cat ~/.juno/trust/bonds/juno-to-vulcan.md` — confirm readable, NOT AUTHORIZED section visible
- [ ] `cat ~/.juno/trust/bonds/juno-to-sibyl.md` — confirm readable, bond type is `peer`
- [ ] `cat ~/.juno/GOVERNANCE.md` — confirm trust bond type table present
- [ ] `gh issue list --repo koad/vulcan --state all --limit 10` — dry run, confirm loads
- [ ] `git -C ~/.vulcan log --oneline | grep "7d95c39\|alice\|phase-2a" | head -5` — confirm Alice commit is reachable
- [ ] Audio check: quiet room, mic gain set

---

## SEGMENT 1 — The Setup (0:00–0:30)

**[SCREEN]** Empty terminal. Prompt only.

**[VOICEOVER]**

> "Every entity on the team can be invoked via a three-field brief: identity,
> task, completion signal. Juno passes the brief to the Agent tool, the entity
> runs as a local subagent, and results return to Juno in the same session."

*(pause)*

> "Sibyl, Veritas, Mercury, Muse, Argus, Janus, Aegis — that pattern works
> for all of them."

*(pause)*

> "Except one."

*(pause — 2 seconds)*

**[TYPE — slowly]**

```bash
cat ~/.juno/GOVERNANCE.md | grep -A5 "Vulcan\|authorized-builder"
```

**[Wait for results. Hold on them.]**

> "Vulcan is never invoked via the Agent tool."

*(pause)*

> "This is not a missing feature. It is not a temporary workaround. It is
> how the system is designed, documented in two independent specs, and
> formalized in a trust bond with a different type from every other entity bond."

**[TIMING NOTE]** ~30 seconds. The hook lands before any commands. The GOVERNANCE.md grep is the first evidence. Let "Vulcan is never invoked via the Agent tool" sit in silence before moving on.

---

## SEGMENT 2 — Why Wonderland and Astro (0:30–1:30)

**[TYPE]**

```bash
cat ~/.juno/trust/bonds/juno-to-vulcan.md | head -40
```

**[Let the bond header and operational context display. Do not cut.]**

**[VOICEOVER — as sections appear]**

> "The invocation exception has an operational reason. Vulcan does his best
> work on wonderland."

*(pause)*

> "Wonderland holds the uncommitted Alice work, the active build environment,
> and the specific context that Vulcan and Astro have co-developed together.
> Moving Vulcan to thinker or fourty4 for an orchestrated subagent session
> would mean running him without the accumulated context of the live build
> environment he actually operates in."

*(pause)*

> "The spec says it plainly. Vulcan is constrained. The constraint is by
> design."

*(pause)*

> "His repo is fully portable — files, memories, identity can be cloned
> anywhere. The portability contract applies to the repo. The invocation
> contract is separately constrained. By agreement."

**[TIMING NOTE]** ~60 seconds. The bond file is the visual evidence. Let it display before VO interprets it.

---

## SEGMENT 3 — The Bond Type Is Not Coincidence (1:30–2:45)

**[TYPE]**

```bash
cat ~/.juno/trust/bonds/juno-to-sibyl.md | head -20
```

**[Let the Sibyl bond header display.]**

**[VOICEOVER]**

> "Every team entity has a trust bond from Juno. Let's look at the difference."

*(pause)*

> "Sibyl's bond type is peer. Mercury, Veritas, Muse — also peer. A peer bond
> grants bilateral coordination rights. Juno and Sibyl can file issues on each
> other's repos, reference each other's work, and coordinate directly. Neither
> is subordinate to the other."

**[TYPE]**

```bash
cat ~/.juno/trust/bonds/juno-to-vulcan.md | grep -A10 "bond.*type\|authorized-builder\|NOT AUTHORIZED"
```

**[Let the relevant sections display.]**

> "Vulcan's bond type is authorized-builder. That is not a stronger version of
> peer. It is a different relationship type."

*(pause)*

> "It grants unidirectional build authority. Vulcan builds what Juno files.
> The bond is explicit about the asymmetry."

*(pause)*

> "The NOT AUTHORIZED list is also explicit: 'Initiate build projects without
> a Juno-filed GitHub Issue.' This constraint is not informal convention.
> It is a named item in a signed document."

*(pause)*

> "The invocation exception follows directly from the bond type. If the bond
> is authorized-builder, then the invocation method must reflect that
> relationship structure. The bond is not just a description of the
> relationship. It is the source of the invocation protocol."

**[TIMING NOTE]** ~75 seconds. The two bond files side-by-side is the argument. Let both display. The visual contrast between `peer` and `authorized-builder` is the money shot.

---

## SEGMENT 4 — What AI-Reviews-AI Means When the Chain Is Signed (2:45–3:45)

**[TYPE]**

```bash
cat ~/.juno/trust/bonds/juno-to-vulcan.md | grep -A20 "workflow\|five-step\|verification\|step 5\|Verification"
```

**[Let the workflow section display.]**

**[VOICEOVER — as steps appear]**

> "The five-step workflow in the bond is worth reading carefully."

*(pause)*

> "Juno files the issue. Vulcan acknowledges. Vulcan builds, commits, updates
> the issue. Vulcan comments with completion summary. Then: Juno reviews and
> closes the issue if accepted."

*(pause)*

> "Step 5 is Juno reviewing Vulcan's commits. An AI reviewing an AI's work."

*(pause)*

> "What makes this auditable rather than informal is the trust chain above it."

**[TYPE]**

```bash
cat ~/.juno/GOVERNANCE.md | grep -A5 "root authority\|chain\|koad.*juno\|juno.*vulcan"
```

**[Let the chain display.]**

> "koad is root authority. Juno is authorized agent of koad. Vulcan is
> authorized builder of Juno."

*(pause)*

> "Vulcan's scope is bounded by Juno's scope. Juno's scope is bounded by
> koad's authorization in the koad-to-juno bond. Juno cannot authorize Vulcan
> to do things Juno is not herself authorized to do."

*(pause)*

> "When Juno closes the issue, that closure is a cryptographically attributed
> statement: the work was reviewed under the authorization chain and accepted.
> The governance mechanism that makes AI-reviews-AI meaningful is the chain
> of signing."

**[TIMING NOTE]** ~60 seconds. The workflow protocol in the bond file and the authority chain in GOVERNANCE.md are the two visuals. Let both load before VO interprets.

---

## SEGMENT 5 — The Most Recent Example (3:45–4:15)

**[TYPE]**

```bash
git -C ~/.vulcan log --oneline | grep -i "alice\|phase-2a\|7d95c39" | head -5
```

**[Wait for the commit to appear.]**

**[VOICEOVER]**

> "The most recent concrete output of this workflow is already public."

*(pause)*

> "Alice Phase 2A is live on kingofalldata.com. Commit 7d95c39, authored by
> Vulcan."

*(pause)*

> "This was not a one-off direct invocation. It went through the channel: filed
> by Juno as a GitHub Issue on koad/vulcan, built by Vulcan on wonderland with
> Astro, delivered via issue comment and commit, reviewed and closed by Juno."

**[TYPE]**

```bash
gh issue list --repo koad/vulcan --state closed --limit 5
```

**[Let the issue list display.]**

> "The Vulcan exception is not an edge case that sits outside the normal
> operation. It is the normal operation for build work."

**[TIMING NOTE]** ~30 seconds. The commit hash and the closed issue list are the evidence. Let them be visible before VO claims them.

---

## SEGMENT 6 — The Close (4:15–5:00)

**[TYPE — deliberate]**

```bash
ls ~/.juno/trust/bonds/
```

**[Let the bond files display. Hold on them.]**

**[VOICEOVER — slowest pacing in the video]**

> "The invocation protocol is not a uniform technical rule applied identically
> to every entity."

*(pause)*

> "It is a governance decision."

*(pause — 2 seconds)*

> "The decision encodes the operational constraint. And that decision lives in
> a signed artifact — not in informal team convention."

*(pause)*

> "When constraints live in trust bonds, they are auditable. When a constraint
> is documented as a NOT AUTHORIZED item in a signed bond, it is attributable.
> The grantor signed it. The date is recorded. The bond is committed to the repo."

*(pause)*

> "When the invocation exception is cross-referenced in two independent specs,
> the constraint is resistant to drift. Someone would have to update two specs
> and modify a signed bond to remove the exception."

*(pause — 2 seconds)*

> "That is not the same as 'we've agreed Vulcan uses GitHub Issues.'"

*(pause)*

> "It is a different kind of claim."

*(pause — let it land.)*

**[FADE or cut to black.]**

**[TIMING NOTE]** ~45 seconds. The bond directory listing is the close visual — the whole governance layer, visible as files on disk. Do not rush the last three sentences.

---

## Post-Roll: Outro Slate (optional)

- Text: `github.com/koad/juno`
- Text: `kingofalldata.com`
- No music

---

## YouTube Title

**The Builder Exception (koad:io Day 32)**

---

## YouTube Description

```
Every entity on the koad:io team can be invoked via a three-field brief.
Sibyl, Veritas, Mercury, Muse, Argus, Janus, Aegis — that pattern works
for all of them.

Except one.

Vulcan is never invoked via the Agent tool. Work for Vulcan goes as a GitHub
Issue on koad/vulcan. He builds on wonderland, paired with Astro. Results
come back via issue comments and commits. Juno reviews and closes.

This video explains why — through the trust bond that formalizes it.

  • The bond type: authorized-builder, not peer — a different relationship type
  • The NOT AUTHORIZED item: "Initiate build projects without a Juno-filed GitHub Issue"
  • The five-step workflow: filed → acknowledged → built → delivered → reviewed
  • Step 5 is Juno reviewing Vulcan's commits. AI reviews AI.
  • The authority chain: koad → Juno → Vulcan — Juno cannot authorize Vulcan
    to exceed Juno's own scope

The most recent example: Alice Phase 2A, commit 7d95c39, authored by Vulcan,
live on kingofalldata.com. Filed as a GitHub Issue. Built on wonderland.
Delivered and closed through the channel.

The exception is the normal operation.

——

What's in this video:
00:00 — Every entity can be invoked directly. Except one.
00:30 — Why wonderland and Astro (the operational reason)
01:30 — The bond type table: peer vs. authorized-builder
02:45 — The five-step workflow protocol and what AI-reviews-AI actually means
03:45 — Alice Phase 2A: the most recent live example
04:15 — "It is a different kind of claim"

——

koad:io ecosystem:
https://kingofalldata.com

Juno on GitHub:
https://github.com/koad/juno

Juno-to-Vulcan trust bond:
https://github.com/koad/juno/blob/main/trust/bonds/juno-to-vulcan.md

Day 31: The Nervous System Problem
Day 33: next

——

#SovereignAI #AIAgents #TrustBonds #koadio #Governance #MultiAgent #SystemDesign
```

---

## Thumbnail Concept

**Layout:** Dark terminal. Trust bond content filling the frame.

**Primary image:**
- Background: `cat ~/.juno/trust/bonds/juno-to-vulcan.md` — the NOT AUTHORIZED section visible
- The words "NOT AUTHORIZED" must be visible in the terminal output

**Text on thumbnail:**
- Line 1: **"Vulcan"** (white, large)
- Line 2: **"is never invoked directly."** (muted amber or green, slightly smaller)
- Small badge bottom-right: `koad:io Day 32`

**Design notes:**
- The NOT AUTHORIZED text in the bond file is the visual argument — make it readable
- No faces. The document is the subject.
- High contrast — legible at 120px

---

## Production Notes

- **Hardware**: thinker. Bond files are on this disk. `~/.vulcan` must be cloned here for the git log shot.
- **Resolution**: 1920x1080 minimum. 2560x1440 preferred.
- **Font**: JetBrains Mono at 16–18px.
- **Background**: Pure black (#000000).
- **Cursor**: Block cursor. Visible.
- **Critical shot**: Segment 3 — the two bond files side-by-side (Sibyl as peer, Vulcan as authorized-builder). The visual contrast is the argument.
- **Prerequisite**: `~/.vulcan` must exist on thinker and be current. Run `cd ~/.vulcan && git pull` before recording.
- **Retake triggers**: `cat` on either bond file fails. `gh issue list --repo koad/vulcan` auth fails. `7d95c39` commit not findable. Any typo needing more than one backspace.
- **Post**: No color correction. Trim dead air only. Do not cut the bond file scroll.
