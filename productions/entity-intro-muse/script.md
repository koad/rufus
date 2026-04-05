---
title: "Meet Muse — koad:io Visual Designer"
series: entity-intro
entity: muse
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Muse

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.muse && git pull` already done (separate terminal, not recording terminal)
- [ ] Confirm `ls ~/.muse/briefs/` shows alice-ui-design-brief.md and dated briefs
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
muse
visual designer
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to muse directory, show README first lines.

**[TYPE]**
```bash
cd ~/.muse && head -5 README.md
```

**[VOICEOVER]**

> "This is Muse. Muse is the visual designer for the koad:io ecosystem.
> She doesn't write code — she writes design briefs. Every interface in the
> koad:io ecosystem that has been designed, Muse designed it first, in a file,
> before Vulcan built it."

> "In the team, Muse sits between Juno and Vulcan. Juno identifies what needs
> to be built. Muse designs what it should look like and how it should feel.
> Vulcan builds it. That's the sequence. Muse is why the build process
> starts with a design, not a guess."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show the briefs directory.

**[TYPE]**
```bash
ls ~/.muse/briefs/
```

**[VOICEOVER]**

> "The briefs directory. Every file here is a design brief: a complete visual
> and UX specification for a product or component. The koad homepage. The
> entity card component. The MVP Zone. The stream PWA. The Alice graduation
> certificate. The trust bond visualization. The blog layout."

> "Look at the dates — April second, third, fourth, fifth. Muse has been
> producing briefs every day since the ecosystem launched. The library grows
> with the product."

**[VOICEOVER continued]**

> "Each brief is in markdown — readable in any editor, committed to git,
> versioned alongside the code it informs. When Vulcan builds, there's a
> file on disk saying what it should look like. Always."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/muse ~/.demo-muse
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Muse right now. Every brief she's written — the full design
> library — comes with her."

**[TYPE]**
```bash
ls ~/.demo-muse
```

**[VOICEOVER]**

> "That's the entity. The design system is portable."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show full briefs library then read Alice UI brief header.

**[TYPE]**
```bash
ls ~/.muse/briefs/
```

**[VOICEOVER]**

> "The full library. Let's look at the one that's been referenced most —
> the Alice UI design brief."

**[TYPE]**
```bash
head -20 ~/.muse/briefs/alice-ui-design-brief.md
```

**[Wait for output. Let viewer read it.]**

**[VOICEOVER]**

> "Status: Updated, Chiron decisions incorporated. Audience: Vulcan and Juno.
> Entity: Muse. References: PROJECT-08, the koad:io design system, vulcan
> issue 36, Chiron's curriculum decisions."

> "This is what a design brief from an entity looks like. It knows who it's
> for. It knows what changed. It tracks the decisions that shaped it. When
> Vulcan built Alice, he built to this. The UI was designed before it was built."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/muse
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- In Segment 4, the VO over the brief header should move at reading pace — the viewer needs time to absorb the frontmatter fields.
- The closing line "The UI was designed before it was built" is the video's thesis statement — deliver it clearly, no rush.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred).
- Cut any dead air where typing pauses exceed 3 seconds.
- Captions required on final export.
