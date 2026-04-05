---
title: "Meet Vulcan — koad:io Builder"
series: entity-intro
entity: vulcan
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Vulcan

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.vulcan && git pull` already done (separate terminal, not recording terminal)
- [ ] Confirm `gh issue list --repo koad/vulcan --state closed | head -10` returns results
- [ ] Demo git log command ready (local clone or gh API fallback — see record.md)
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
vulcan
builder
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to vulcan directory, show README first lines.

**[TYPE]**
```bash
cd ~/.vulcan && head -5 README.md
```

**[VOICEOVER]**

> "This is Vulcan. Vulcan is the builder for the koad:io ecosystem.
> He receives work assignments from Juno — via GitHub Issues — and ships
> code to real repositories. Not prototypes. Not mockups. Production code,
> on GitHub, deployed."

> "In the team, Vulcan sits at the intersection of design and distribution.
> Muse writes the brief. Vulcan builds it. Veritas reviews it. Then Mercury
> distributes it. Vulcan is the entity that turns specifications into software."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show vulcan directory and key files.

**[TYPE]**
```bash
ls ~/.vulcan/
```

**[VOICEOVER]**

> "Vulcan's entity directory contains his identity, his commands, his issue
> tracking, and his build history. But the deliverables don't live here —
> they live in the repos he builds for."

**[TYPE]**
```bash
gh issue list --repo koad/vulcan --state open | head -5
```

**[VOICEOVER]**

> "GitHub Issues are Vulcan's work queue. Juno files issues. Vulcan builds.
> When the work is done, the issue closes. Let's look at what he's already
> shipped."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/vulcan ~/.demo-vulcan
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Vulcan right now. His identity, his commands, his issue
> context — all on your disk."

**[TYPE]**
```bash
ls ~/.demo-vulcan
```

**[VOICEOVER]**

> "That's the entity. But the real proof is in the repos he's shipped to."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show closed issues then Vulcan's commits on Alice.

**[TYPE]**
```bash
gh issue list --repo koad/vulcan --state closed | head -10
```

**[Wait for output. Let viewer read it.]**

**[VOICEOVER]**

> "Ten most recently closed issues. Build Alice UI. Blog infrastructure.
> Fix the hook bug. Accessibility fixes flagged by Veritas. Fix UX issues
> flagged by Veritas. Every CLOSED label is a task that went from filed
> to shipped."

**[TYPE]**
```bash
git -C ~/.demo-koadcom log --author="Vulcan" --oneline -5
```

**[Wait for output.]**

**[VOICEOVER]**

> "And here's Vulcan in the commit history of the Alice repository. Alice
> curriculum integration. Blog infrastructure. Alice Phase 2A. Mercury copy
> applied. Initial commit. That's not a plan. That's a production codebase
> with Vulcan's name on the commits."

> "Alice Phase 2A is live on kingofalldata.com right now. Vulcan built it."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/vulcan
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- The CLOSED issue list is the visual anchor in Segment 4 — let it sit on screen for a full 3 seconds before speaking. The viewer is reading.
- The commit log VO is the close — "that's not a plan, that's a production codebase" is the thesis. Deliver it clearly, no rush.
- If using the `gh api` fallback instead of local git log, the output format will differ — adjust VO to match what is actually on screen.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred).
- Cut any dead air where typing pauses exceed 3 seconds.
- Captions required on final export.

---

## Fallback Commands

If `~/.demo-koadcom` is not available during recording, use:

```bash
gh api 'repos/koad/kingofalldata-dot-com/commits?per_page=5' \
  --jq '.[].commit | "\(.author.name): \(.message | split("\n")[0])"'
```

Adjust VO: "Here's Vulcan's commit history on the Alice repository, pulled directly from GitHub."
