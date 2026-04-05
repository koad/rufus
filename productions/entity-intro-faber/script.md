---
title: "Meet Faber — koad:io Content Strategist"
series: entity-intro
entity: faber
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Faber

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.faber && git pull` done in a separate terminal
- [ ] Confirm target post exists: `ls ~/.faber/content/2026-04-05-trust-bonds-arent-policy.md`
- [ ] If not present: identify fallback post with `ls ~/.faber/content/ | tail -1`
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
faber
content strategist
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to faber, show README head.

**[TYPE]**
```bash
cd ~/.faber && head -5 README.md
```

**[VOICEOVER]**

> "This is Faber. Faber is the content strategist for the koad:io ecosystem.
> He writes the Reality Pillar — the public-facing post series that documents
> what it looks like to build sovereign AI infrastructure in real time. Not
> marketing copy. Field notes."

> "In the pipeline, Faber receives research briefs from Sibyl, brand context
> from Juno, and audience intelligence from Veritas. He synthesizes all of that
> into content that can ship to the blog, to Reddit, to Show HN. He hands the
> finished posts to Mercury for distribution."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show content directory overview and editorial structure.

**[TYPE]**
```bash
ls ~/.faber/
```

**[VOICEOVER]**

> "Faber's directory has a content folder, a content calendar, an editorial
> policy, an audience segments document. This isn't a prompt file — it's a
> strategist's working environment."

**[TYPE]**
```bash
head -5 ~/.faber/EDITORIAL.md
```

**[VOICEOVER]**

> "His editorial document defines the voice, the rules for what gets published,
> and what the Reality Pillar is actually trying to accomplish. Every post
> traces back to this document."

> "The posts themselves are markdown files, dated, with YAML frontmatter
> that carries the pillar, status, and priority. No post ships without
> a committed file."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/faber ~/.demo-faber
```

**[Wait for clone to complete.]**

**[VOICEOVER]**

> "Clone Faber and you have a content strategist on disk. His editorial
> policy, audience profiles, content calendar, and every post he's
> written — all in git, all yours."

**[TYPE]**
```bash
ls ~/.demo-faber
```

**[VOICEOVER]**

> "Files. No content management system. No subscription."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Show posts directory then read a post header.

**[TYPE]**
```bash
ls ~/.faber/content/
```

**[Wait for output — let viewer see the list of dated posts.]**

**[VOICEOVER]**

> "Every post Faber has written. Date-named. All committed. You can see the
> series building in real time — this is the public record of the koad:io
> build."

**[TYPE]**

*Use the trust-bonds post if present; otherwise substitute most recent file:*
```bash
cat ~/.faber/content/2026-04-05-trust-bonds-arent-policy.md | head -20
```

**[Wait for output — let viewer read the frontmatter and opening.]**

**[VOICEOVER]**

> "Title: Trust Bonds Aren't Policy. Status: draft. Pillar: Reality. And
> then the first lines of the argument — this is the working document before
> Mercury publishes it."

> "That's Faber. Content as infrastructure. Every post a commit."

**[TIMING]** ~50 seconds.

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/faber
koad.sh
```

**[SILENCE]**

---

## Editing Notes

- No music. No transitions. Straight cuts.
- If `ls ~/.faber/content/` returns more than 12 files, the list may wrap — that's fine, let it wrap; it demonstrates volume
- If the target post frontmatter includes a `description:` field, read that line aloud — it's the clearest signal of strategic intent
- If EDITORIAL.md head-5 is sparse at record time, substitute `head -10`
- Opening and closing cards: live typed preferred; static PNG overlay acceptable
- Captions required on final export.
