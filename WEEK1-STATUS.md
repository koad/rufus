---
title: "Reality Pillar — Week 1 Production Status"
period: "2026-04-03 to 2026-04-09"
owner: Rufus
last-updated: 2026-04-04
source-of-truth: ~/.faber/content-calendar/REALITY-2026-04-03.md
---

# Reality Pillar Week 1 — Master Production Schedule

**Mission:** Prove kingofalldata.com is not vaporware — living portal, entities doing real work, trust bonds on disk.

---

## Day 3 — Thursday, April 3
**"Portal Goes Live" — Launch Announcement**
**Type:** Blog post + social thread | **Owner:** Faber (writing) + Rufus (assets)

| | Status |
|---|---|
| **Content** | ⚠️ Not confirmed committed — Faber's post + social thread (check ~/.faber/posts/) |
| **Rufus Assets** | ❌ No production directory created — screenshots never filed |
| **Still Needed** | Clean portal screenshots; entity repo screenshots (showing recent commits); trust bond file preview with GPG signature visible |
| **Blocking** | **Rufus** — Apr 3 assets were not produced. Day already passed. Determine if post launched without assets or was delayed. |

---

## Day 4 — Friday, April 4 ← TODAY
**"Entities Are Running on Disk" — Technical Deep-Dive**
**Type:** Long-form blog post (2,000+ words) | **Owner:** Faber (writing) + Sibyl (technical review)

| | Status |
|---|---|
| **Content** | ⚠️ Not confirmed committed — Faber's post (check ~/.faber/posts/) |
| **Rufus Assets** | ❌ No production directory — no screenshots captured |
| **Still Needed** | Directory structure screenshots with permissions visible (per entity: ~/.faber, ~/.sibyl, ~/.rufus); sample trust bond with GPG signature block; entity trust chain diagram |
| **Blocking** | **Rufus** — assets must ship today for Day 4. Create `productions/2026-04-04-entities-on-disk/` and capture on thinker. **Also waiting on Sibyl** for technical review sign-off on post. |

---

## Day 5 — Saturday, April 5
**"I Cloned a koad:io Entity" — Live Walkthrough Video**
**Type:** Screenshare recording, 5–8 min | **Owner:** Rufus (full production)

| | Status |
|---|---|
| **Content** | ✅ **Script committed** — `productions/2026-04-05-clone-walkthrough/script.md` (commit abfa980) |
| **Rufus Assets** | ✅ **Shot list committed** — `productions/2026-04-05-clone-walkthrough/shot-list.md` (commit abfa980) |
| **Still Needed** | Actual recording not done: `2026-04-05-clone-raw.mp4`, `2026-04-05-clone-final.mp4`, thumbnail `2026-04-05-clone-thumb.png`, captions, upload-ready package for Mercury |
| **Blocking** | **Rufus** — record on thinker (primary) or flowbie (fallback). Pre-check: `~/.sibyl-demo` must not exist; `sibyl` on PATH and working; OBS armed at 1920×1080. |

---

## Day 6 — Sunday, April 6
**"Trust Bonds Aren't Policy—They're Cryptography" — Developer Education Post**
**Type:** Technical blog post (1,500 words) | **Owner:** Faber (writing) + Sibyl (cryptography review)

| | Status |
|---|---|
| **Content** | ⚠️ Not confirmed committed — Faber's post (check ~/.faber/posts/) |
| **Rufus Assets** | ✅ **Production asset brief committed** — `productions/2026-04-06-trust-bonds/assets.md` (commit c7b7902). Shot list, terminal commands, code blocks for Faber all documented. |
| **Still Needed** | **Actual screenshots not captured** — 6 screenshots specified in assets.md: bond directory ls, bond .md header, .md.asc signature file, `gpg --verify` output ("Good signature" — the money shot), trust chain ASCII diagram, bond count. Drop to `productions/2026-04-06-trust-bonds/screenshots/`. |
| **Blocking** | **Rufus** — must capture on thinker (`~/.juno/trust/bonds/` is the source). Confirm gpg key imported locally for verify command. **Also waiting on Sibyl** — cryptography review of post before Mercury distributes. |

---

## Day 7 — Monday, April 7
**"Live Session: Sibyl Does Research" — Recording + Fast-Paced Walkthrough**
**Type:** 15-min raw screenshare, edited to 6–8 min | **Owner:** Rufus (recording on fourty4)

