---
title: "Shot List — The Review Chain"
video: day-34-review-chain
production-owner: Rufus
hardware: thinker (primary)
status: production-ready
---

# Shot List: "The Review Chain"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text — no themes, no powerline, no decorations
- [ ] Font: JetBrains Mono or Fira Code at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only
- [ ] Clear scrollback before every take: `clear && printf '\033[3J'`
- [ ] Scrollback buffer: 10,000+ lines

### State verification (CRITICAL: pull both entity repos immediately before recording)
- [ ] `git -C ~/.veritas pull` — must be run immediately before the session, not the night before
- [ ] `git -C ~/.iris pull` — same
- [ ] `cat ~/.veritas/reviews/2026-04-05-day30-review.md` — confirm bond count finding present; confirm "19" is visible
- [ ] `cat ~/.iris/reviews/2026-04-05-day30-review.md` — confirm independent bond count flag present
- [ ] `cat ~/.veritas/reviews/2026-04-05-day24-review.md` — confirm "third delegation hop" NOT FOUND verdict present
- [ ] `cat ~/.iris/reviews/2026-04-05-day28-voice-review.md` — confirm gradient descent finding present
- [ ] `ls ~/.veritas/reviews/ | sort` — confirm review file listing is populated
- [ ] `gh auth status` — confirm GitHub CLI authenticated
- [ ] OBS armed at 1920x1080, 60fps, black background capture
- [ ] Mic check

### What to know before recording
- Day 30 bond count in post: 11 (wrong)
- Actual bond count at time of post: 19
- Error magnitude: understated by 8
- Veritas method: counted `.md` files in `~/.juno/trust/bonds/`
- Iris method: reasoned from team roster growth since founding batch
- Fabricated paper: arxiv:2501.09674
- Fabricated quote: "by the third delegation hop, there is no cryptographic link to the initiating agent or user"
- Quote status: does not appear in the paper (confirmed by Veritas full-text search)
- Other Day 24 corrections: Cloud Security Alliance attribution (actually Entro Security, Sept 2024); NIST attack vector misidentification
- Day 29 cost error: $24/month stated, $105/month actual
- Copia's role: accountant, budget ledger review — added to pipeline for posts with financial claims
- Argus/Salus entity health cycle (Day 6): 6/15 → 15/19 fully compliant; trust bond coverage 93% → 100%

---

## Shot 1: Empty Terminal — Opening Hook

**Segment:** SEGMENT 1 (0:00–0:30)
**Duration:** ~30 seconds

**What the screen shows:**
- Terminal. Prompt only. Nothing else.

**What to type:** Nothing.

**What to say:**
> "The Day 30 post stated: 'Eleven bonds signed.'"
>
> *(pause — 2 seconds)* "The actual count was 19."
>
> *(pause)* "Two reviewers flagged it. Neither knew the other had flagged it."
>
> *(pause)* "They arrived at the same finding. Through independent verification. Working from different scopes."
>
> *(pause — 2 seconds)* "That is what the review chain actually does."

**Technical notes:**
- Deliver the hook cold. No commands until Shot 2.
- State "The actual count was 19" flatly — do not editorialize. Let the convergence land.
- Retake trigger: any verbal stumble in the first four sentences.

---

## Shot 2: Veritas Day 30 Review — Bond Count Finding

**Segment:** SEGMENT 2 (0:30–1:15)
**Duration:** ~45 seconds

**What to type:**
```
cat ~/.veritas/reviews/2026-04-05-day30-review.md
```

**Expected output:** The Veritas Day 30 review, with the bond count finding prominently showing "19 bonds" and the file-counting methodology.

**What to say:**
> "Veritas ran the check by counting `.md` files in `~/.juno/trust/bonds/`."
>
> *(pause)* "Nineteen bonds. Not eleven. The count in the post was wrong by eight."

**Technical notes:**
- DO NOT CUT the scroll. Let the full review display.
- Hold on the bond count finding (wherever "19" appears) for 5 seconds before speaking.
- This is the first half of the convergence proof — it must be readable.
- Retake trigger: finding not visible at recording resolution.

---

## Shot 3: Iris Day 30 Review — Independent Bond Count Flag

**Segment:** SEGMENT 2 (1:15–2:00)
**Duration:** ~45 seconds

**What to type:**
```
cat ~/.iris/reviews/2026-04-05-day30-review.md
```

**Expected output:** The Iris Day 30 review, with the bond count flag — different methodology from Veritas (team roster reasoning rather than file counting).

**What to say:**
> "Iris arrived at the same finding — from a completely different angle. Not by counting files. By reasoning about the team roster: the founding batch was eleven, but the team had grown since."
>
> *(pause)* "Two review files. Two independent verdicts. Same error."
>
> *(pause)* "The post was corrected before publication."

