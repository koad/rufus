---
title: "Meet Salus — koad:io Entity Health"
series: entity-intro
entity: salus
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Salus

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.salus && git pull` already done (separate terminal, not recording terminal)
- [ ] Confirm `head -35 ~/.salus/CLAUDE.md` shows role description and healing protocol
- [ ] Confirm `ls ~/.salus/reports/` shows dated heal report files
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
salus
entity health
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to salus directory, show README first lines.

**[TYPE]**
```bash
cd ~/.salus && head -5 README.md
```

**[VOICEOVER]**

> "This is Salus. Named for the Roman goddess of safety and wellbeing. Salus
> is the healer of the koad:io ecosystem. She runs daily health checks on
> all twelve entities, fixes what she can directly, and escalates what she
> can't to Juno."

> "Salus works from two sources of truth. Argus's diagnosis tells her what's
> broken. Vesta's protocol tells her what healthy looks like. She sits between
> them — acting on their combined output."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show salus directory.

**[TYPE]**
```bash
ls ~/.salus/
```

**[VOICEOVER]**

> "Salus's directory contains her protocols, her memories, her heal reports,
> and her governance structure. The deliverable is the reports — one per day,
> one per incident, filed and committed."

**[TYPE]**
```bash
ls ~/.salus/reports/
```

**[VOICEOVER]**

> "Heal reports. April second, third, fourth — three consecutive days. Cascade
> environment verification. GitHub connectivity. Vesta spec audits. Vulcan-
> specific checks. This is not a single daily cron job — this is active
> incident response."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/salus ~/.demo-salus
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Salus right now. Her healing protocol and report history
> come with her."

**[TYPE]**
```bash
ls ~/.demo-salus
```

**[VOICEOVER]**

> "That's the entity. The healing protocol is in CLAUDE.md."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show Salus's CLAUDE.md role description and healing protocol.

**[TYPE]**
```bash
head -35 ~/.salus/CLAUDE.md
```

**[Wait for output. Let viewer read it.]**

**[VOICEOVER]**

> "Her CLAUDE.md. 'I am Salus — healer of the koad:io ecosystem.' Then
> the two sources of truth: Argus's diagnosis, Vesta's protocol."

> "And the healthy entity checklist — passenger.json, memories, hooks, comms
> inbox and outbox, recent git commit, GitHub repo accessible. Every entity
> in the system is measured against this list. Every day."

> "When entities drift, Salus corrects them. That is the job."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/salus
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- The CLAUDE.md output is text-dense — let it sit for 3–4 seconds before VO. The viewer needs time to read the healthy entity checklist table.
- The closing line ("when entities drift, Salus corrects them") is the thesis — deliver it clearly, after the checklist read.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred).
- Cut any dead air where typing pauses exceed 3 seconds.
- Captions required on final export.
