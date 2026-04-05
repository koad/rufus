---
title: "Shot List — The Governance Gap Nobody Planned For"
video: day-46-the-governance-gap-nobody-planned-for
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "The Governance Gap Nobody Planned For"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines (the gh issue views may be long)

### State verification (CRITICAL: verify all paths immediately before recording)
- [ ] `gh issue view 52 --repo koad/juno` — confirm: Janus escalation, April 4, 15 Sibyl commits in Vulcan repo, bond gap cited
- [ ] `gh issue view 48 --repo koad/vulcan` — confirm: audit signal, Janus origin
- [ ] `cat /home/koad/.juno/trust/bonds/juno-to-sibyl.md` — confirm: peer type, peer authorization clauses, explicit negative on subordination
- [ ] `cat /home/koad/.juno/trust/bonds/juno-to-vulcan.md` — confirm: authorized-builder type, explicit NOT authorized list including "initiate build projects without a Juno-filed GitHub Issue"
- [ ] `cat /home/koad/.juno/trust/bonds/juno-to-janus.md` — confirm: peer type, same structure as sibyl bond
- [ ] `git -C /home/koad/.vulcan log --oneline` — confirm: governance note commit visible (GOVERNANCE-NOTES.md in trust/)
- [ ] Audio check: quiet room, mic gain set
- [ ] OBS: single-monitor capture configured, no chat overlay

### What to know before recording

**The structural argument of this video:**

Two entities applied correct logic from their respective positions. Sibyl committed to Vulcan's repo under Juno's directive — the task chain was coherent, the authorization cascaded from koad through Juno. Janus audited the commits, found no bond covering the cross-entity scope, and filed an escalation. Both were correct. The gap was in the governance documents, not in either entity's reasoning.

The video's job is to show that gap on screen — not through narration, but through the three bonds rendered side by side, none of which covers the cross-entity case. Then show the resolution: one governance note commit, one format requirement. The detection mechanism is the story. The fix is deliberately small.

**The four technical facts to carry through the video:**

1. `koad/juno#52` — Janus escalation, filed 2026-04-04: 15 Sibyl commits in Vulcan's repo, no bond authorizes this in Vulcan's trust chain
2. The three bonds: juno-to-sibyl (peer), juno-to-vulcan (authorized-builder), juno-to-janus (peer) — none covers cross-entity commits from Sibyl to Vulcan
3. The governance note in `koad/vulcan/trust/GOVERNANCE-NOTES.md` — retroactive authorization for the April 3–4 bootstrapping session
4. The policy: `Directed by: koad/juno#NN` in cross-entity commit messages — one format requirement

**The tonal distinction from Day 44 and Day 45:**
- Day 44: forensic — examining a silent failure the record barely shows. Ends on unease.
- Day 45: reconstruction — examining a loop that worked, spec corrected same session. Ends on satisfaction.
- Day 46: investigative — the system found the gap while it was happening. Ends on confirmation. Not triumph. Not relief. The quieter feeling of a mechanism doing exactly what it was designed to do under conditions it wasn't specifically designed for.

**Key accuracy constraints:**
- Sibyl's 15 commits were authorized — the bootstrapping context establishes this. The gap was in documentation, not intent.
- Janus's escalation was correct — the peer bond does not cover cross-entity commits. The escalation was not a mistake or overreach.
- The resolution is specifically minimal: one governance note, one policy sentence. Do not overstate it.
- "The governance system found the gap itself." is the exact closing line — use verbatim.

---

## Shot 1: The Opening — Blank Terminal, The Signal

**Segment:** SEGMENT 1 (0:00–1:00)
**Duration:** 60 seconds

**What to show:**
Blank terminal. No commands. Narration only.

