---
title: "Meet Veritas — koad:io Quality and Fact-Check"
series: entity-intro
entity: veritas
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Veritas

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.veritas && git pull` already done (separate terminal, not recording terminal)
- [ ] Confirm `ls ~/.veritas/reviews/ | wc -l` returns current review count
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
veritas
quality and fact-check
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to veritas directory, show README first lines.

**[TYPE]**
```bash
cd ~/.veritas && head -5 README.md
```

**[VOICEOVER]**

> "This is Veritas. Veritas is the fact-checker and quality officer for the
> koad:io ecosystem. Nothing factual leaves the team without passing through
> here. Not a blog post, not a research brief, not a public announcement."

> "Veritas sits between every creative entity and the outside world. Vulcan
> ships a build — Veritas checks it. Faber writes a post — Veritas reviews it.
> Mercury has a queue — Veritas signs off before Argus gates it."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show protocols and criteria directories.

**[TYPE]**
```bash
ls ~/.veritas/
```

**[VOICEOVER]**

> "The Veritas directory has the full verification stack: protocols for how
> reviews run, criteria for what passes, a claims registry, and the reviews
> themselves. Confidence levels are required on every finding — CONFIRMED,
> PROBABLE, SPECULATIVE, FLAGGED. No claim leaves without a level attached."

**[TYPE]**
```bash
ls ~/.veritas/protocols/
```

**[VOICEOVER]**

> "Veritas doesn't make judgment calls from memory — it has documented
> protocols for each review type. Factual claim verification, source
> credibility, scope alignment. Every review runs the same checklist."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/veritas ~/.demo-veritas
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Veritas right now. Every review protocol, every verification
> criteria, every review file — it's all on disk, in git, on GitHub."

**[TYPE]**
```bash
ls ~/.demo-veritas
```

**[VOICEOVER]**

> "That's the entity. Files. No external fact-checking service. No API. No
> human editor."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show the reviews directory count and a real review file.

**[TYPE]**
```bash
ls ~/.veritas/reviews/ | wc -l
```

**[VOICEOVER]**

> "Twenty-one reviews on disk. Every one of them is a real review of real
> team output."

**[TYPE]**
```bash
ls ~/.veritas/reviews/
```

**[Wait for output. Let viewer read the file names.]**

**[VOICEOVER]**

> "Mercury milestone announcements. Competitive claims. Sibyl research briefs.
> Faber posts. Kingofalldata homepage copy. Every team function represented."

**[TYPE]**
```bash
head -20 ~/.veritas/reviews/2026-04-04-faber-pipeline-review.md
```

**[Wait for output. Let viewer read it.]**

**[VOICEOVER]**

> "Here's the structure of a real review. Reviewer: Veritas. Files reviewed.
> Method: claims verified against live filesystem, git history, and GitHub
> Issues — repos pulled fresh before reading. That's the protocol. Every
> review, the same rigor."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/veritas
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- If `ls ~/.veritas/reviews/` output fills the terminal across multiple lines, that's a feature — the volume of reviews is the point.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred — stays in the terminal aesthetic).
- Cut any dead air where typing pauses exceed 3 seconds.
- Captions required on final export.
