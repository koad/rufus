---
title: "19 Entities, 9 of Them Non-Compliant"
video-type: standalone
pillar: Reality
date: 2026-05-20
duration: 7–9 minutes
subject: Argus compliance scan — 15 entities, 9 failures, Alice worst at 5/8 (no keys, no bonds, no hook), Salus remediates 5 in one day, two gaps escalate to koad
production-owner: Rufus
status: production-ready
---

# Script: "19 Entities, 9 of Them Non-Compliant"

## Directorial Note

This is a diagnostic video. The register is clinical throughout — Argus is a health-check entity, not a morality engine, and the video should feel the same way. Findings are findings. Numbers are numbers. Remediation is remediation. Escalation is escalation.

The irony beat in this video is Alice. Alice's score — 5/8, the worst on the team — belongs to the entity whose stated function is to onboard others to sovereign infrastructure. This is the video's one ironic moment. It should land once: show the score, hold on the row, let the viewer read the finding. Then continue. Do not return to it. Do not editorialize it. The viewer does not need it pointed at them a second time.

The Salus section is efficiency, not drama. Five items closed in one day by one entity, no koad involvement, clean commits. The tone should match: methodical, unhurried, already done. The remediation log on screen is the evidence. Name the five items. Name the judgment call Salus made about the hook gaps. Then move on.

The two open gaps at the close are not a failure. They are the system identifying its own limits and naming them correctly. Alice's empty `id/` directory and Astro's absent presence on thinker both require a human. They are escalated to the right party. The closing beat is not "the system failed" — it is "the system ran the audit, fixed what it could, documented what it couldn't, and handed the remainder up." That is governance working.

The Argus self-audit section is the philosophically interesting beat of the video. Argus passed its own compliance check. This is a real finding with a real answer: the architecture explains why self-audit is meaningful even if imperfect, and why transparency is the honest claim. Deliver it without hedging, without over-assurance, and without pretending the question is trivial. The video can hold that tension.

---

## Pre-Roll Checklist (before recording)

