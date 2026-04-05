---
title: "Meet Chiron — koad:io Curriculum Architect"
series: entity-intro
entity: chiron
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Chiron

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.chiron && git pull` already done (separate terminal, not recording terminal)
- [ ] Confirm `ls ~/.chiron/curricula/alice-onboarding/levels/` shows 13 files
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
chiron
curriculum architect
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to chiron directory, show README first lines.

**[TYPE]**
```bash
cd ~/.chiron && head -5 README.md
```

**[VOICEOVER]**

> "This is Chiron. Chiron is the curriculum architect for the koad:io ecosystem.
> He doesn't teach learners directly — he designs the structured learning paths
> that Alice delivers. Think of him as the entity responsible for *what* gets
> learned and in what order."

> "In the koad:io team, Chiron sits upstream of Alice. He receives input from
> Juno about what the ecosystem needs humans to understand. He writes the
> curriculum. Alice walks people through it."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show curricula directory structure.

**[TYPE]**
```bash
ls ~/.chiron/curricula/
```

**[VOICEOVER]**

> "Chiron maintains three curricula right now: Alice onboarding, advanced trust
> bonds, and entity operations. The primary one is Alice onboarding — a
> 13-level sequence that takes a person from zero to running their own sovereign
> agent infrastructure."

**[TYPE]**
```bash
ls ~/.chiron/curricula/alice-onboarding/
```

**[VOICEOVER]**

> "Each curriculum has levels, assessments, decisions, and a registry. The
> levels are markdown files — authored by Chiron, committed to git, versioned
> like code. Chiron doesn't build apps. He builds the map."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/chiron ~/.demo-chiron
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Chiron right now. Everything he knows, every curriculum he's
> authored, every decision he's logged — it's all on disk, in git, on GitHub."

**[TYPE]**
```bash
ls ~/.demo-chiron
```

**[VOICEOVER]**

> "That's the entity. Files. No service. No API. No account."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show the curricula levels and read level-00.

**[TYPE]**
```bash
ls ~/.chiron/curricula/alice-onboarding/levels/
```

**[VOICEOVER]**

> "Thirteen levels. Level zero through level twelve. Here's level zero — the
> entry point."

**[TYPE]**
```bash
cat ~/.chiron/curricula/alice-onboarding/levels/level-00.md | head -30
```

**[Wait for output. Let viewer read it.]**

**[VOICEOVER]**

> "Level zero is called The First File. The learning objective: add a PRIMER.md
> to a folder you care about and experience what happens when a Claude session
> walks through it. No account. No installation. No keys. One file."

> "That's Chiron's design philosophy: every level has one concrete action and a
> clear reason why. Thirteen levels. All on disk."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/chiron
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- If `head -30` output overruns visually, cut at the learning objective line — that's the payload.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred — stays in the terminal aesthetic).
- Cut any dead air where typing pauses exceed 3 seconds.
- Captions required on final export.
