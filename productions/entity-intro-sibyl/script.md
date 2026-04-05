---
title: "Meet Sibyl — koad:io Research Director"
series: entity-intro
entity: sibyl
video-type: screencast
date: 2026-04-05
duration: under 3 minutes
production-owner: rufus
status: production-ready
---

# Script: Meet Sibyl

## Pre-Roll Checklist

- [ ] Terminal: black background, 16–18px monospace, full-screen
- [ ] Shell prompt stripped to `$ ` — no git decorations, no powerline
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] `cd ~/.sibyl && git pull` done in a separate terminal
- [ ] `sibyl` command confirmed working: `PROMPT="test" sibyl`
- [ ] `ssh fourty4 echo ok` confirmed (or fallback path decided)
- [ ] Audio check: quiet room, mic gain set

---

## OPENING CARD (0:00–0:05)

**[SCREEN]** Static frame — black background, white monospace text centered:

```
sibyl
research director
koad:io ecosystem
```

**[SILENCE]** No voice during card.

---

## SEGMENT 1 — Who (0:05–0:40)

**[SCREEN]** Navigate to sibyl, show README head.

**[TYPE]**
```bash
cd ~/.sibyl && head -5 README.md
```

**[VOICEOVER]**

> "This is Sibyl. Sibyl is the research director for the koad:io ecosystem.
> She doesn't write content, she doesn't build products — she feeds the front
> of every decision. Every research brief ends with an actionable conclusion,
> not just a summary."

> "Sibyl sits at the top of the pipeline: Juno identifies a question, Sibyl
> researches it, Veritas fact-checks the output, and then the rest of the team
> acts. She's the reason the ecosystem moves on intelligence instead of
> guesswork."

**[TIMING]** ~35 seconds.

---

## SEGMENT 2 — What (0:40–1:30)

**[SCREEN]** Show research output directory and briefing template.

**[TYPE]**
```bash
ls ~/.sibyl/research/ | tail -5
```

**[VOICEOVER]**

> "Research assignments arrive as GitHub Issues on koad/sibyl. Sibyl completes
> them and commits the brief to her research directory — one file per
> assignment, named by date and topic."

**[TYPE]**
```bash
head -10 ~/.sibyl/BRIEFING_TEMPLATE.md
```

**[VOICEOVER]**

> "Every brief follows the same template: question, context, findings, and a
> conclusion section that must contain a decision recommendation. Not 'here is
> information.' Here is what to do."

> "She runs on deepseek-r1 at 8 billion parameters via ollama — local
> inference on fourty4. Zero cost per query. 128k context window."

**[TIMING]** ~50 seconds.

---

## SEGMENT 3 — Clone (1:30–2:00)

**[SCREEN]** Live clone and ls.

**[TYPE — deliberately, audibly]**
```bash
git clone https://github.com/koad/sibyl ~/.demo-sibyl
```

**[Wait for clone to complete. Let output scroll.]**

**[VOICEOVER]**

> "Clone Sibyl and you have a research director on your disk. Her briefing
> templates, her research output, her editorial calendar — all in git, all
> yours."

**[TYPE]**
```bash
ls ~/.demo-sibyl
```

**[VOICEOVER]**

> "Files on disk. No API. No subscription. No kill switch."

**[TIMING]** ~30 seconds.

---

## SEGMENT 4 — Demo (2:00–2:50)

**[SCREEN]** Invoke Sibyl with a small research question, show output, show git commit.

**[TYPE]**
```bash
PROMPT="What are the top 3 reasons developers clone open source tools instead of subscribing to SaaS equivalents? Two sentences max per reason." sibyl
```

**[Wait for inference. Do not cut the wait. If it takes more than 10 seconds, that is fine — voice over during wait:]**

**[VOICEOVER — during inference wait if >5s]**

> "She's running on local inference right now. Watch what comes back."

**[Wait for output to complete. Let viewer read it.]**

**[VOICEOVER — after output appears]**

> "Three findings. Two sentences each. That's the discipline — Sibyl doesn't
> pad, she concludes."

**[TYPE]**
```bash
git -C ~/.sibyl log --oneline -3
```

**[VOICEOVER]**

> "Committed. Every brief is a permanent record. That's Sibyl."

**[TIMING]** ~50 seconds. May run slightly over if inference is slow — acceptable up to 3:15.

---

## FALLBACK SCRIPT — Segment 4 (if fourty4 offline)

*Use this version of Segment 4 if sibyl cannot be invoked live.*

**[TYPE]**
```bash
ls ~/.sibyl/research/ | tail -5
```

**[VOICEOVER]**

> "Here are Sibyl's five most recent research deliverables. Each one is a
> committed brief."

**[TYPE]**
```bash
cat ~/.sibyl/research/$(ls ~/.sibyl/research/ | tail -1) | head -25
```

**[VOICEOVER]**

> "Date, topic, context, findings, conclusion. Every brief has a decision
> recommendation — not just information. And it's committed to git automatically."

**[TYPE]**
```bash
git -C ~/.sibyl log --oneline -3
```

**[VOICEOVER]**

> "Permanent record. Files on disk. That's Sibyl."

---

## CLOSING CARD (2:50–3:00)

**[SCREEN]** Static frame — black background, white monospace text:

```
git clone https://github.com/koad/sibyl
koad.sh
```

**[SILENCE]**

---

## Editing Notes

- Inference wait is not dead air — mention it in VO if it exceeds 5 seconds
- If output runs long (>8 lines), cut at the third finding — three is the stated structure
- Opening and closing cards: live typed preferred; static PNG overlay acceptable
- No music. No transitions. Straight cuts only.
- Captions required on final export.
- If using fallback path: add a brief slate card at start of Segment 4 reading `(from existing research output)` — 2 seconds, typed live — to be transparent with viewers.
