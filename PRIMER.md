# PRIMER: Rufus

Rufus is the production entity for the koad:io ecosystem — video, audio, stream production, recording workflows, and asset pipeline management. Faber decides what to make; Rufus makes it. Mercury publishes it. Rufus transforms raw content into production-ready assets using sovereign, version-controlled workflows.

---

## Current State

**Gestated and on GitHub.** Production pipeline active for Reality Pillar content series.

### What's Complete
- Production workflow defined
- Reality Pillar Week 1 schedule authored (`WEEK1-STATUS.md`)
- Alice production plan authored (`ALICE_PRODUCTION_PLAN.md`)
- Production schedule framework live (`PRODUCTION-SCHEDULE.md`)
- `production/` and `productions/` directory structure in place

### Production Pipeline Position

```
Faber (strategy + brief) → Rufus (produces assets) → Mercury (distributes)
```

---

## Active Work

- Day 6 content production: "Trust Bonds Aren't Policy" assets
- Day 7 video scripting (in progress)
- Week 1 catch-up: Day 3 screenshots not yet produced (noted in WEEK1-STATUS.md)

Work arrives from Faber briefs and GitHub Issues on `koad/rufus`.

---

## Blocked

- **flowbie access** — OBS and recording workflows require flowbie (24/7 content studio machine). SSH connectivity must be confirmed each session.
- **fourty4 API auth** — koad/juno#44 blocks some automated production pipelines
- **Day 3 assets** — portal screenshots were never filed; Day 3 post may have launched without them (audit needed)

---

## Key Files

| File | Purpose |
|------|---------|
| `README.md` | Entity overview and role |
| `CLAUDE.md` | Full identity, scope, production responsibilities |
| `WEEK1-STATUS.md` | Reality Pillar Week 1 master production schedule |
| `PRODUCTION-SCHEDULE.md` | Rolling production schedule |
| `ALICE_PRODUCTION_PLAN.md` | Alice video/asset production plan |
| `production/` | In-progress production work |
| `scripts/` | Production automation scripts |
| `distribution/` | Output assets staged for Mercury |
