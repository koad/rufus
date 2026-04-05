---
title: "Meet Argus — koad:io Diagnostics"
series: entity-intro
entity: argus
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Argus

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.argus && git pull` already done (separate terminal, not recording terminal)
- [ ] Confirm `git log --author="Argus" --oneline -5` returns 5 results
- [ ] Confirm `head -30 ~/.argus/CLAUDE.md` shows role description including Mercury gate
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
argus
diagnostics
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to argus directory, show README first lines.

**[TYPE]**
```bash
cd ~/.argus && head -5 README.md
```

**[VOICEOVER]**

> "This is Argus. Named for the hundred-eyed giant of mythology — the one
> who sees everything and misses nothing. Argus is the diagnostics entity
> for the koad:io ecosystem. He examines entity directories, checks them
> against the koad:io protocol, and reports exactly what's wrong."

> "Argus does not fix. Salus fixes. Argus diagnoses. And he is the gate
> between Mercury's content pipeline and the outside world. Nothing reaches
> a platform without his verdict."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show argus directory and key structures.

**[TYPE]**
```bash
ls ~/.argus/
```

**[VOICEOVER]**

> "Argus's directory contains his diagnostic protocols, his gate logs, his
> diagnoses directory, and his memories. The work is in the diagnoses —
> structured reports on what's healthy and what's broken."

**[TYPE]**
```bash
ls ~/.argus/diagnoses/ 2>/dev/null || ls ~/.argus/
```

**[VOICEOVER]**

> "The quality chain runs: Argus diagnoses, Salus heals, Vesta defines what
> healthy looks like. Argus is the starting point. Without diagnosis, nothing
> gets fixed — and nothing gets published."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/argus ~/.demo-argus
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Argus right now. His diagnostic protocols and gate rules
> come with him."

**[TYPE]**
```bash
ls ~/.demo-argus
```

**[VOICEOVER]**

> "That's the entity. The proof of operation is in the git log."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show Argus's commits, then his CLAUDE.md role description.

**[TYPE]**
```bash
git -C ~/.argus log --author="Argus" --oneline -5
```

**[Wait for output. Let viewer read it.]**

**[VOICEOVER]**

> "Five recent commits by Argus. PRIMER injection. PID lock on hooks. Fresh
> sessions for tasks. Readme architecture. These are infrastructure commits —
> Argus building the watching infrastructure itself."

**[TYPE]**
```bash
head -30 ~/.argus/CLAUDE.md
```

**[Wait for output.]**

**[VOICEOVER]**

> "His CLAUDE.md self-description. 'The hundred-eyed giant who sees everything
> and misses nothing. That is the job.' And his standing assignment: nothing
> reaches a platform without his verdict."

> "Every system needs someone watching it. In this system, that's Argus."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/argus
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- The CLAUDE.md read contains the key quote — "hundred-eyed giant who sees everything and misses nothing" — let it sit on screen before delivering it in VO.
- The closing line ("every system needs someone watching it") is the thesis — deliver it clearly, after the CLAUDE.md quote.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred).
- Cut any dead air where typing pauses exceed 3 seconds.
- Captions required on final export.
