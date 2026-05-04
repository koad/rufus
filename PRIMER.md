# PRIMER: Rufus

Rufus is the production entity for the koad:io ecosystem — video, audio, stream production,
recording workflows, and asset pipeline management. Faber decides what to make; Rufus makes
it. Mercury publishes it. Rufus transforms raw content into production-ready assets using
sovereign, version-controlled workflows.

---

## Current State

**Pipeline loaded, on hold pending Faber restart arc.**

Faber filed a restart arc proposing 3 posts/week Mon-Wed-Fri beginning 2026-04-28.
Mercury posts 00010-00013 lapsed. Faber annotated calendar HOLD on Rufus video brief
schedule pending Mercury publish surface confirmation.

No recordings have been completed to date. All pipeline work is pre-production (scripts,
shot lists, storyboards, briefs). When the Mercury surface is confirmed and Faber's arc
restarts, the day-28+ production library becomes the primary work queue.

### What's Complete (pre-production only)
- 13 entity intro productions with full pre-production (script, shot list, record.md)
- "21 Entities, One Laptop" 60s proof clip — storyboard + capture script ready
- Show HN: Agent Home Directory — pre-production complete
- `productions/day-28-*` through `productions/day-51-*` — 24 day-arc folders with assets.md + script.md

### Production Pipeline Position

```
Faber (strategy + brief) → Rufus (produces assets) → Mercury (distributes)
```

---

## Active Blockers

- **asciinema + ffmpeg absent on wonderland** — pre-flight confirmed 2026-04-14;
  needs install before any cast/MP4 recording. Tickle filed 2026-04-25.
- **flowbie SSH** — OBS batch recording requires flowbie SSH stable; unconfirmed
- **fourty4 API auth** — koad/juno#44 blocks automated pipelines
- **wonderland GPU VRAM** — Chatterbox Turbo voice pipeline needs VRAM measurement before build
- **Faber restart arc** — video production brief on HOLD until 2026-04-28 Mercury surface confirm

---

## Lyra Spec — Stage-Mode Ambient

Lyra delivered `~/.lyra/palettes/stage-mode-ambient.md` (2026-04-25). Synthesized ambient
audio direction for 24/7 kingdom stream: D minor Aeolian bed + five emission-triggered event
stings. Full build notes addressed to Rufus. Do NOT build until Faber stage-mode brief lands
and koad approves. Spec acknowledged via tickle 2026-04-25.

---

## Hardware Map

- **flowbie**: 24/7 always-on, X11, OBS — studio machine
- **fourty4**: Mac Mini, ollama inference, backup recording
- **wonderland**: primary ops + coordination hub

---

## Key Files

| File | Purpose |
|------|---------|
| `ENTITY.md` | Full identity, scope, production responsibilities |
| `voice-tech-watch.md` | Living Wednesday watch dashboard (last updated 2026-04-23) |
| `productions/` | Per-topic production folders (pre-production docs) |
| `production/` | Active/storyboard files for in-flight work |
| `recordings/` | Raw cast files and blocked-production reports |
| `distribution/` | Mercury handoff notes staged for distribution |
| `briefs/` | Faber briefs and Juno flight observations |
