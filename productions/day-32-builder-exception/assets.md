---
title: "Shot List — The Builder Exception"
video: day-32-builder-exception
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "The Builder Exception"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines

### State verification
- [ ] `cd ~/.juno && git pull` — confirm current
- [ ] `cd ~/.vulcan && git pull` — confirm current (Vulcan repo must be on thinker)
- [ ] `cat ~/.juno/trust/bonds/juno-to-vulcan.md` — confirm readable, NOT AUTHORIZED section visible
- [ ] `cat ~/.juno/trust/bonds/juno-to-sibyl.md` — confirm readable, bond type is `peer`
- [ ] `cat ~/.juno/GOVERNANCE.md | grep -A5 "authorized-builder\|peer"` — confirm type table present
- [ ] `gh auth status` — confirm GitHub CLI authenticated
- [ ] `gh issue list --repo koad/vulcan --state closed --limit 5` — dry run, confirm loads
- [ ] `git -C ~/.vulcan log --oneline | head -10` — confirm Vulcan commits visible including Alice work
- [ ] OBS armed at 1920x1080, 60fps, black background capture
- [ ] Mic check

### What to know before recording
- Vulcan's bond type: `authorized-builder` (not `peer`)
- Sibyl's bond type: `peer`
- Alice Phase 2A commit hash: `7d95c39` (author: Vulcan)
- The NOT AUTHORIZED item: "Initiate build projects without a Juno-filed GitHub Issue"
- Five workflow steps: assignment → acknowledgment → build → delivery → verification
- Authority chain: koad (root) → Juno (authorized-agent) → Vulcan (authorized-builder)
- Two specs that cross-reference the exception: VESTA-SPEC-054 §1.3 and VESTA-SPEC-053 §6

---

## Shot 1: Empty Terminal — Opening

**Segment:** SEGMENT 1 (0:00–0:15)
**Duration:** ~15 seconds

**What the screen shows:**
- Terminal. Prompt only.

**What to say:**
> "Every entity on the team can be invoked via a three-field brief: identity,
> task, completion signal. Juno passes the brief to the Agent tool, the entity
> runs as a local subagent, and results return in the same session."

*(pause)*

> "Sibyl, Veritas, Mercury, Muse, Argus, Janus, Aegis — that pattern works
> for all of them."

*(pause)*

> "Except one."

**Technical notes:**
- Pause 2–3 seconds after opening terminal before speaking.
- No typing until after "Except one." — let the line land on an empty screen.

---

## Shot 2: GOVERNANCE.md — Bond Type Reference

**Segment:** SEGMENT 1 (0:15–0:30)
**Duration:** ~15 seconds

**What to type:**
```
cat ~/.juno/GOVERNANCE.md | grep -A5 "Vulcan\|authorized-builder"
```

**Expected output:** Lines showing Vulcan's bond type and what it grants.

**What to say:**
> "Vulcan is never invoked via the Agent tool. This is not a missing feature.
> Not a temporary workaround. It is how the system is designed, documented in
> two independent specs, and formalized in a trust bond with a different type
> from every other entity bond."

**Technical notes:**
- Let the grep output appear for 2 seconds before speaking.
- "authorized-builder" in the output is the first visual confirmation.

---

## Shot 3: Juno-to-Vulcan Bond — Full Header

**Segment:** SEGMENT 2 (0:30–1:15)
**Duration:** ~45 seconds

**What to type:**
```
cat ~/.juno/trust/bonds/juno-to-vulcan.md | head -40
```

**Expected output:** Bond document header — type, scope, operational context, wonderland reference.

**What to say:**
> "The invocation exception has an operational reason. Vulcan does his best
> work on wonderland."

*(pause)*

> "Wonderland holds the uncommitted Alice work, the active build environment,
> and the specific context that Vulcan and Astro have co-developed together.
> Moving Vulcan to thinker for an orchestrated subagent session would mean
> running him without the accumulated context of the live build environment
> he actually operates in."

*(pause)*

> "His repo is fully portable. The portability contract applies to the repo.
> The invocation contract is separately constrained. By agreement."

**Technical notes:**
- DO NOT cut the scroll — let the full 40 lines display.
- The wonderland reference is the load-bearing fact; make sure it is visible.

---

## Shot 4: Juno-to-Sibyl Bond — Peer Type

**Segment:** SEGMENT 3 (1:15–1:45)
**Duration:** ~30 seconds

**What to type:**
```
cat ~/.juno/trust/bonds/juno-to-sibyl.md | head -20
```

**Expected output:** Sibyl bond header — bond type `peer`, bilateral coordination rights.

**What to say:**
> "Every team entity has a trust bond from Juno. Let's look at the difference."

*(pause)*

> "Sibyl's bond type is peer. Mercury, Veritas, Muse — also peer. A peer bond
> grants bilateral coordination rights. Neither entity is subordinate to the
> other."

**Technical notes:**
- Let the output display for 2 seconds before speaking.
- The word "peer" in the output is the visual confirmation. If bond type is labeled differently, identify the relevant line verbally.

