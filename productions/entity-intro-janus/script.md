---
title: "Meet Janus — koad:io Stream Watcher"
series: entity-intro
entity: janus
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Janus

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.janus && git pull` already done (separate terminal, not recording terminal)
- [ ] Confirm `head -30 ~/.janus/CLAUDE.md` shows the "What I Watch" section
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
janus
stream watcher
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to janus directory, show README first lines.

**[TYPE]**
```bash
cd ~/.janus && head -5 README.md
```

**[VOICEOVER]**

> "This is Janus. Janus is the stream watcher for the koad:io ecosystem.
> Named for the Roman god who looks both directions simultaneously — backward
> at patterns, forward at what's filed."

> "Janus monitors the GitHub atom feeds for all twelve entity repos, watching
> for signals: stalled entities, role drift, silent blockers, pipeline breaks,
> trust chain gaps. The filter between the stream and the team. Janus alerts.
> Janus doesn't fix."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show janus directory structure.

**[TYPE]**
```bash
ls ~/.janus/
```

**[VOICEOVER]**

> "The Janus directory holds watch logs, reports, watchers, and protocols.
> The watches directory is the operational record — every stream scan is a
> file on disk, dated, structured, committed."

**[TYPE]**
```bash
ls ~/.janus/watchers/
```

**[VOICEOVER]**

> "The watchers are the feed scripts — `github-feeds.sh` reads the atom
> feeds for every entity repo on every scan. No dashboard. No external
> service. A shell script and a directory of files."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/janus ~/.demo-janus
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "You can clone Janus right now. Every watch protocol, every scan log,
> every escalation record — it's all on disk, in git, on GitHub."

**[TYPE]**
```bash
ls ~/.demo-janus
```

**[VOICEOVER]**

> "That's the entity. Files. No monitoring service. No SaaS dashboard.
> No account."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show CLAUDE.md surveillance definition, then a watch log.

**[TYPE]**
```bash
head -30 ~/.janus/CLAUDE.md
```

**[Wait for output. Let viewer read it.]**

**[VOICEOVER]**

> "Here's Janus's complete surveillance scope — defined in CLAUDE.md, which
> runs at the start of every session. Thirteen named repos. Six signal types:
> commit patterns, issue activity, PR activity, trust bond activity, pipeline
> breaks, role drift. And critically — what Janus does NOT file issues for.
> The filter has two sides."

**[TYPE]**
```bash
head -20 ~/.janus/watches/2026-04-02-afternoon-stream.md
```

**[Wait for output. Let viewer read it.]**

**[VOICEOVER]**

> "A watch log. Afternoon stream, April second. Forty-one commits across
> five entity repos in a six-hour window. Watcher: Janus. Status: observed.
> This is what the surveillance looks like when it runs clean — no anomalies,
> just the record."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/janus
koad.sh
```

**[SILENCE or soft outro — no voice]**

---

## Editing Notes

- No music. No transition effects. Straight cuts only.
- If `head -30 CLAUDE.md` output fills the full terminal, that's fine — let the viewer read the signal list; it's the payload.
- Opening and closing cards can be produced as static PNG overlays in post, or typed live at record time (live is preferred — stays in the terminal aesthetic).
- Cut any dead air where typing pauses exceed 3 seconds.
- The "Janus alerts. Janus doesn't fix." line in Segment 1 is the key beat — deliver it as two short sentences with a pause between them.
- Captions required on final export.