**Technical notes:**
- DO NOT CUT the scroll. Let the full review display.
- Hold 5 seconds on the bond count flag before speaking.
- This is the second half of the convergence proof — two methods, one finding. The viewer needs to see both files in sequence.
- After this shot, the structural argument is complete. Move to Segment 3.

---

## Shot 4: Iris Day 28 Voice Review — Gradient Descent Finding

**Segment:** SEGMENT 3 (2:00–3:00)
**Duration:** ~60 seconds

**What to type:**
```
cat ~/.iris/reviews/2026-04-05-day28-voice-review.md | head -60
```

**Expected output:** The Day 28 voice review — the gradient descent / operational sense distinction, Iris's suggested fix.

**What to say:**
> "Iris and Veritas do not run the same check."
>
> *(pause)* "Veritas runs fact accuracy. Iris runs brand register: does this post speak to the right audience in the right voice?"
>
> *(pause)* "The Day 28 voice review caught something no fact-check would have caught."
>
> *(pause)* "The title 'The Hook Is the Training' did not earn its claim — the gradient descent sense versus operational sense distinction was underspecified. Engineers who know what gradient descent means would read the title as a stronger claim than the post was making."
>
> *(pause)* "That is not a factual error. It is a positioning error for the target audience. Veritas checking code paths would not have caught it."

**Technical notes:**
- Let the suggested fix ("The hook IS the training — not in the gradient descent sense, but in the operational sense") appear on screen before explaining what it catches.
- Hold on the suggested fix text for 3 seconds before moving on.

---

## Shot 5: Veritas Day 24 Review — The Fabricated Citation (MONEY SHOT)

**Segment:** SEGMENT 4 (3:00–4:15)
**Duration:** ~75 seconds

**What to type (deliberately, not fast):**
```
cat ~/.veritas/reviews/2026-04-05-day24-review.md
```

**Expected output:** The full Day 24 Veritas review — the "third delegation hop" NOT FOUND verdict, the Cloud Security Alliance/Entro Security attribution correction, the NIST attack vector misidentification.

**CRITICAL VISUAL:** The fabricated quote ("by the third delegation hop, there is no cryptographic link to the initiating agent or user") and the NOT FOUND verdict must both be readable on screen simultaneously, or in immediate succession. This is the emotional center of the video.

**What to say:**
> "The Day 24 post cited arxiv:2501.09674."
>
> *(pause)* "Real paper. Correct authors. Right area of research."
>
> *(pause)* "The post included a direct quote."
>
> *(pause — let viewer find it on screen)*
>
> "'By the third delegation hop, there is no cryptographic link to the initiating agent or user.'"
>
> *(pause — 2 seconds)*
>
> "That sentence does not appear in the paper."
>
> *(pause — 2 seconds)*
>
> "Veritas ran a full-text search. The phrase 'third delegation hop' — not found. The quoted language — not found. The paper is real. The topic is right. The quote was plausible. It did not exist in the source."
>
> *(pause)* "The fabricated attribution was removed before Day 24 published."
>
> *(pause)* "Same review session. Same post. Veritas also caught: the 97% figure misattributed to Cloud Security Alliance (actually Entro Security, September 2024). The NIST attack vector characterization that misidentified the attack type."
>
> *(pause)* "Multiple corrections. One review."

**Technical notes:**
- TYPE THE COMMAND DELIBERATELY. Do not rush. This is the shot the whole video builds toward.
- DO NOT CUT the scroll. The full review must display.
- DO NOT cut after the fabricated quote appears and before the "not found" verdict appears.
- If font size makes the quote run off-screen: reduce to 14px for this shot only, then restore.
- Retake trigger: cut during the review scroll. Quote and verdict not simultaneously or immediately visible.

---

## Shot 6: Copia — Scope Boundary Illustration

**Segment:** SEGMENT 5 (4:15–4:45)
**Duration:** ~30 seconds

**What to type:**
```
ls ~/.copia/ 2>/dev/null && echo "Copia entity — accountant, budget ledger review" || echo "Copia: accountant entity — added to pipeline for posts with financial claims"
```

**Expected output:** Either Copia directory listing or the echo fallback — both communicate that Copia is a real, scoped entity.

**What to say:**
> "The Day 29 post contained a cost figure: $24 per month. The actual running cost was approximately $105 per month."
>
> *(pause)* "Veritas did not catch it. Iris did not catch it."
>
> *(pause)* "Copia caught it — the accountant, checking the actual budget ledger."
>
> *(pause)* "The review chain catches what it is scoped to catch. The response was not to expand Veritas's scope to include financial auditing. The response was to add Copia to the pipeline."