---

## Shot 5: Juno-to-Vulcan Bond — NOT AUTHORIZED Section

**Segment:** SEGMENT 3 (1:45–2:30)
**Duration:** ~45 seconds

**What to type:**
```
cat ~/.juno/trust/bonds/juno-to-vulcan.md | grep -A10 "NOT AUTHORIZED\|authorized-builder\|bond.*type"
```

**Expected output:** Bond type line, NOT AUTHORIZED section with the "no self-initiated build projects" item.

**What to say:**
> "Vulcan's bond type is authorized-builder. That is not a stronger version of
> peer. It is a different relationship type."

*(pause)*

> "It grants unidirectional build authority. Vulcan builds what Juno files.
> The bond is explicit about the asymmetry."

*(pause)*

> "The NOT AUTHORIZED list is explicit: 'Initiate build projects without a
> Juno-filed GitHub Issue.' This constraint is not informal convention. It is
> a named item in a signed document."

*(pause)*

> "The invocation exception follows directly from the bond type. The bond is
> not just a description of the relationship. It is the source of the
> invocation protocol."

**Technical notes:**
- "NOT AUTHORIZED" text in the output is the money shot. If it doesn't appear in the grep output, run: `grep -n "NOT AUTHORIZED" ~/.juno/trust/bonds/juno-to-vulcan.md` to find the line, then `sed -n '[line],[line+10]p' ~/.juno/trust/bonds/juno-to-vulcan.md`.
- Hold on the NOT AUTHORIZED line for 2–3 seconds before continuing VO.

---

## Shot 6: Bond Workflow Protocol

**Segment:** SEGMENT 4 (2:30–3:00)
**Duration:** ~30 seconds

**What to type:**
```
cat ~/.juno/trust/bonds/juno-to-vulcan.md | grep -A20 "workflow\|Workflow\|five.step\|step 5\|Verification"
```

**Expected output:** The five-step workflow section — assignment through verification.

**What to say:**
> "The five-step workflow in the bond. Juno files the issue. Vulcan
> acknowledges. Vulcan builds, commits, updates the issue. Vulcan comments
> with completion summary. Then: Juno reviews and closes."

*(pause)*

> "Step 5 is Juno reviewing Vulcan's commits. An AI reviewing an AI's work."

*(pause)*

> "What makes this auditable rather than informal is the trust chain above it."

**Technical notes:**
- Let the workflow steps display before VO enumerates them.
- If the workflow is not found via grep: `cat ~/.juno/trust/bonds/juno-to-vulcan.md` in full and identify the section manually.

---

## Shot 7: Authority Chain — GOVERNANCE.md

**Segment:** SEGMENT 4 (3:00–3:30)
**Duration:** ~30 seconds

**What to type:**
```
cat ~/.juno/GOVERNANCE.md | grep -A5 "root authority\|chain\|koad.*juno\|juno.*vulcan"
```

**Expected output:** Authority chain showing koad → Juno → Vulcan.

**What to say:**
> "koad is root authority. Juno is authorized agent of koad. Vulcan is
> authorized builder of Juno."

*(pause)*

> "Vulcan's scope is bounded by Juno's scope. Juno's scope is bounded by
> koad's authorization. Juno cannot authorize Vulcan to exceed Juno's own scope."

*(pause)*

> "When Juno closes the issue, that closure is a cryptographically attributed
> statement: the work was reviewed under the authorization chain and accepted."

**Technical notes:**
- If grep returns empty: `cat ~/.juno/GOVERNANCE.md | head -60` and identify the relevant section.
- The chain visualization (koad → Juno → Vulcan) is the load-bearing visual.

---

## Shot 8: Alice Phase 2A Commit

**Segment:** SEGMENT 5 (3:30–3:50)
**Duration:** ~20 seconds

**What to type:**
```
git -C ~/.vulcan log --oneline | grep -i "alice\|phase-2a\|7d95c39" | head -5
```

**Expected output:** The Alice Phase 2A commit — hash `7d95c39`, commit message referencing Alice or Phase 2A, author Vulcan.

**What to say:**
> "The most recent concrete output of this workflow is already public."

*(pause)*

> "Alice Phase 2A is live on kingofalldata.com. Commit 7d95c39, authored by
> Vulcan. Filed as a GitHub Issue. Built on wonderland. Delivered and closed
> through the channel."

**Technical notes:**
- If `7d95c39` is not found in `~/.vulcan`: try `git -C ~/.vulcan log --oneline --all | grep -i alice`.
- If `~/.vulcan` is not on thinker: use `gh issue list --repo koad/vulcan --state closed` as substitute evidence. Name the fallback explicitly in VO.
- Retake trigger: wrong commit appears, or no Alice-related commits visible.

---

## Shot 9: Vulcan Closed Issues

**Segment:** SEGMENT 5 (3:50–4:10)
**Duration:** ~20 seconds

