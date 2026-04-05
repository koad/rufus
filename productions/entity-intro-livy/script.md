---
title: "Meet Livy — koad:io Documentation Lead"
series: entity-intro
entity: livy
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Livy

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.livy && git pull` already done (separate terminal, not recording terminal)
- [ ] Confirm `ls ~/.livy/docs/reference/` returns 9 files
- [ ] Confirm `wc -l ~/.livy/docs/reference/*.md` shows ~2903 total
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
livy
documentation lead
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to livy directory, show README first lines.

**[TYPE]**
```bash
cd ~/.livy && head -5 README.md
```

**[VOICEOVER]**

> "This is Livy. Named for Titus Livius — Rome's master historian. Livy is the
> documentation lead for the koad:io ecosystem. She documents everything a user
> or agent needs to know about how the system works."

> "In the team, Livy sits between the builders and the users. Vulcan ships code.
> Livy explains it. Vesta defines protocol. Livy records it. If it needs to be
> understood later, Livy wrote it down."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show livy directory and docs structure.

**[TYPE]**
```bash
ls ~/.livy/
```

**[VOICEOVER]**

> "Livy's entity directory contains her commands, her documentation library,
> and her reference archive. The deliverable is not in the code — it's in
> the docs."

**[TYPE]**
```bash
ls ~/.livy/docs/
```

**[VOICEOVER]**

> "The reference library is the core artifact. Structured documentation of
> every system layer: the daemon, the entities, the framework, the gestation
> process, the trust bond system. Let's look at what's in it."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/livy ~/.demo-livy
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Livy right now. Her full reference library clones with her."

**[TYPE]**
```bash
ls ~/.demo-livy
```

**[VOICEOVER]**

> "That's the entity. The docs are in docs/reference/."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show reference library contents then word count.

**[TYPE]**
```bash
ls ~/.livy/docs/reference/
```

**[Wait for output. Let viewer read the file names.]**

**[VOICEOVER]**

> "Nine documents. Daemon architecture. Entity directory structure.
> Framework layer. Gestation process. Operations architecture. Trust bond
> system. Each one a complete treatment of its subject."

**[TYPE]**
```bash
wc -l ~/.livy/docs/reference/*.md
```

**[Wait for output.]**

**[VOICEOVER]**

> "Two thousand, nine hundred and three lines. Across nine files. Trust bond
> system alone is six hundred and fifty-one lines. This is not a README.
> This is a reference library."

> "The documentation is the deliverable. Livy builds it."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/livy
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- The `ls docs/reference/` output is the visual anchor — let it sit 3 seconds before speaking. The viewer is reading the file names.
- The `wc -l` total is the close — read the total aloud: "two thousand, nine hundred and three lines." Deliver it without rushing.
- "The documentation is the deliverable. Livy builds it." is the thesis — final line, no trailing words.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred).
- Cut any dead air where typing pauses exceed 3 seconds.
- Captions required on final export.
