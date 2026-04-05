---
title: "Meet Alice — koad:io Learning System"
series: entity-intro
entity: alice
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Alice

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.alice && git pull` already done (separate terminal)
- [ ] `cd ~/.chiron && git pull` already done (separate terminal)
- [ ] Confirm `ls ~/.chiron/curricula/alice-onboarding/levels/` shows level-00.md through level-12.md
- [ ] Confirm `head -10 ~/.chiron/curricula/alice-onboarding/levels/level-00.md` shows front matter
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
alice
learning system
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to alice directory, show README first lines.

**[TYPE]**
```bash
cd ~/.alice && head -5 README.md
```

**[VOICEOVER]**

> "This is Alice. Alice is koad:io's learning system and ambassador to the
> world. She is not part of the operational team. She is sent out, to find
> people who are ready, and walk them home."

> "Alice works in partnership with Chiron — the curriculum architect. Chiron
> designs the learning path. Alice delivers it. Thirteen levels, from first
> contact to full sovereignty."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show alice directory structure.

**[TYPE]**
```bash
ls ~/.alice/
```

**[VOICEOVER]**

> "Alice's directory contains her commands, her curriculum delivery system,
> her identity, and her memories. The key directory is curriculum — Alice
> is built from the ground up to deliver structured learning."

**[TYPE]**
```bash
ls ~/.alice/curriculum/
```

**[VOICEOVER]**

> "Her curriculum directory holds the delivery layer. The content itself lives
> in Chiron's directory — that's the architectural separation. Chiron designs.
> Alice delivers."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/alice ~/.demo-alice
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Alice right now. The delivery system comes with the entity."

**[TYPE]**
```bash
ls ~/.demo-alice
```

**[VOICEOVER]**

> "That's Alice. The curriculum is in Chiron. Let's look at what Chiron built."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show Chiron's alice-onboarding levels, then Level 0 head.

**[TYPE]**
```bash
ls ~/.chiron/curricula/alice-onboarding/levels/
```

**[Wait for output. Let viewer read the file names.]**

**[VOICEOVER]**

> "Thirteen levels. Level zero through level twelve. Each one a markdown file
> in Chiron's curriculum directory. This is the complete alice-onboarding
> journey — fully authored, not a stub."

**[TYPE]**
```bash
head -10 ~/.chiron/curricula/alice-onboarding/levels/level-00.md
```

**[Wait for output.]**

**[VOICEOVER]**

> "Level zero. Front matter: curriculum ID, curriculum slug, level zero.
> This is the entry point. The system is ready to receive a new human."

> "Alice delivers this. Chiron designs it. Together, they are how koad:io
> teaches itself to the world."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/alice
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- The `ls levels/` output showing thirteen files is the visual proof — let it sit for 3 seconds before VO. The viewer is counting.
- The Level 0 front matter read is the close — it proves the content is real and structured, not a placeholder file named level-00.md.
- "Alice delivers this. Chiron designs it." is the thesis — deliver it clearly, after the Level 0 read.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred).
- Cut any dead air where typing pauses exceed 3 seconds.
- Captions required on final export.

---

## Fallback for ls ~/.alice/curriculum/

If `~/.alice/curriculum/` is empty or does not exist, skip Shot 4 and go directly to the Chiron curricula demo. Adjust VO: "The curriculum lives in Chiron's directory — that's the architectural separation."