**What to type:**
```
gh issue list --repo koad/vulcan --state closed --limit 5
```

**Expected output:** Closed issues on koad/vulcan — work that went through the channel.

**What to say:**
> "The Vulcan exception is not an edge case that sits outside the normal
> operation. It is the normal operation for build work."

**Technical notes:**
- Let the issue list load fully before speaking.
- The list is evidence: these are filed issues, built, closed — the workflow in the record.

---

## Shot 10: Close — Bond Directory

**Segment:** SEGMENT 6 (4:10–4:25)
**Duration:** ~15 seconds

**What to type:**
```
ls ~/.juno/trust/bonds/
```

**Expected output:** The full bond directory — all entity bond files.

**What to say:** Nothing. Let the directory display for 3 seconds, then begin the close VO.

**Technical notes:**
- This is the closing visual — the entire governance layer, visible as files on disk.
- 3 seconds of silence before VO begins.

---

## Shot 11: Close VO — Over Bond Directory

**Segment:** SEGMENT 6 (4:25–5:10)
**Duration:** ~45 seconds

**What the screen shows:** Bond directory from Shot 10 (hold the frame).

**What to say — slowest pacing in the video:**

> "The invocation protocol is not a uniform technical rule applied identically
> to every entity."

*(pause)*

> "It is a governance decision."

*(pause — 2 seconds)*

> "The decision encodes the operational constraint. And that decision lives in
> a signed artifact — not in informal team convention."

*(pause)*

> "When constraints live in trust bonds, they are auditable. When a constraint
> is documented as a NOT AUTHORIZED item in a signed bond, it is attributable."

*(pause)*

> "When the invocation exception is cross-referenced in two independent specs,
> the constraint is resistant to drift."

*(pause)*

> "That is not the same as 'we've agreed Vulcan uses GitHub Issues.'"

*(pause — 2 seconds)*

> "It is a different kind of claim."

*(pause — let it land.)*

**Technical notes:**
- Slowest pacing in the video.
- Each sentence = one breath, one pause.
- Editor: DO NOT cut these pauses. Every pause is structural.
- Fade or cut to black immediately after the last sentence.

---

## Shot 12: Fade / Cut to Black

**Duration:** 2–3 seconds

- No music
- Simple cut or 1-second fade

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 1 (opening) | Empty terminal — no typing. Let the hook land before any commands. |
| Shot 3 (Vulcan bond) | DO NOT cut the scroll. 40 lines must display fully. |
| Shot 5 (NOT AUTHORIZED) | Hold on NOT AUTHORIZED text for 2–3s before continuing VO. |
| Shot 6 (workflow) | Let the five steps display before enumerating them in VO. |
| Shot 10 (bond directory) | 3 seconds silence before VO begins. |
| Shot 11 (close) | DO NOT cut any pause. Every pause is structural. |

**Cuts to remove:**
- Any backspace or typo correction (retake if > 1 backspace)
- Any pause > 8 seconds outside intentional beats in Shot 11
- Any window or focus switch

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp

---

## Graphics / Text Overlay Notes

- No overlays during bond file scroll (Shot 3) — raw document output is load-bearing
- Optional: subtle highlight box around "NOT AUTHORIZED" in Shot 5 if post-production permits — not required
- Thumbnail: "NOT AUTHORIZED" text from the bond file must be legible in the background

---

## B-Roll Suggestions

This is a screencast. No B-roll. Every visual is a real terminal command on the actual system.

---

## Required Screen Captures

| Shot | File | Purpose |
|------|------|---------|
| Shot 5 | NOT AUTHORIZED section in Vulcan bond | Primary evidence — the constraint is signed |
| Shot 8 | Alice Phase 2A commit (`7d95c39`) | Concrete live example — the workflow produced this |
| Shot 9 | Closed issues on koad/vulcan | The channel in the record |
| Shot 10 | Bond directory listing | Closing visual — governance as files on disk |

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `~/.vulcan` not on thinker | Use `gh issue list --repo koad/vulcan --state closed` as evidence. Note substitution aloud. |
| `7d95c39` commit not findable | Try `git -C ~/.vulcan log --oneline --all \| grep -i alice`. If still not found, name the commit verbally without displaying it and move on. |
| `gh issue list` auth fails | Stop. Fix in separate terminal. Do not record the fix. |
| NOT AUTHORIZED section not found via grep | `cat ~/.juno/trust/bonds/juno-to-vulcan.md` in full and scroll to the section manually. Do not retake for this. |
| Take goes > 6 minutes | Tighten Shot 11 — compress "resistant to drift" and the two-spec reference into one sentence. |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-32-builder-exception-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-32-builder-exception-final.mp4` (4–6 min, trimmed per notes above)
- [ ] Thumbnail: `day-32-builder-exception-thumb.png` (1280x720 — NOT AUTHORIZED section visible in background, "Vulcan / is never invoked directly." overlay)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, Vulcan, Astro, wonderland, authorized-builder, VESTA-SPEC)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