**Key delivery beats:**
- "On April 4th, Janus filed an issue." — flat statement. 3-second pause.
- "Janus checked the trust bonds." — 3-second pause. The weight is in what comes next.
- "The conclusion was one sentence: no trust bond authorizes this in Vulcan's trust chain." — 4 seconds of silence after. This is the audit finding. Let it register.
- "That sentence was correct." — 3-second pause.
- "And so was everything that led to the commits being there." — 5 seconds of silence. This is the full thesis. Both halves must land before evidence appears.

**Technical notes:**
- No commands in this segment
- The opening pair ("That sentence was correct. / And so was everything that led to the commits being there.") is the structural thesis. If either lands weakly, retake.
- Retake trigger: any pause shorter than 4 seconds after "no trust bond authorizes this"; the closing line rushed

---

## Shot 2: The Escalation — THE FIRST MONEY SHOT

**Segment:** SEGMENT 2 (1:00–2:30)
**Duration:** 90 seconds

**What to run:**
```bash
gh issue view 52 --repo koad/juno
```

**Expected output:**
The Janus escalation issue. Title naming the 15 Sibyl commits. Body: observed behavior (commits), entities involved (Sibyl, Vulcan), bond review result (no authorization in Vulcan's trust chain), question for Juno (are these authorized?). Filed 2026-04-04.

**CRITICAL HOLD:** 10 seconds of silence after output renders. Do not narrate. The viewer reads the issue. The escalation language is the evidence.

**Key delivery beats (after hold):**
- "That is an audit report." — flat. 3-second pause.
- "And no action taken beyond the filing." — 4 seconds of silence.
- "That waiting is not passivity. It is the correct behavior for an auditor in a system where an auditor's authority is bounded." — 4 seconds of silence.

**Then:**
```bash
gh issue view 48 --repo koad/vulcan
```

**Hold 8 seconds. Then:**
- "The audit signal on Vulcan's repo. The escalation filed on Juno's. Two issues. One question." — 4 seconds of silence.

**Technical notes:**
- If `gh issue view` output is very long (comments, long body), use `--json title,body,state,createdAt | jq '.title, .body'` to isolate signal
- The two issues together show the two-hop escalation chain — signal on Vulcan's repo, escalation on Juno's repo
- Retake trigger: hold shorter than 8 seconds; narration begins before viewer can read the issue; "passivity" line delivered with any apologetic tone for Janus's behavior

---

## Shot 3: The Three Bonds — THE STRUCTURAL CENTER

**Segment:** SEGMENT 3 (2:30–5:00)
**Duration:** 150 seconds

**This is the core visual sequence. Three bonds. Same screen layout. Each rendered fully. Each held for reading. The gap is visible only when all three are read together.**

**Bond 1:**
```bash
cat /home/koad/.juno/trust/bonds/juno-to-sibyl.md
```

**Hold 8 seconds. Viewer reads: peer type, coordination authorization, explicit negative ("Peer bonds do not grant financial authority, key access, or the right to issue bonds on behalf of the other."). No cross-entity commit clause.**

**After hold:**
> "Peer. Coordination, not delegation. No clause covering commits to a third-party repository."

*(pause — 4 seconds of silence)*

**Clear screen. Bond 2:**
```bash
cat /home/koad/.juno/trust/bonds/juno-to-vulcan.md
```

**Hold 8 seconds. Viewer reads: authorized-builder type, Juno-directed issue workflow, explicit NOT authorized list. Nothing about who else may commit to Vulcan's repo.**

**After hold:**
> "Authorized-builder. Receives Juno-directed assignments. Says nothing about who else is permitted to commit here."

*(pause — 4 seconds of silence)*

**Clear screen. Bond 3:**
```bash
cat /home/koad/.juno/trust/bonds/juno-to-janus.md
```

**Hold 8 seconds. Viewer reads: peer type, same structure as Sibyl bond. Authorizes filing, referencing, coordinating. Does not define audit scope, escalation authority, or action standing beyond filing and waiting.**

**After hold:**
> "Peer. Same structure as the Sibyl bond. The standing to file. Not the authority to act."

*(pause — 4 seconds of silence)*

> "Three bonds. None of them covers the cross-entity case."

*(pause — 5 seconds of silence)*

> "Not because they are incomplete. Because the situation they would have needed to cover did not exist until April 3."

*(pause — 4 seconds of silence)*

**Technical notes:**
- Clear screen between each bond — each bond gets a clean read. Do not let the previous bond's text remain visible when the next renders.
- The three bonds are individually coherent. The gap is not a defect in any bond. The viewer must arrive at this conclusion from reading, not from narration.
- The pivot line ("Three bonds. None of them covers the cross-entity case.") lands after the third bond's text has been on screen and the viewer has had time to see the pattern.
- Retake trigger: any bond held fewer than 6 seconds; the pivot line delivered before the third bond's hold is complete; "Not because they are incomplete" softened or qualified

---

## Shot 4: Why Both Entities Were Correct

**Segment:** SEGMENT 4 (5:00–6:30)
**Duration:** 90 seconds

**What to show:**
Blank terminal. No commands. Narration only.

**Key delivery beats:**
- "From Sibyl's position, the task chain was coherent." — 3-second pause. The claim is stated flatly, without hedge.
- "From Janus's position, the situation was equally coherent." — 3-second pause. This symmetry is the point.
- "Both entities were applying correct logic." — 4 seconds of silence. This is the structural claim distinguishing this from the previous two failure modes.
- "The gap was not in either entity's reasoning. The gap was in the space between them." — 5 seconds of silence.
- "That is the third failure mode." — slow. 3-second pause. Name it.
- The three-failure-mode taxonomy (engineering / specification / governance gap) — each item a distinct beat; 3 seconds between items.
- "The fix for a governance gap is escalation — not inference — and policy written from operational evidence." — 4 seconds of silence. This is the actionable principle.

**Technical notes:**
- No commands in this segment
- "Both entities were applying correct logic." must be delivered without hedging, without "arguably" or "effectively" — it is the plain statement
- The three-failure-mode taxonomy should feel like an enumeration, not a list — each type gets its own beat, not a recital
- Retake trigger: "Both entities were applying correct logic" delivered tentatively; the three failure modes recited as a list rather than named individually

---

## Shot 5: The Escalation Mechanism

**Segment:** SEGMENT 5 (6:30–7:45)
**Duration:** 75 seconds

**What to show:**
Blank terminal. Narration only.

**Key delivery beats:**
- "Consider what Janus could have done instead." — 3-second pause. Opens the counterfactual.
- The inference failure path: described carefully, with the implicit-precedent chain explained. 4 seconds of silence after.
- The revert failure path: "Sibyl's correctly-directed work would have been treated as unauthorized activity." — 4 seconds of silence.
- "The escalation was the right move." — flat. Not emphatic. Statement.
- "The mechanism worked because the entity knew where its authority ended." — slow. Flat. 5 seconds of silence. This is the key claim. Let it stand.

**Technical notes:**
- The two failure paths (inference and revert) are structural counterfactuals — present them with precision, not alarm. They are not near-misses. They are alternative paths that did not occur.
- "The entity knew where its authority ended." is the claim about bounded authority as a design feature. Do not rush it or reduce it to an incidental observation.
- Retake trigger: counterfactuals delivered with drama; "The mechanism worked because the entity knew where its authority ended" delivered with any triumph; any implication that Janus was unusually wise or exceptional

---

## Shot 6: The Resolution — THIRD TERMINAL SCENE

**Segment:** SEGMENT 6 (7:45–8:45)
**Duration:** 60 seconds

**What to run:**
```bash
git -C /home/koad/.vulcan log --oneline
```

**Expected output:**
The Vulcan git log. The governance note commit is present — a commit to `trust/GOVERNANCE-NOTES.md`. The commit message names Sibyl's authorized-researcher role for the April 3–4 bootstrapping session.

**CRITICAL HOLD:** 8 seconds of silence after output renders. Do not narrate. Let viewer locate the governance note commit. The rest of the log shows the ordinary development history — the governance note commit stands out by its location in the trust/ directory and its language.

**Key delivery beats (after hold):**
- "There it is." — flat. 4 seconds. Not triumphant.
- "A governance note committed to Vulcan's trust directory. Fifteen commits retroactively authorized." — 3-second pause.
- "And a policy. One format requirement: 'Directed by: koad/juno#NN' in the commit message or PR description." — 4 seconds of silence.
- "The gap was large enough to require a policy. The policy is small enough to fit in one line." — paired. Pause between. This is the deliberate understatement.

**Technical notes:**
- The governance note commit must be visible in the default `--oneline` output. If the log is very long, use `git -C /home/koad/.vulcan log --oneline | grep -i governance` to verify its presence before recording.
- "There it is." — same delivery as Day 45's use of this line: flat observation, not triumph. This is the resolution. It is small by design.
- Retake trigger: "There it is" delivered with any warmth or triumph; the policy sentence delivered rapidly; "The policy is small enough to fit in one line" delivered as self-deprecation

---

## Shot 7: The Record — Closing

**Segment:** SEGMENT 7 (8:45–9:30)
**Duration:** 45 seconds

**What to show:**
Blank terminal. No commands.

**Delivery map:**

| Line | Pause after |
|------|-------------|
| "Day 44: a hook routed to a machine with a dead API key and returned silence wearing the face of success. The fossil record barely shows it." | 4 seconds |
| "Day 45: a spec written before the implementation that falsified it. Six predictions wrong. Six corrections committed in the same session. The record shows the loop closing." | 4 seconds |
| "Day 46: two entities applying correct logic. A gap at the intersection of two correct behaviors. The audit mechanism found it, surfaced it through the correct channel, and waited for resolution." | 5 seconds silence |
| "Three failure modes. Three different mechanisms for catching them." | 3 seconds |
| "Engineering: the system breaks and the record shows it — or doesn't." | 2 seconds |
| "Specification: the implementation runs and reports back." | 2 seconds |
| "Governance: an auditor finds the edge of documented scope and escalates instead of inferring." | 5 seconds silence |
| "The bonds are real documents. The issue is in the record. The policy is committed. The fossil record is complete." | 4 seconds silence |
| "The governance system found the gap itself." | 6 seconds silence → cut to black |

**Technical notes:**
- The three-day summary is a brief recitation — not a recap, a taxonomy. Each day is one sentence, no more.
- The three failure mode taxonomy (Engineering / Specification / Governance) uses the same enumeration pattern from Segment 4, now completed. The viewer has seen the third item played out; the list names all three.
- "The governance system found the gap itself." — last line. No inflection. Statement. Cut to black in the silence, not on the final syllable.
- Retake trigger: any day's summary longer than two sentences; the final line delivered with any warmth or emphasis; silence shorter than 5 seconds before cut to black

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 2 (gh issue view 52 hold) | 10 seconds minimum. Do not fill. The issue text is the evidence. |
| Shot 2 (gh issue view 48 hold) | 8 seconds minimum. The two-issue chain must read. |
| Shot 3 (each bond hold) | 8 seconds per bond. Each bond gets a full read. No compression. |
| Shot 3 (post-"Three bonds. None of them covers the cross-entity case.") | 5 seconds. The pivot. Do not rush past it. |
| Shot 4 (post-"Both entities were applying correct logic.") | 4 seconds. The structural claim. |
| Shot 4 (post-"The gap was in the space between them.") | 5 seconds. |
| Shot 5 (post-"The mechanism worked because the entity knew where its authority ended.") | 5 seconds. Key claim. |
| Shot 6 (post-git log hold) | 8 seconds minimum. Governance note commit must be locatable. |
| Shot 6 (between "The gap was large enough" and "The policy is small enough") | 2 seconds. Paired lines. |
| Shot 7 (post-three-day summary) | 5 seconds silence. |
| Shot 7 (post-three failure modes) | 5 seconds silence. |
| Shot 7 (closing silence) | 6 seconds. Cut to black in the silence. |

**Cuts to remove:**
- Any backspace or typo correction on `gh issue view` commands or file paths
- Any pause longer than 12 seconds outside intentional beats
- Any verbal filler ("um", "so", "like", "right") — retake the segment

**No:**
- No zoom effects
- No lower-thirds or text overlays during bond reads (the text is the visual — do not annotate)
- No background music
- No speed ramp
- No B-roll
- No side-by-side layout tricks (bonds are read sequentially, with clear screen between — the gap emerges from the reading, not from a visual comparison tool)
- No annotations on the git log (viewer locates the governance note commit themselves)

---

## Graphics / Text Overlay Notes

- No overlays during terminal shots. The bond text, issue text, and git log are the evidence — do not annotate.
- Optional thumbnail frame: Shot 3, one of the three bond files rendered with the peer authorization clauses visible. Or Shot 7, blank terminal with closing line as overlay text.
- Thumbnail text options:
  - `The gap wasn't in any bond. It was between them.`
  - `Neither entity did anything wrong. — Day 46`
  - `The governance system found the gap itself.`

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `gh issue view 52 --repo koad/juno` returns error | Verify `gh auth status` on thinker; if authentication issue, note on camera and read the issue summary from the script — the argument stands |
| `gh issue view 48 --repo koad/vulcan` not accessible | Check repo access with `gh repo view koad/vulcan`; if unavailable, skip Shot 2b and note the gap — the main escalation (#52) is the primary evidence |
| Bond files moved or renamed | Check `/home/koad/.juno/trust/bonds/` with `ls`; if naming differs, read the actual files and note corrected names on camera |
| `git -C /home/koad/.vulcan log` does not show governance note | Run `git -C /home/koad/.vulcan pull` first; if still absent, reference the resolution from the script and note the commit is pending |
| `gh issue view` output very long (many comments) | Use `--json title,body,state,createdAt | jq -r '.title + "\n\n" + .body'` to isolate the original issue text without comment thread |

---

## Required Screen Captures

| Shot | Content | Purpose |
|------|---------|---------|
| Shot 2a | `gh issue view 52 --repo koad/juno` — Janus escalation issue | THE ESCALATION — audit finding, bond gap citation, bounded-authority waiting |
| Shot 2b | `gh issue view 48 --repo koad/vulcan` — audit signal | Two-issue chain: signal on Vulcan's repo, escalation on Juno's |
| Shot 3a | `cat juno-to-sibyl.md` — peer bond rendered | Bond 1 of 3 — peer authorization, no cross-entity commit clause |
| Shot 3b | `cat juno-to-vulcan.md` — authorized-builder bond rendered | Bond 2 of 3 — builder authorization, no third-party commit clause |
| Shot 3c | `cat juno-to-janus.md` — peer bond rendered | Bond 3 of 3 — audit peer authorization, standing to file and wait only |
| Shot 6 | `git -C /home/koad/.vulcan log --oneline` with governance note commit visible | THE RESOLUTION — retroactive authorization committed, policy in record |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-46-the-governance-gap-nobody-planned-for-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-46-the-governance-gap-nobody-planned-for-final.mp4` (8–10 min, trimmed per notes above)
- [ ] Thumbnail: `day-46-the-governance-gap-nobody-planned-for-thumb.png` (1280x720 — bond read with peer authorization language visible, or blank terminal with closing line)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, trust bond, Janus, Sibyl, Vulcan, Juno, peer bond, authorized-builder, cross-entity, escalation, governance note, GOVERNANCE-NOTES.md, fossil record, bounded authority, the governance system found the gap itself)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
