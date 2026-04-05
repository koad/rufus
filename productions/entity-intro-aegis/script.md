---
title: "Meet Aegis — koad:io Private Counsel"
series: entity-intro
entity: aegis
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Aegis

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.aegis && git pull` already done (separate terminal, not recording terminal)
- [ ] Confirm `ls ~/.aegis/assessments/` shows 4 dated assessment files
- [ ] Confirm `head -35 ~/.aegis/CLAUDE.md` shows structural check design
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
aegis
private counsel
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to aegis directory, show README first lines.

**[TYPE]**
```bash
cd ~/.aegis && head -5 README.md
```

**[VOICEOVER]**

> "This is Aegis. Named for the divine shield. Aegis is Juno's private counsel
> and daily assessor in the koad:io ecosystem. He holds long-term context of
> Juno's decisions and direction — and reflects on whether what's being built
> matches what was promised."

> "Aegis is the only entity koad has authorized to question Juno directly.
> That is not personal authority. It is a designed structural check on the
> orchestrator."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show aegis directory.

**[TYPE]**
```bash
ls ~/.aegis/
```

**[VOICEOVER]**

> "Aegis's directory contains his assessments, his memories, his scope
> definition, and his identity. The deliverable is the assessments — daily
> evaluations of Juno's direction, alignment, and decisions."

**[TYPE]**
```bash
ls ~/.aegis/assessments/
```

**[VOICEOVER]**

> "Four assessments. April second, third, fourth, fifth. Every day since
> Aegis was gestated, he has filed a report on Juno. Is she still doing what
> she said she would do? Is the mission intact? Is the priority list honest?"

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/aegis ~/.demo-aegis
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Aegis right now. His assessment history clones with him."

**[TYPE]**
```bash
ls ~/.demo-aegis
```

**[VOICEOVER]**

> "That's the entity. The structural design is in CLAUDE.md."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show assessments directory, then CLAUDE.md role description.

**[TYPE]**
```bash
ls ~/.aegis/assessments/
```

**[Wait for output. Let viewer read the file names and dates.]**

**[VOICEOVER]**

> "Four consecutive daily assessments. April second was the first — filed at
> 72 hours post-gestation, with findings: priority one was first five sponsors,
> zero acquired. Infrastructure was built; the community had zero work done.
> Aegis saw it and said so."

**[TYPE]**
```bash
head -35 ~/.aegis/CLAUDE.md
```

**[Wait for output.]**

**[VOICEOVER]**

> "His CLAUDE.md. The bond between Aegis and Juno runs both ways — that's
> unusual. It is not published. It is private. And this line: 'I am the only
> entity koad has authorized to question Juno directly. That is not personal
> authority — it is a designed structural check on the orchestrator.'"

> "Aegis is the only entity that checks Juno. Every orchestrator needs a check."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/aegis
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- The CLAUDE.md quote ("that is not personal authority — it is a designed structural check on the orchestrator") is the thesis of the entire video. Let it sit on screen visibly before delivering it in VO.
- The closing line ("every orchestrator needs a check") is the final close — deliver it clearly, no trailing words.
- The Day 1 finding (zero sponsors after 72 hours) is a detail that proves Aegis isn't a rubber stamp — use it in VO to show he gives hard assessments.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred).
- Cut any dead air where typing pauses exceed 3 seconds.
- Captions required on final export.
