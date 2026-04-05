---
title: "Meet Mercury — koad:io Publisher / Distributor"
series: entity-intro
entity: mercury
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Mercury

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.mercury && git pull` already done (separate terminal, not recording terminal)
- [ ] Confirm `cat ~/.mercury/SCHEDULE.md | head -30` produces expected output
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
mercury
publisher / distributor
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to mercury directory, show README first lines.

**[TYPE]**
```bash
cd ~/.mercury && head -5 README.md
```

**[VOICEOVER]**

> "This is Mercury. Mercury is the publisher and distributor for the koad:io
> ecosystem. Everything the team creates — research briefs, announcements,
> content drafts — ends up here before it reaches the outside world."

> "In the team workflow, Mercury sits at the end of the pipeline. Juno assigns
> content, Mercury drafts it, Veritas fact-checks it, Argus gates it, then
> Mercury publishes. The messenger is the message — how Mercury communicates
> IS the brand."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show distribution directory listing.

**[TYPE]**
```bash
ls ~/.mercury/distribution/
```

**[VOICEOVER]**

> "Mercury maintains a full distribution library — platform-specific packages
> ready to publish. Each one has been through the pipeline: drafted, verified,
> gated, staged. Nothing in this directory went straight from a Claude session
> to Twitter."

**[TYPE]**
```bash
ls ~/.mercury/ops/
```

**[VOICEOVER]**

> "The ops directory is Mercury's infrastructure layer: an incident log,
> incident response playbook, platform publisher spec, and a formal Veritas
> SLA. Mercury doesn't wing it — every platform has documented behavior."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/mercury ~/.demo-mercury
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Mercury right now. Every draft, every publish log, every
> posting rule — it's all on disk, in git, on GitHub."

**[TYPE]**
```bash
ls ~/.demo-mercury
```

**[VOICEOVER]**

> "That's the entity. Files. No social media dashboard. No API keys baked in.
> No account."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show the posting schedule and distribution queue.

**[TYPE]**
```bash
cat ~/.mercury/SCHEDULE.md | head -30
```

**[Wait for output. Let viewer read it.]**

**[VOICEOVER]**

> "Mercury's posting schedule isn't a suggestion — it's an operational
> constraint. Max three original posts per day across all platforms.
> Two-hour minimum gap between posts on the same platform. No originals
> between midnight and seven AM. Monday, Wednesday, Friday for original
> content. Tuesday and Thursday for engagement only."

**[TYPE]**
```bash
cat ~/.mercury/QUEUE-2026-04-03.md | head -25
```

**[Wait for output. Let viewer read it.]**

**[VOICEOVER]**

> "Here's a live distribution queue. Three drafts staged for review.
> Each one documents what Veritas needs to check and what Argus needs
> to gate before Mercury publishes. That's the discipline. Every post,
> the same path."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/mercury
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- If `head -25` output on the queue overruns the terminal, cut after the first draft entry — the pipeline structure is the payload, not all three drafts.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred — stays in the terminal aesthetic).
- Cut any dead air where typing pauses exceed 3 seconds.
- Captions required on final export.
