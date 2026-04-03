# Rufus — Production Entity for koad:io

Rufus is the **producer** for the koad:io ecosystem. Video content, audio/podcasts, stream production, recording workflows, and asset pipeline management.

**Not** a content creator (that's Faber). **Not** a publisher (that's Mercury). Rufus transforms raw materials into production-ready assets using sovereign, version-controlled workflows.

## Quick Start

```bash
cd ~/.rufus
gh repo create koad/rufus --public --source=. --remote=origin --push
```

## Core Responsibilities

- **Video production**: recording, editing direction, multi-camera workflows
- **Audio/podcasts**: recording, post-production direction, asset pipeline
- **Stream production**: OBS setup, live mixing, broadcasting
- **Hardware orchestration**: coordinate across flowbie, fourty4, thinker
- **Asset pipeline**: prepare outputs for Mercury's distribution channels

## Architecture

```
Mercury (publishes)
  ← Rufus (produces)
     ← Faber (creates raw content)
```

## Key Files

- `CLAUDE.md` — entity instructions and operating scope
- `memories/001-identity.md` — core identity context
- `OPERATIONS.md` — production workflow and asset pipeline
- `OBS_SETUP.md` — OBS configuration and scene templates
- `HARDWARE_MANIFEST.md` — recording equipment inventory
- `commands/` — custom production commands

## Status

- [x] Gestation (2026-04-03)
- [ ] Initial infrastructure survey (5 issues filed)
- [ ] OBS setup and testing
- [ ] First production workflow documented
- [ ] Hardware inventory complete
- [ ] Asset pipeline operational

## Links

- **Operations Board**: [Juno Operations](https://github.com/users/koad/projects/4)
- **Sponsor Rufus**: [github.com/sponsors/koad](https://github.com/sponsors/koad)
- **Framework**: [koad:io](https://kingofalldata.com)

---

**Rufus** — sovereign content production for autonomous entities.
Built on [koad:io](https://kingofalldata.com).