**Technical notes:**
- Keep this segment clean and brief. The point is accurate scope description, not a failure story.
- If Copia directory exists and has review files, cat the relevant one instead.

---

## Shot 7: Review File Listing — The Fossil Record

**Segment:** SEGMENT 6 (4:45–5:30)
**Duration:** ~45 seconds

**What to type:**
```
ls ~/.veritas/reviews/ | sort | tail -10
```

**Expected output:** Review files, sorted, dated — the record of corrections on disk.

**What to say (slowest pacing in the video):**
> "The bond count error on Day 30 was caught twice before any reader saw it."
>
> *(pause)* "The fabricated quote on Day 24 was caught once."
>
> *(pause)* "The cost figure on Day 29 was caught by the specialist who was not yet in the chain."
>
> *(pause — 2 seconds)* "Each review file is on disk. Dated. With the verdicts and the correction text."
>
> *(pause)* "The chain leaves a fossil record."
>
> *(pause)* "Not of the published post."
>
> *(pause)* "Of what the published post was corrected from."

**Technical notes:**
- Each sentence = one breath, one pause. DO NOT compress.
- Let the review file listing display for 5 seconds before speaking.
- "The chain leaves a fossil record" is the close — it should land with weight. Do not rush into the final three lines.

---

## Shot 8: Fade / Cut to Black

**Duration:** 2–3 seconds

- No music
- Simple cut or 1-second fade

---

## Editing Notes

| Cut point | Note |
|-----------|------|
| Shot 1 (opening hook) | No typing. Empty terminal. |
| Shot 2 (Veritas Day 30) | DO NOT CUT scroll. Bond count finding must be readable. |
| Shot 3 (Iris Day 30) | DO NOT CUT scroll. Independent verdict must be readable. |
| Shot 5 (Day 24 fabricated citation) | DO NOT CUT. Quote AND verdict must be visible. This is the money shot. |
| Shot 7 (fossil record close) | DO NOT cut any pause. Every pause is structural. |

**Cuts to remove:**
- Any backspace or typo correction (retake if > 1 backspace)
- Any pause > 8 seconds outside intentional beats in Shot 7
- Any window or focus switch

**No:**
- No zoom effects
- No lower-thirds
- No background music
- No speed ramp

---

## Graphics / Text Overlay Notes

- No overlays during any review file scroll (Shots 2, 3, 5) — the review output is the argument, not decoration
- Optional: subtle highlight box around the fabricated quote in Shot 5 if post-production permits — not required, the text itself is stark enough
- Thumbnail text must match the terminal font family

---

## B-Roll Suggestions

This is a screencast. No B-roll. The review files on disk are the argument — fabricated citation, independent bond count convergence, Copia's cost correction. Supplemental footage would dilute the authenticity.

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `~/.iris/reviews/2026-04-05-day30-review.md` does not exist after git pull | Note the absence on screen. Show only Veritas Day 30 finding. The convergence story weakens but the Day 24 fabricated citation segment stands independently. |
| `~/.veritas/reviews/2026-04-05-day24-review.md` does not exist | STOP. This is the money shot. Do not record without it. File a GitHub Issue on koad/veritas to locate the review file. |
| Fabricated quote not visible at recording resolution | Reduce font to 14px for Shot 5 only. This segment requires both the quote and the verdict to be readable. |
| Take goes > 6 minutes | Tighten Shot 4 — deliver the Iris gradient descent finding as two sentences rather than the full explanation. |

---

## Required Screen Captures

| Shot | File | Purpose |
|------|------|---------|
| Shot 1 | Opening terminal — empty | Establish the cold open |
| Shot 2 | Veritas Day 30 bond count finding | First half of convergence proof |
| Shot 3 | Iris Day 30 bond count flag | Second half of convergence proof |
| Shot 5 | Veritas Day 24 — fabricated citation verdict | Primary evidence; thumbnail source |
| Shot 7 | Review file listing | Fossil record visual; close |

---

## Final Deliverables from This Session

- [ ] Raw recording: `day-34-review-chain-raw.mp4` (OBS) or `.cast` (asciinema)
- [ ] Edited cut: `day-34-review-chain-final.mp4` (4–6 min, trimmed per notes above)
- [ ] Thumbnail: `day-34-review-chain-thumb.png` (1280x720 — Veritas Day 24 review filling the screen, fabricated quote and NOT FOUND verdict visible, with "Real paper. Fake quote. Caught." overlay)
- [ ] Captions: auto-generated + manually reviewed (check: koad:io, Veritas, Iris, Copia, arxiv, Faber, Sibyl, NIST, Entro Security)
- [ ] Upload-ready: title, description, tags from script.md applied before Mercury hand-off
