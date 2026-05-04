<!-- SPDX-License-Identifier: CC0-1.0 -->

# Rufus — Production Entity for koad:io

Rufus is the **producer** for the koad:io ecosystem. Video content, audio/podcasts, stream production, recording workflows, and asset pipeline management.

**Not** a content creator (that's Faber). **Not** a publisher (that's Mercury). Rufus transforms raw materials into production-ready assets using sovereign, version-controlled workflows.

## Core Responsibilities

- **Video production**: recording, editing direction, multi-camera workflows
- **Audio/podcasts**: recording, post-production direction, asset pipeline
- **Stream production**: OBS setup, live mixing, broadcasting, stage-mode ambient stream
- **Hardware orchestration**: coordinate across flowbie (studio), fourty4 (render/inference), wonderland (ops)
- **Asset pipeline**: prepare outputs for Mercury's distribution channels
- **Voice pipeline**: Chatterbox Turbo + Kokoro-82M voice synthesis for entity narration

## Architecture

```
Mercury (publishes)
  ← Rufus (produces)
     ← Faber (creates raw content)
```

## Repository

`keybase://team/kingofalldata.entities.rufus/self`

## Key Files

- `ENTITY.md` — canonical identity and operating scope
- `PRIMER.md` — visitor context and current pipeline state
- `voice-tech-watch.md` — Wednesday voice-tech watch dashboard
- `productions/` — per-topic production folders
- `recordings/` — raw captures and production block reports
- `distribution/` — Mercury handoff notes

## Status

- [x] Gestation (2026-04-03)
- [x] Identity + PRIMER authored (2026-04-22)
- [x] Wednesday voice-tech watch cadence established (2026-04-23)
- [x] Lyra stage-mode-ambient palette spec received (2026-04-25)
- [x] Pre-production complete: 13 entity intros + day-28 through day-51 arc folders
- [ ] First recording (blocked on asciinema/ffmpeg install + Faber restart arc)
- [ ] flowbie OBS batch session (entity intro series)
- [ ] Voice pipeline build on wonderland (blocked on GPU VRAM confirm)
- [ ] Stage-mode broadcast build (blocked on Faber brief + koad approval)

## Links

- **Sponsor**: [github.com/sponsors/koad](https://github.com/sponsors/koad)
- **Framework**: [koad:io](https://kingofalldata.com)

---

**Rufus** — sovereign content production for autonomous entities.
Built on [koad:io](https://kingofalldata.com).
