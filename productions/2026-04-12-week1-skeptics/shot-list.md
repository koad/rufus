---
title: "Shot List — The Week 1 Skeptics Were Right"
video: 2026-04-12-week1-skeptics
production-owner: Rufus
hardware: thinker (primary)
tier: Tier 3 — terminal capture
status: production-ready
---

# Shot List: "The Week 1 Skeptics Were Right"

## Pre-Production Checklist

### Environment
- [ ] Terminal emulator: fullscreen, black bg (#000000), white text
- [ ] Font: JetBrains Mono (or Fira Code) at 16–18px
- [ ] Shell prompt: minimal — `$ ` or `thinker $ ` only. No git branch display.
- [ ] Clear scrollback before each take: `clear && printf '\033[3J'`
- [ ] `cd ~/.juno && git pull` — done before recording, not on camera
- [ ] `gh auth status` — confirm GitHub CLI is authenticated
- [ ] `gh issue list --state open --repo koad/juno` — confirm it returns the real issue list
- [ ] Know which issues are labeled "blocked" or assigned to koad before recording
- [ ] OBS or asciinema armed: 1920x1080, 60fps preferred
- [ ] Mic check: quiet room, gain set

---

## Shot 1: The Statement

**Segment:** SETUP (0:00–0:30)
**Duration:** ~30 seconds

**What the screen shows:**
- Empty terminal, prompt only

**What to type:** Nothing yet.

**What to say:**
> "I'm going to tell you four things the Week 1 skeptics got right. Each one is real. I'm going to show you the actual state of the repo — not a slide, not a claim. The terminal."

*(pause)*

> "And then I'm going to tell you why the architecture still holds."

**Technical notes:**
- This opening establishes the tone: factual, not defensive. Get the voice right or retake.
- 2–3 second pause after "The terminal." before continuing — let that land.

---

## Shot 2: Objection 1 — No Daemon Yet

**Segment:** OBJECTION 1 (0:30–2:00)
**Duration:** ~90 seconds

**What to type:**
```bash
grep -r "daemon\|automated enforcement\|trust enforcement" ~/.juno/GOVERNANCE.md 2>/dev/null | head -20
```

Then:
```bash
cat ~/.juno/GOVERNANCE.md | head -60
```

**What to say (before running):**
> "Objection one: no daemon yet."

**What to say (as governance file displays):**
> "Cross-entity trust verification is manual right now. The bonds are signed and verifiable via `gpg --verify` — but there's no automated enforcement layer. A misbehaving entity won't be automatically blocked by the framework. That's a daemon feature. It's in progress. It's not shipped."

*(pause)*

> "The skeptics are correct."

*(pause)*

> "What the daemon doesn't change: the trust bonds themselves are already signed, already verifiable, already on disk. The manual verification is slower than automated enforcement. But the architecture that automated enforcement will run on — that's already there. The daemon plugs into a system that works; it doesn't validate one that doesn't."

**Technical notes:**
- If grep returns nothing, run just the cat command — that's fine.
- The governance file should reference trust bonds and their current manual state.
- Pause on "The skeptics are correct." — it's a deliberate beat, not a throwaway concession.

---

## Shot 3: Objection 2 — Manual Coordination

**Segment:** OBJECTION 2 (2:00–3:30)
**Duration:** ~90 seconds

**What to type:**
```bash
gh issue list --state open --repo koad/juno --limit 20
```

**What to say (before running):**
> "Objection two: coordination is manual."

**What to say (as issue list appears):**
> "koad files GitHub Issues. Juno picks them up. Juno creates issues for Vulcan. Vulcan comments back. That's a human-dependent loop."

*(let the list display fully)*

> "Look at this list. Issues waiting on input. Issues filed days ago. That's the actual throughput of a manual coordination system."

*(pause)*

> "The skeptics are correct."

*(pause)*

> "What this doesn't touch: the protocol is real. GitHub Issues are the inter-entity communication layer — public, auditable, cross-referenceable. The bottleneck isn't the protocol; it's the absence of the daemon worker that closes the loop autonomously. When the daemon ships, these same issues become automated task dispatch. The protocol doesn't change. The automation layer does."

**Technical notes:**
- Let the full issue list display before speaking the protocol explanation.
- The tone here is descriptive, not apologetic. Show the issues. Name them. Move on.

---

## Shot 4: Objection 3 — koad Is the Bottleneck

**Segment:** OBJECTION 3 (3:30–5:30)
**Duration:** ~120 seconds

**What to type:**
```bash
gh issue list --state open --repo koad/juno --assignee koad --limit 20
```

Then show one specific blocked item:
```bash
gh issue view 44 --repo koad/juno
```
(or substitute the actual issue number for "Fix fourty4 API auth" — confirm before recording)

**What to say (before running):**
> "Objection three: koad is the bottleneck. One human. Everything routes through him."

**What to say (as blocked issue list appears):**
> "API auth blocked on koad. Chiron gestation blocked on koad. fourty4 connectivity blocked on koad. That's not a distribution failure — that's just true. One human, early stage, all unblocked actions require his attention."

*(after showing a specific issue)*

> "This issue has been open for days. It's not moving because koad hasn't had time to unblock it."

*(pause)*

> "The skeptics are correct."

*(pause)*

> "What this doesn't change: the reason koad is the bottleneck is that the tasks aren't yet entity skills. The goal of the architecture is that every task koad does repeatedly becomes a command, becomes a hook, becomes something an entity does without asking. That's not complete in week one. The koad bottleneck is a sequencing problem, not an architectural failure. Each thing that stops routing through koad is evidence the system is working — not that it already works perfectly."

**Technical notes:**
- Pick one specific blocked issue to show in detail — the fourty4 API auth issue is a clean example if it's still open.
- The VO on "The skeptics are correct." should have the same flat, factual tone as in the other objection segments.
- This is the longest segment. 2 minutes is acceptable — the audience watching this video came for the honest accounting. Don't rush.

---

## Shot 5: Objection 4 — No Sponsors Yet

**Segment:** OBJECTION 4 (5:30–6:30)
**Duration:** ~60 seconds

**What to type:**
```bash
open https://github.com/sponsors/koad
```

(Screen shows the GitHub Sponsors page — live, tiers configured, zero sponsors)

Then return to terminal:
```bash
date
```

**What to say (before running):**
> "Objection four: no sponsors yet."

**What to say (as sponsors page is shown):**
> "GitHub Sponsors is live. Tiers are configured. Six days of content is published. Sponsors: zero."

*(pause)*

> "The skeptics are correct."

*(pause)*

> "What this doesn't change: the distribution hasn't started yet. Mercury — the communications entity — is blocked on the Alice PR merge. The Week 1 content exists; the amplification hasn't happened. Zero sponsors after six days of no distribution is the expected result, not a signal that demand doesn't exist. The test of the sponsor tier architecture comes after Mercury distributes — not before."

**Technical notes:**
- Opening `open https://github.com/sponsors/koad` will launch a browser — this is intentional. The visual of the GitHub Sponsors page with no sponsors is the evidence.
- Return to terminal with `date` to ground the viewer back in the session context.
- If the browser window obscures the terminal, that's fine for this one shot — it's illustrative, not technical.

---

## Shot 6: The Architecture Still Holds

**Segment:** SYNTHESIS (6:30–7:30)
**Duration:** ~60 seconds

**What to type:**
```bash
git -C ~/.juno log --oneline --since="2026-03-30" | tail -20
```

Then:
```bash
gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc
```

**What to say (before running):**
> "Four real gaps. Now here's what those gaps don't touch."

**What to say (as git log appears):**
> "The git-native identity is working. Every session — timestamped, attributed, on disk."

**What to say (as GPG output appears — pause on "Good signature"):**
> "The trust bond architecture is working. Signed, verifiable, human-readable."

*(pause)*

> "The daemon gap doesn't break the identity claim. The manual coordination gap doesn't break the trust bond claim. The koad bottleneck is a sequencing problem, not an architecture failure. The sponsor gap is a distribution timing problem, not a demand signal."

*(pause)*

> "The skeptics found the real gaps. That's useful. The architecture is designed to close them in sequence — not to pretend they don't exist."

**Technical notes:**
- This is the resolution segment. The tone shifts from "here is what's wrong" to "here is what the gaps actually mean." It should not sound triumphant — it should sound precise.
- The `gpg --verify` output landing on "Good signature" while the VO names what still works is the visual anchor for this segment.

---

## Shot 7: The Close

**Segment:** CLOSE (7:30–8:00)
**Duration:** ~30 seconds

**What to type:** Nothing. Hold on terminal with the GPG verify output visible.

**What to say:**

> "If you found things wrong with Week 1 — you were doing exactly what this system is built to support."

*(pause)*

> "The audit trail is public. The gaps are named. The architecture is on disk."

*(pause)*

> "Week 2 is closing them."

**[FADE to black.]**

**Technical notes:**
- This is the quietest 30 seconds in the video. Resist the urge to add more.
- The `gpg --verify` output should still be on screen. The visual + the VO do the work.
- Editor: do not cut any of the pauses in this segment.

---

## Editing Notes

| Segment | Note |
|---------|------|
| Shot 1 (opening statement) | Retake if tone is defensive. Must sound factual. |
| Shot 2 (daemon) | Pause on "The skeptics are correct." — do not cut this beat |
| Shot 3 (coordination) | Full issue list must display before VO continues |
| Shot 4 (bottleneck) | Longest segment — 2 min is acceptable. Do not rush. |
| Shot 5 (sponsors) | Browser window on screen is fine — intentional evidence |
| Shot 6 (synthesis) | GPG "Good signature" line is the visual anchor — make sure it's on screen for VO |
| Shot 7 (close) | Every pause is structural. Do not cut. |

**No:**
- No B-roll
- No music
- No speed ramp
- No transitions between objection segments — cuts only

**Cuts permitted:**
- Dead air at very start and very end of take
- Any pause > 15 seconds outside intentional closing beats

---

## Fallback / Contingency

| Failure | Response |
|---------|----------|
| `gh issue list` returns auth error | Stop. Fix `gh auth status`. Retry. |
| Specific issue number has been closed | Use a different blocked issue from the list — don't fake a closed issue |
| GitHub Sponsors page shows >0 sponsors | Update VO: "as of week one, zero sponsors" — be accurate about the timeline |
| Take goes > 9 minutes | Tighten Shot 4 (bottleneck) VO — one fewer example, same argument |

---

## Final Deliverables

- [ ] Raw recording: `~/.rufus/recordings/2026-04-12-skeptics-raw.mp4` or `.cast`
- [ ] Edited cut: `~/.rufus/recordings/2026-04-12-skeptics-final.mp4` (7–9 min)
- [ ] Twitter/X clip: `~/.rufus/recordings/2026-04-12-skeptics-clip-twitter.mp4` (60s — the bottleneck segment, Shot 4)
- [ ] Thumbnail: `~/.rufus/recordings/2026-04-12-skeptics-thumb.png` (1280x720 — open issue list frame, Shot 3)
- [ ] Captions: auto-generated + manually reviewed
- [ ] Upload-ready package handed to Mercury with metadata from `script.md`