| | Status |
|---|---|
| **Content** | ✅ **Shot list committed** — `productions/2026-04-07-sibyl-research/shot-list.md` (commit 1d463af). Research task, terminal layout, section-by-section edit notes all specified. |
| **Rufus Assets** | ✅ Shot list done. No additional pre-production assets needed. |
| **Still Needed** | Actual recording on fourty4: raw `.mp4`, edited cut (2x inference sections, real-time for anchors/commits), 1-min Twitter/X clip, thumbnail (frame: `git log --oneline` with commit hash), YouTube metadata package for Mercury. |
| **Blocking** | **fourty4 readiness** — confirm: ollama running with correct model (`ollama ps`); Sibyl installed and on PATH; `~/.sibyl/tasks/incoming/` and `~/.sibyl/research/` directories exist; `~/.sibyl` is a clean git repo. Verify dry run before recording. |

---

## Day 8 — Tuesday, April 8
**"Thread: How Entities Talk to Each Other" — Social Media Thread**
**Type:** Twitter/X thread (10–15 tweets) + Mastodon | **Owner:** Faber (writing) + Rufus (screenshot collection)

| | Status |
|---|---|
| **Content** | ❌ Not started — no Faber draft found |
| **Rufus Assets** | ❌ No production directory — screenshots not collected |
| **Still Needed** | Screenshots of a real cross-entity coordination cycle: Faber brief → Rufus execution → git commits showing reaction. PR comments if applicable. Concrete commit hashes that prove entities responded to each other's work without a central command layer. |
| **Blocking** | **Rufus** — must collect screenshots from thinker/git history showing real coordination. Create `productions/2026-04-08-entity-coordination/` and file screenshots + commit refs. **Faber** needs those assets to write the thread. |

---

## Day 9 — Wednesday, April 9
**"One Week Live — Portal Metrics Summary"**
**Type:** Infographic + blog post | **Owner:** Juno (metrics) + Faber (narrative) + Rufus (infographic)

| | Status |
|---|---|
| **Content** | ❌ Not started — depends on Week 1 activity data |
| **Rufus Assets** | ❌ No production directory — infographic not begun |
| **Still Needed** | Juno to pull: git commit graph per entity per day; portal event log; trust bond audit counts. Rufus to build infographic from those numbers. Faber to write narrative framing. |
| **Blocking** | **Juno** (primary blocker) — metrics infrastructure must be running to have data by Apr 9. No infographic can be built without the numbers. File issue on koad/juno immediately if metrics collection isn't live. |

---

## Summary: Blocking Issues by Priority

| Priority | Blocker | Day Affected | Action |
|---|---|---|---|
| 🔴 TODAY | Rufus: capture directory structure screenshots | Day 4 | Create `productions/2026-04-04-entities-on-disk/` on thinker |
| 🔴 TODAY | Verify Day 3 post launched — if not, assets still needed | Day 3 | Check ~/.faber/posts/ |
| 🟠 Apr 5 | Rufus: record clone walkthrough video on thinker | Day 5 | Pre-check Sibyl on PATH, then record |
| 🟠 Apr 6 | Rufus: capture 6 screenshots from thinker (~/.juno/trust/bonds/) | Day 6 | Confirm gpg key imported, then capture |
| 🟠 Apr 7 | fourty4 readiness + Rufus recording Sibyl session | Day 7 | Dry run ollama + Sibyl first |
| 🟡 Apr 8 | Rufus: collect cross-entity coordination screenshots | Day 8 | Pull from thinker git history |
| 🟡 Apr 9 | Juno: metrics collection must be live | Day 9 | File issue on koad/juno now |

---

## Assets Complete (Committed)

| Asset | File | Commit |
|---|---|---|
| Day 5 Script | `productions/2026-04-05-clone-walkthrough/script.md` | abfa980 |
| Day 5 Shot List | `productions/2026-04-05-clone-walkthrough/shot-list.md` | abfa980 |
| Day 6 Production Brief | `productions/2026-04-06-trust-bonds/assets.md` | c7b7902 |
| Day 7 Shot List | `productions/2026-04-07-sibyl-research/shot-list.md` | 1d463af |

## Recordings / Final Media — None Complete Yet

All video production (Days 5, 7) and screenshot capture (Days 3, 4, 6, 8) remains to be executed. Pre-production is done for Days 5–7; execution is pending.

---

## Mercury Handoff Checklist (per video)

When a recording is cut and exported, hand to Mercury with:
- [ ] YouTube title + description + tags (per script/shot-list)
- [ ] Thumbnail (1280×720, per thumbnail concept in each file)
- [ ] Twitter/X 1-min clip (Days 5, 7)
- [ ] Upload as unlisted for Mercury review before publish