- [ ] Terminal: black background (#000000), white text, fullscreen
- [ ] Font: JetBrains Mono or Fira Code, 16–18px
- [ ] Shell prompt: minimal — `$ ` or `host $ ` only, no decorations
- [ ] Clear scrollback: `clear && printf '\033[3J'`
- [ ] Verify `cat /home/koad/.argus/reports/2026-04-05-team-health-check.md` displays cleanly — the summary table with all 15 entities and scores is visible
- [ ] Verify `ls /home/koad/.alice/id/` returns empty output or only `.gitignore` — no key files
- [ ] Verify `git -C /home/koad/.salus log --oneline -8` shows the five remediation commits with correct hashes
- [ ] Verify `gh issue view 59 --repo koad/juno` returns the open issue, assigned to koad, zero comments
- [ ] Audio check: quiet room, mic gain set
- [ ] OBS: single-monitor capture, no chat overlay

---

## SEGMENT 1 — The Audit Runs (0:00–1:15) — OPENING TERMINAL SCENE

**No preamble. No title card. Open on blank terminal. Type slowly.**

```bash
cat /home/koad/.argus/reports/2026-04-05-team-health-check.md
```

**[Execute. The full report renders — the header, the criteria list, the per-entity tables, the summary table. Let it scroll. When the output settles on the summary table — the one with all 15 entities and their scores — hold for 15 full seconds. Do not narrate during the hold. The viewer reads the table: nine entities with scores below 8/8. Let them register the distribution before a word is spoken.]**

**After the hold, narration — flat, factual:**

> "Day 6. Argus ran a full health check against all 15 team entities."

*(pause — 4 seconds)*

> "Eight criteria. File presence checks. PRIMER.md. The hook script — present, and executable. CLAUDE.md. README.md. A memories directory with content. A .env. A keys directory with actual key files. A trust bonds directory with actual bond files."

*(pause — 4 seconds)*

> "Not an evaluation of what those files say. Whether they exist."

*(pause — 5 seconds)*

> "Nine entities failed at least one check."

*(pause — 6 seconds of silence)*

---

## SEGMENT 2 — The Table (1:15–2:30) — TERMINAL CLOSE ON SUMMARY TABLE

**Clear screen. Type slowly.**

```bash
cat /home/koad/.argus/reports/2026-04-05-team-health-check.md
```

**[Execute. Let the report scroll again to the summary table. Once the table is visible and settled, hold for 12 seconds. This is the second view of the table — now the viewer is reading it as a document, not encountering it for the first time. The scores should be legible: five entities at 8/8, nine at 7/8, one at 5/8. The 5/8 row is Alice. Do not direct attention to it during the hold. Let the viewer find it.]**

**Narration — measured:**

> "Five entities at 8/8: Juno, Vesta, Livy, Argus, Salus, Aegis."

*(pause — 3 seconds)*

> "Nine below that. Seven entities at 7/8. The most common gap: no executable hook file. Six of those seven were missing the hooks directory entirely — the directory did not exist. Sibyl's case was different. The directory existed. It contained documentation for a hook that had never been written."

*(pause — 4 seconds)*

> "The spec was present. The implementation was not."

*(pause — 5 seconds)*

> "And then there is Alice."

*(pause — 4 seconds)*

> "5 out of 8."

*(pause — 8 seconds of silence — hold on the table; do not narrate; let Alice's row stand)*

---

## SEGMENT 3 — Alice (2:30–3:45) — TERMINAL SCENE

**Clear screen. Type slowly.**

```bash
ls /home/koad/.alice/id/
```

**[Execute. The output is empty — or only a .gitignore. Nothing else. Hold for 10 seconds. Do not narrate during the hold. The viewer reads the empty listing. Then narrate.]**

**Narration — flat, no irony in the voice:**

> "Alice's `id/` directory. No Ed25519. No ECDSA. No RSA. No DSA. The directory was gestated. The keys were never generated."

*(pause — 5 seconds)*

> "Alice also had no hooks directory and no trust directory. Three hard failures."

*(pause — 4 seconds)*

> "Alice is the onboarding entity. Her documented function is to introduce new users to koad:io sovereign infrastructure. She is the entity designed to demonstrate sovereign identity to the people who are deciding whether to build on it."

*(pause — 5 seconds)*

> "At the time of the Day 6 audit, Alice had no cryptographic fingerprint. She could not sign her own commits. She could not issue or receive trust bonds in a way anyone could verify. There was no chain that could run through her."

*(pause — 6 seconds of silence)*

---

## SEGMENT 4 — What the Criteria Are (3:45–4:45) — BLANK TERMINAL

**Blank terminal. No commands. This segment is the framing. Deliver it cleanly — the criteria are not arbitrary.**

> "Eight checks. The question worth asking: why these eight?"

*(pause — 4 seconds)*

> "PRIMER.md and CLAUDE.md: context-carrying. An entity without these has no orientation document for arriving agents. It cannot be briefed from its own directory."

*(pause — 3 seconds)*

> "The hook: the entry point for autonomous invocation. An entity without an executable hook cannot be called by the framework. It can only be reached by a human who knows to run it manually."

*(pause — 3 seconds)*

> "The memories directory: persistent state. An entity with no memories files starts each session without carry-forward context."

*(pause — 3 seconds)*

> ".env: the entity's identity and configuration layer. Required for git authorship, for the harness to recognize entity scope."

*(pause — 3 seconds)*

> "Keys and trust bonds: cryptographic attribution and authorization. An entity without keys cannot be the documented author of its own work. An entity without trust bonds has no machine-readable record of who authorized it to do what."

*(pause — 4 seconds)*

> "These are not governance ideals. They are the minimum scaffold for an entity that can operate, be attributed, and be verified."

*(pause — 5 seconds of silence)*

---

## SEGMENT 5 — Salus Remediates (4:45–6:15) — TERMINAL SCENE

**Clear screen. Type slowly.**

```bash
git -C /home/koad/.salus log --oneline -8
```

**[Execute. The log renders — the five remediation commits visible in the output, all dated 2026-04-05. Hold for 10 seconds. The viewer reads the commit messages: Chiron's trust bond, Faber's memory gap, Rufus's memory gap, Lyra's README, Copia's README. Five items. Same day as the audit. Then narrate.]**

**Narration — efficient, no acceleration:**

> "The Argus report ends with one line: 'Salus: this report is your work queue.'"

*(pause — 4 seconds)*

> "Within the same day, Salus closed five items."

*(pause — 4 seconds)*

> "Chiron's trust bond: the juno-to-chiron bond files already existed in Juno's directory. Salus dual-filed them to Chiron's repository. Commit 99638f1. There is a minor attribution note — the bond filing is documented with the expected git author being Juno rather than Salus; Chiron's KNOWN-IRREGULARITIES.md records it. The irregularity is noted, not hidden."

*(pause — 3 seconds)*

> "Faber's memory gap: one file for an entity 26 posts into a series. Salus created a second memory file documenting the full Reality Pillar state. Commit 53084fa."

*(pause — 3 seconds)*

> "Rufus's memory gap: sparse. Salus created a production portfolio memory file — master schedule, five videos ready to record. Commit b4aac01."

*(pause — 3 seconds)*

> "Lyra and Copia: both gestated with keys and bonds, both missing README.md. Added. Commits 0937f25 and ee4263a. Both moved from WARN to COMPLIANT."

*(pause — 5 seconds)*

> "Five items. One day. No koad involvement required."

*(pause — 6 seconds of silence)*

---

## SEGMENT 6 — Salus's Judgment Call (6:15–7:00) — BLANK TERMINAL

**Blank terminal. No commands. This segment names the distinction between the audit layer and the remediation layer.**

> "Salus did not create stub hooks for Vulcan, Faber, Muse, Veritas, Mercury, or Sibyl."

*(pause — 4 seconds)*

> "Per the koad:io framework, the hook file in an entity directory is an override, not a requirement. Entities without custom routing needs use the framework default in ~/.koad-io/. Argus flags absence — file present is a pass, file absent is a fail. Salus judged that absence is valid design, not a gap."

*(pause — 4 seconds)*

> "Argus and Salus read the same fact and reached different conclusions about whether action was required. That is not a system failure. It is two layers of the governance architecture operating correctly: Argus gives the complete picture, Salus applies design knowledge to determine what actually needs to change. Neither layer has the full picture alone."

*(pause — 6 seconds of silence)*

---

## SEGMENT 7 — The Argus Self-Audit (7:00–7:45) — BLANK TERMINAL

**Blank terminal. No commands. This segment holds the tension honestly.**

> "Argus is one of the 15 entities in the scan. Argus audited itself."

*(pause — 4 seconds)*

> "Score: 8 out of 8."

*(pause — 5 seconds)*

> "The harder question the report does not resolve: the criteria Argus checked are the criteria Argus was designed with. The self-audit demonstrates compliance against those criteria. It does not demonstrate that the criteria are the right ones."

*(pause — 4 seconds)*

> "The team is the only auditor available. An external independent audit of 19 sovereign AI entities does not exist as a service."

*(pause — 4 seconds)*

> "What the system has is transparency: committed reports, public repositories, git history, signed bonds, an audit trail any reader can traverse. The self-audit is a stronger signal than no audit. It is a weaker signal than external verification. The operation is honest about which one it has."

*(pause — 6 seconds of silence)*

---

## SEGMENT 8 — Two Open Gaps (7:45–9:00) — TERMINAL SCENE + CLOSE

**Clear screen. Type slowly.**

```bash
gh issue view 59 --repo koad/juno
```

**[Execute. The full issue renders — title: "Alice needs cryptographic identity — id/ dir empty, no keys generated." State: OPEN. Assigned to koad. Zero comments. Hold for 12 seconds. The viewer reads the issue: the finding, the why-it-matters, the fix, the single word "Blocked on: koad." Then narrate.]**

**Narration — flat:**

> "koad/juno#59. Open. Zero comments. Assigned to koad. The playbook is written — Salus produced the exact key generation steps in a committed protocol document. The keys do not exist."

*(pause — 5 seconds)*

> "The second open gap: Astro's on-disk presence. On thinker, `ls /home/koad/.astro` returns nothing. Astro is described in Juno's memory as ring zero — a genuine peer relationship already established — but has no entity directory at the primary machine. The Day 33 re-audit noted Astro may reside on another machine. This was not documented at audit time."

*(pause — 5 seconds of silence)*

> "Both items are escalated correctly. The system ran the audit, remediated everything within its reach, documented what it could not reach, and handed the remainder to the person who can close it."

*(pause — 4 seconds)*

> "That is not a system in trouble. That is governance finding its own limits and naming them."

*(pause — 6 seconds of silence)*

**Type slowly:**

```bash
gh issue view 59 --repo koad/juno
```

**[Do not execute again — this is the hold frame. If cutting in post, freeze on the open issue state. If recording live, leave it on screen. The open issue — assigned, uncommented, waiting — is the closing image. 8 seconds. Then black.]**

---

## Timing Map

| Segment | Clock | Content |
|---------|-------|---------|
| 1 | 0:00–1:15 | The audit runs — full report on screen, 15-second hold on summary table, criteria named |
| 2 | 1:15–2:30 | The table — second view, score distribution named, Alice's row held |
| 3 | 2:30–3:45 | Alice — ls /home/koad/.alice/id/ empty, three failures named, governance tension stated |
| 4 | 3:45–4:45 | What the criteria are — blank terminal, eight checks explained by function |
| 5 | 4:45–6:15 | Salus remediates — git log, five items, same day, commits named |
| 6 | 6:15–7:00 | Salus's judgment call — blank terminal, hook distinction, two layers named |
| 7 | 7:00–7:45 | The Argus self-audit — blank terminal, 8/8, the harder question held honestly |
| 8 | 7:45–9:00 | Two open gaps — gh issue view 59, Alice and Astro, governance finding its limits |

---

## Delivery Notes

- **Tone throughout:** Diagnostic. Clinical without coldness. The findings are findings — they are not accusations, and they are not minimized. Deliver the numbers in the same register you would read a health report: accurate, complete, non-dramatic.
- **The opening hold (15 seconds, Segment 1):** Complete silence. The summary table is on screen. Nine entities below 8/8. One at 5/8. Do not direct the viewer to Alice during the hold. Let them find the row themselves. The first narration line — "Day 6. Argus ran a full health check" — comes after the hold.
- **"And then there is Alice." (Segment 2):** Short. Even. Then a four-second pause. Then "5 out of 8." Then 8 seconds of silence with the table still on screen. This is the video's single ironic beat. The sentence and the silence carry it. Do not add weight with your voice. Do not return to it after this moment.
- **ls /home/koad/.alice/id/ (Segment 3):** The empty output is the visual argument. Hold 10 seconds of silence after it renders. The narration begins after the hold. Do not narrate during the hold — the viewer is already registering what they see.
- **"Five items. One day. No koad involvement required." (Segment 5):** Delivered as a summary, not a celebration. Efficient. The Salus section should feel like reading a closed task list, not a success story.
- **"Neither layer has the full picture alone." (Segment 6):** This is the conceptual heart of the Salus section. Do not rush past it. Deliver it and then let 6 seconds of silence hold the distinction before moving to the self-audit.
- **"What the system has is transparency." (Segment 7):** The honest claim. Deliver it plainly — neither apologetically nor with oversell. The self-audit result is a weaker signal than external verification; say so directly. The video does not need to defend the system from honest description.
- **gh issue view 59 close (Segment 8):** The closing image is an open issue. Assigned. Zero comments. Waiting. The 8-second hold after the final narration line — "That is governance finding its own limits and naming them." — is the punctuation. Hold it. Then black.
- **No backspace corrections on camera.** Retake immediately on any typo in a path or command.
- **No live entity invocations.** All terminal work is file reads, directory listings, git log, and gh CLI. Nothing that kicks off a Claude session.

---

## Tonal Reference

The video is not about the nine failures. It is about what the system did with them. The audit ran. The findings were specific. Five items were closed the same day. Two items were correctly escalated to the one party who can close them. That sequence — detect, remediate, escalate — is governance operating as designed.

Alice is the exception that makes the governance architecture legible. An entity in a central onboarding role, non-compliant in the most structurally significant ways, is not a system failure. It is the audit doing its job. The video names the finding once, shows the empty directory, and moves on. That is the correct register.

The close — a GitHub issue sitting open, assigned to koad, zero comments — is not a defeat image. It is evidence that the escalation path worked. The system found the limit, documented it, and addressed it to the right party. The governance architecture does not pretend to be self-sufficient. It is honest about where human action is required. Show that honestly and cut to black.

---

## Accuracy Notes

- Argus report source: `/home/koad/.argus/reports/2026-04-05-team-health-check.md` — Day 6 scan, 15 entities, 8 criteria, committed 2026-04-05
- Nine entities below 8/8: Vulcan (7/8), Faber (7/8), Chiron (7/8), Muse (7/8), Rufus (7/8), Sibyl (7/8), Veritas (7/8), Mercury (7/8), Alice (5/8)
- Alice's three failures: no hooks/ directory (hook absent and not executable counts as two check failures), id/ empty (zero keys), trust/ directory absent entirely — confirmed by `ls /home/koad/.alice/id/`
- Salus five remediations, same day: Chiron trust bond (99638f1), Faber memory (53084fa), Rufus memory (b4aac01), Lyra README (0937f25), Copia README (ee4263a) — source: `git -C /home/koad/.salus log --oneline -8`
- Salus judgment on hook gaps: documented in `~/.salus/protocols/` and `~/.argus/reports/2026-04-05-health-check-remediation.md`; hook absence valid by design, not remediated
- Open gap 1: koad/juno#59 — Alice empty id/, OPEN, assigned to koad, zero comments; playbook at `~/.salus/protocols/alice-key-generation.md` (commit 4847bff)
- Open gap 2: Astro — no /home/koad/.astro on thinker; noted in Day 33 re-audit report; possible residence on fourty4 or wonderland, undocumented
- Day 33 re-audit result: 19 entities (4 new gestated: Lyra, Copia, Janus, Iris), 17 of 19 compliant; Alice moved from critical to warning after trust bond gap closed
- Argus self-audit score: 8/8 — source: summary table in `~/.argus/reports/2026-04-05-team-health-check.md`
- GPG revocation gap: 14 of 15 entities missing gpg-revocation.asc; only Juno has one; mentioned in the post but not in a dedicated segment — may reference in passing during Segment 1 if timing allows
