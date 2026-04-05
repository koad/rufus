---
title: "Meet the Entity — Series Format Spec"
owner: rufus
created: 2026-04-05
status: active
series-id: entity-intro
target-runtime: under 3 minutes
---

# Meet the Entity — Series Format Spec

Short introductions to every koad:io entity. Each video is a standalone unit: who this entity is, what it does, how to clone it, and a live demo proving it works. Under 3 minutes. Terminal-capture throughout.

**Purpose:** Show HN, Reddit, and newsletter audiences can't evaluate entities from a README. These videos do the work in one watch.

---

## Format Spec

### Runtime
- Target: **2:30–3:00**
- Hard ceiling: **3:15**
- No padding. No credits roll. No music bed.

### Capture Method
- **Tier 3 terminal-capture** throughout: asciinema recording exported to mp4 via `agg` or ffmpeg, OR OBS screen capture of full terminal window
- Resolution: 1920x1080 minimum
- Frame rate: 60fps preferred, 30fps acceptable
- Font: JetBrains Mono or Fira Code, 16–18px
- Terminal theme: pure black (#000000) background, white text — no syntax highlighting, no prompt decorations, no git branch indicators, no powerline
- Shell prompt stripped to: `$ ` or `host $ `
- Clear scrollback before every take: `clear && printf '\033[3J'`

### Opening Card
- **Duration:** 5 seconds (static frame, no animation)
- **Format:** Full black screen, centered white text
- Line 1: entity name in large monospace (e.g., `chiron`)
- Line 2: role in smaller monospace (e.g., `curriculum architect`)
- Line 3: `koad:io ecosystem` — small, bottom
- Produced as a static PNG overlaid in post, OR typed live in the terminal at record time

### Closing Card
- **Duration:** 10 seconds (static frame)
- **Format:** Full black screen, white text
- Line 1: `git clone https://github.com/koad/<entity>`
- Line 2: `koad.sh` or `canon.koad.sh`
- Same monospace aesthetic as opening
- Produced as static PNG or typed live

### Segment Structure

Every video follows the same four-segment structure, in order, with no exceptions:

```
[OPENING CARD]         5s
SEGMENT 1: Who         0:05–0:40    (~35s)  — identity and role
SEGMENT 2: What        0:40–1:30    (~50s)  — what the entity produces, how it fits the team
SEGMENT 3: Clone       1:30–2:00    (~30s)  — git clone live, ls, README.md first line
SEGMENT 4: Demo        2:00–2:50    (~50s)  — entity-specific demo
[CLOSING CARD]         10s
```

**Total budget:** 2:55 with cards. 2:40 bare runtime.

### Segment 1: Who (0:05–0:40)

**Screen:** Entity home directory, open README.md or CLAUDE.md first lines visible.

**Voice:**
- State the entity name
- State the single-sentence role
- State where it sits in the team workflow (who feeds it, who it feeds)

**Do not:** list features, explain koad:io, explain AI, mention competitors.

### Segment 2: What (0:40–1:30)

**Screen:** Key output files, directory listing, or a relevant file read.

**Voice:**
- Describe the concrete deliverables this entity produces
- Name the primary command or invocation pattern
- One sentence on why this matters to the ecosystem

### Segment 3: Clone (1:30–2:00)

**Screen:** Live `git clone https://github.com/koad/<entity> ~/.demo-<entity>` then `ls` then `cat README.md | head -5`.

**Voice:**
- "You can clone this entity right now."
- Read the clone command aloud as you type it
- Brief: "That's all you need to get started."

### Segment 4: Demo (2:00–2:50)

**Screen:** Entity-specific demo (defined per production record).

**Voice:** Narrate what is happening on screen. No speculation, no future features. Only what is visibly happening.

---

## Series Plan — All Entities

Priority order for production. First twelve are pre-production complete and ready to record.

| Priority | Entity | Role | Demo Type | Production Record |
|----------|--------|------|-----------|-------------------|
| 1 | **chiron** | Curriculum architect | `ls` curricula levels + `cat level-00.md` | `productions/entity-intro-chiron/` — pre-production complete |
| 2 | **sibyl** | Research director | Invoke with question, show output + git commit | `productions/entity-intro-sibyl/` — pre-production complete |
| 3 | **faber** | Content strategist | `ls` posts dir + `cat` post header | `productions/entity-intro-faber/` — pre-production complete |
| 4 | **vesta** | Protocol keeper | `ls specs/ \| wc -l` + `head` VESTA-SPEC-033 | `productions/entity-intro-vesta/` — pre-production complete |
| 5 | **muse** | Visual designer | `ls briefs/` + `head` Alice UI brief | `productions/entity-intro-muse/` — pre-production complete |
| 6 | **vulcan** | Builder | Closed issues + `git log --author="Vulcan"` on Alice | `productions/entity-intro-vulcan/` — pre-production complete |
| 7 | **juno** | Business orchestrator | `git log --author="Juno"` + `cat memories/001-identity.md \| head -20` | `productions/entity-intro-juno/` — pre-production complete |
| 8 | **livy** | Documentation lead | `ls docs/reference/` + `wc -l docs/reference/*.md` | `productions/entity-intro-livy/` — pre-production complete |
| 9 | **alice** | Learning system | `ls ~/.alice/` + `ls chiron curricula levels` + `head level-00.md` | `productions/entity-intro-alice/` — pre-production complete |
| 10 | **argus** | Diagnostics | `git log --author="Argus"` + `head CLAUDE.md` | `productions/entity-intro-argus/` — pre-production complete |
| 11 | **salus** | Entity health | `head CLAUDE.md` + `ls reports/` | `productions/entity-intro-salus/` — pre-production complete |
| 12 | **aegis** | Private counsel | `ls assessments/` + `head CLAUDE.md` | `productions/entity-intro-aegis/` — pre-production complete |
| 13 | **mercury** | Publisher / distributor | Show distribution queue or publish command | TBD |
| 14 | **veritas** | Quality and fact-check | Show a verification run on a brief | TBD |
| 15 | **janus** | Cross-boundary coordination | Show a cross-entity message or bridge call | TBD |
| 16 | **astro** | Framework exploration | Show a framework audit or probe | TBD |
| 17 | **rufus** | Media production | Show a production record being created | TBD |

---

## Naming Convention

- YouTube title format: `Meet Chiron — koad:io Curriculum Architect`
- File naming: `entity-intro-<entityname>/`
- Git tag on publish: `entity-intro/<entityname>/published`

---

## Handoff Protocol

1. Rufus marks `record.md` status as `production-ready`
2. koad records on thinker or flowbie
3. Rufus post-production checklist (trim, export, captions)
4. Mercury receives: `final.mp4`, `thumb.png`, YouTube title, description, tags
5. Mercury publishes to YouTube, clips for platform distribution
6. Rufus closes production record, commits final links

---

## Distribution Plan (per video)

| Platform | Format | Owner |
|---------|--------|-------|
| YouTube | Full video (under 3 min) | Mercury |
| Twitter/X | 60s clip | Mercury |
| r/LocalLLaMA | YouTube link + comment | Mercury |
| r/selfhosted | YouTube link + comment | Mercury |
| Show HN comment | YouTube link in thread | Juno |
