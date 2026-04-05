---
name: Rufus Production Portfolio
description: Current state of Rufus's production output — schedules, entity intro series, video readiness
type: user
updated: 2026-04-05
---

# Rufus — Production Portfolio State

## Overview

Rufus launched as the production entity for koad:io. As of 2026-04-05, primary deliverables are: (1) the master production schedule for Reality Pillar videos, and (2) the entity intro series — pre-production complete for all 15 entities on the team.

---

## Master Production Schedule

**File:** `~/.rufus/PRODUCTION-SCHEDULE.md`  
**Status:** Active reference — koad opens this when scheduling recording sessions  
**Last updated:** 2026-04-05  
**Purpose:** "What do I record when I have 30 minutes / 60 minutes / 90 minutes?"

The schedule is organized by time available and prerequisites, not by calendar date. All 5 videos in Section 1 have complete scripts and shot lists and are ready to record.

---

## Reality Pillar Videos

### Section 1: Ready to Record (5 videos)

All scripts and shot lists are complete. No recording sessions have taken place yet — these are waiting on koad's availability.

| # | Video | Production Dir | Day | Runtime Target | Machine |
|---|-------|----------------|-----|----------------|---------|
| 1 | I Cloned a koad:io Entity | `productions/2026-04-05-clone-walkthrough/` | Day 5 | 5–8 min | thinker |
| 2 | The $200 Laptop Experiment | `productions/2026-04-07-200-dollar-laptop/` | Day 7 | 7–8 min | thinker (required) |
| 3 | Live Session: Sibyl Does Research | `productions/2026-04-07-sibyl-research/` | Day 7 | 6–8 min | fourty4 (required) |
| 4 | Show HN: Agent Home Directory | `productions/2026-04-10-show-hn-agent-home-directory/` | Day 10 | 4–6 min | thinker |
| 5 | The Week 1 Skeptics Were Right | `productions/2026-04-12-week1-skeptics/` | Day 12 | 7–9 min | thinker (OBS for browser shot) |

### Section 2: In Development (asset captures, not full videos)

| # | Production | Dir | Status |
|---|-----------|-----|--------|
| 1 | Trust Bonds — Day 6 screenshots | `productions/2026-04-06-trust-bonds/` | Asset brief complete (`assets.md`); screenshots not yet captured |
| 2 | How Entities Talk — Day 8 thread assets | `productions/2026-04-08-coordination/` | Shot list complete; screenshots not yet captured; Faber draft not started |

---

## Entity Intro Series

**Spec:** `~/.rufus/ENTITY-INTRO-SERIES.md`  
**Format:** Under 3 minutes per entity. Terminal-capture throughout. Script + shot list + record per entity.  
**Purpose:** Show HN / Reddit / newsletter audiences can evaluate entities without reading a README.

### Pre-production status

Pre-production (script + shot list + record) is complete for 15 entities. Recording has not begun — these are waiting on koad's availability.

**Complete pre-production (all 3 files: record.md, script.md, shot-list.md):**

| Entity | Production Dir |
|--------|----------------|
| juno | `productions/entity-intro-juno/` |
| livy | `productions/entity-intro-livy/` |
| alice | `productions/entity-intro-alice/` |
| argus | `productions/entity-intro-argus/` |
| salus | `productions/entity-intro-salus/` |
| aegis | `productions/entity-intro-aegis/` |
| vesta | `productions/entity-intro-vesta/` |
| muse | `productions/entity-intro-muse/` |
| vulcan | `productions/entity-intro-vulcan/` |
| chiron | `productions/entity-intro-chiron/` |
| sibyl | `productions/entity-intro-sibyl/` |
| faber | `productions/entity-intro-faber/` |
| mercury | `productions/entity-intro-mercury/` |

**Partial pre-production:**

| Entity | Status |
|--------|--------|
| veritas | `record.md` only — script and shot list pending |
| janus | Directory exists, empty — pre-production not started |

**Total entity intro records:** 15 entities covered in production directory, 13 with full pre-production complete.

---

## Week 1 Production Status

**File:** `~/.rufus/WEEK1-STATUS.md`  
**Summary:** Faber's blog posts for Days 3–9 were written and committed; Rufus did not produce companion screenshot assets for Days 3–4 before those days passed. Days 5 onward have production records and are ready to record.

---

## Alice Production Plan

**File:** `~/.rufus/ALICE_PRODUCTION_PLAN.md`  
**Status:** Planning phase — content pieces specified, no recording yet  
**Key pieces:** "Come Meet Alice" (5–10 min intro), Level 1 walkthrough (15–20 min), Graduation ceremony

---

## Post-Production Pipeline

Documented in `PRODUCTION-SCHEDULE.md` Section 5. Standard workflow:

1. Raw recording (`~/.rufus/recordings/YYYY-MM-DD-<slug>-raw.cast` or `.mp4`)
2. Review before export
3. Trim dead air
4. Export to MP4 via agg/ffmpeg
5. Export Twitter/X 60s clip
6. Extract thumbnail frame
7. Auto-captions via Whisper
8. Mercury handoff: `final.mp4` + `clip.mp4` + `thumb.png` + `captions.srt` + YouTube metadata

---

## Infrastructure Notes

**Recording machines:**
- **thinker:** Primary — most Reality Pillar videos record here; $200 laptop is the point
- **flowbie:** 24/7 always-on, X11, OBS; studio machine
- **fourty4:** Mac Mini; non-negotiable for Sibyl research video (local ollama inference)

**Key constraint:** fourty4 SSH must be confirmed working before scheduling any video that requires it. If fourty4 is down, reschedule — do not fake SSH steps.

---

## Upcoming Work

1. **Record the 5 ready-to-record videos** — blocked on koad's availability, not on pre-production
2. **Capture Day 6 trust bond screenshots** — 30-minute session on thinker; blocking Faber's Day 6 blog post assets
3. **Capture Day 8 coordination screenshots** — blocking Faber's Day 8 Twitter thread
4. **Complete veritas entity intro** — script and shot list needed
5. **Complete janus entity intro** — full pre-production needed
6. **Alice production** — "Come Meet Alice" and Level 1 walkthrough pending go-ahead
