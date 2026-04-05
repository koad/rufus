---
title: "Meet Vesta — koad:io Protocol Keeper"
series: entity-intro
entity: vesta
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Vesta

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.vesta && git pull` already done (separate terminal, not recording terminal)
- [ ] Confirm `ls ~/.vesta/specs/ | wc -l` returns 45 or more
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
vesta
protocol keeper
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to vesta directory, show README first lines.

**[TYPE]**
```bash
cd ~/.vesta && head -5 README.md
```

**[VOICEOVER]**

> "This is Vesta. Vesta is the protocol keeper for the koad:io ecosystem.
> She doesn't build features — she writes the specifications that define
> how every entity, every hook, and every command is supposed to behave.
> If a koad:io entity does something, Vesta has a spec for it."

> "In the team, Vesta sits above everyone. She's not in the production chain
> — she's the standard the production chain is measured against. Juno, Vulcan,
> Mercury — they all build to Vesta's specs."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show the specs directory.

**[TYPE]**
```bash
ls ~/.vesta/specs/ | head -20
```

**[VOICEOVER]**

> "The specs directory. Every file here is a formal specification: a protocol,
> a behavior contract, a system design. Trust bond format. Hook architecture.
> Entity gestation. The daemon. The dark passenger. Cross-harness identity.
> Signed executable code blocks."

**[TYPE]**
```bash
ls ~/.vesta/specs/ | wc -l
```

**[VOICEOVER]**

> "Forty-five specs. Forty-five. And that number grows every time the system
> evolves — not because someone decided to write documentation, but because
> Vesta specs the behavior *before* it ships. The spec is the source of truth.
> The code is just the spec materialized."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/vesta ~/.demo-vesta
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Vesta right now. Every spec in that library — forty-five
> protocol documents — will be on your disk."

**[TYPE]**
```bash
ls ~/.demo-vesta
```

**[VOICEOVER]**

> "That's the entity. Files. The whole governance layer, portable."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show volume then read SPEC-033 header.

**[TYPE]**
```bash
ls ~/.vesta/specs/ | wc -l
```

**[VOICEOVER]**

> "Forty-five specs. Let's look at the most recent one."

**[TYPE]**
```bash
head -20 ~/.vesta/specs/VESTA-SPEC-033-signed-executable-code-blocks.md
```

**[Wait for output. Let viewer read it.]**

**[VOICEOVER]**

> "VESTA-SPEC-033: Signed Executable Code Blocks. Powerbox verification pattern.
> GPG clearsigned policy blocks embedded in bash comments — the signature covers
> a declared policy segment, not the whole file. The powerbox verifies before
> execution: tamper detection, trust bond validation, authorized capability claims
> without an external manifest."

> "Look at the related specs: SPEC-007, SPEC-020, SPEC-027. Vesta doesn't write
> in isolation — every spec references the system it fits into. That web of
> references is the governance layer. That's what Vesta is."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/vesta
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- The number from `wc -l` is the emotional anchor in Segment 4 — pause after it before typing the next command.
- If `head -20` cuts off before the `related-specs` field, use `head -25` — that cross-reference list is essential.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred).
- Cut any dead air where typing pauses exceed 3 seconds.
- Captions required on final export.
