---
production: "Thread: How Entities Talk to Each Other"
date: 2026-04-08
content-calendar-ref: REALITY-2026-04-03.md (Tuesday Apr 8 slot)
content-type: Twitter/X thread (10–15 tweets) + Mastodon thread
production-role: Rufus (screenshot/proof collection)
distribution-owner: Mercury
writing-owner: Faber
key-issues: koad/juno#25, koad/vulcan#35
---

# Shot List & Capture Guide
## "Thread: How Entities Talk to Each Other"

Day 8 of the Reality Pillar. The thread proves entities coordinate through files and git — not Slack, not meetings. The concrete chain to show: Juno files a build assignment → Vulcan executes → Veritas fact-checks → Mercury distributes. Every handoff is a public GitHub comment. Everything is auditable.

---

## Evidence Chain to Document

```
Faber (research brief) → Juno (issue filed: koad/juno#25) →
  Vulcan (build plan: koad/vulcan#35) →
    Vulcan delivers (comment on koad/vulcan#35, cross-posted koad/juno#25) →
      Veritas (fact-check flagged in koad/juno#25) →
        koad confirms fix →
          Mercury (cleared to distribute)
```

Each step leaves a file on disk or a public comment. No step requires a private channel. That's the argument.

---

## Pre-Capture Checklist

```bash
# Machine: thinker (primary ops) for browser captures
# Machine: fourty4 for terminal / git log captures

# Browser (Chrome or Firefox — use Firefox for cleaner dark mode)
# - Log into GitHub as koad
# - Set zoom to 100% — no scaling artifacts
# - Hide browser bookmarks bar (Cmd+Shift+B)
# - Use dark mode (GitHub dark theme or system dark)
# - Window width: 1280px minimum. No browser chrome beyond tab + address bar.

# Terminal (fourty4 or thinker)
# - font: monospace, 16pt minimum for legibility at Twitter card size
# - theme: dark bg, light text (no powerline noise)
# - clean prompt: export PS1="[koad@thinker] $ "
# - clear scrollback before each capture: clear && printf '\033[3J'
```

---

## Shot List

Shots are ordered for Faber's thread sequencing. Capture in order — some shots build on prior state.

---

### SHOT 1 — The Juno Assignment (koad/juno#25 issue body)
**What it proves:** Entities receive work through issues — there's a paper trail from the moment a task is filed.

**Capture:**
1. Open `https://github.com/koad/juno/issues/25` in browser
2. Scroll to the **issue body only** (Muse's Alice UI design brief deliverable notice)
3. Frame: issue title + first three paragraphs + "Next: Vulcan Integration / Handoff: @vulcan" line visible
4. No comments visible yet — just the original assignment

**Framing notes:**
- Full browser width (1280px+), no sidebar open
- Ensure "Handoff: @vulcan" is clearly readable — that's the coordination proof
- Capture the issue number ("#25") and repo ("koad/juno") in the tab/URL bar

**Tweet context:** "Tweet 2 — How a brief becomes a build assignment. Juno tracks it in koad/juno#25. The handoff line: 'Handoff: @vulcan'. That's the entire routing layer."

---

### SHOT 2 — Juno Answers Vulcan's Blockers (koad/juno#25 comment)
**What it proves:** Decisions happen in public. Juno's answers to Vulcan's three questions are a permanent record — not in a DM, not in Slack.

**Capture:**
1. Scroll down to the **"Juno here. Answering Vulcan's three blockers"** comment
2. Frame the full comment — all three numbered answers visible
3. Comment author and timestamp must be readable

**Framing notes:**
- Show author badge ("koad/juno" or equivalent) + comment timestamp
- All three answers (tech stack, cert signing, conversational AI) must fit in one screenshot — scroll to get clean single-frame capture, or capture as tall screenshot (2× height acceptable for long-form)

**Tweet context:** "Tweet 4 — Vulcan asked three questions. Juno answered in the thread. Permanent record. No DM needed."

---

### SHOT 3 — The Vulcan Build Plan (koad/vulcan#35 issue body)
**What it proves:** Vulcan received the assignment and filed a structured plan before building. The brief → plan handoff is visible.

**Capture:**
1. Open `https://github.com/koad/vulcan/issues/35` in browser
2. Frame: issue title + the **Current State Assessment table** + the top of the **Decision Required** section
3. The table's "State" column (showing "Complete", "Exists", "No frontend code exists") is the key visual

**Framing notes:**
- Full browser width
- Table must be readable — zoom to 110% if needed, then screenshot at native resolution
- "Tracking: koad/juno#25" cross-reference link should be visible — proves the chain

**Tweet context:** "Tweet 3 — Vulcan opens its own issue (koad/vulcan#35) with a state assessment before touching a line of code. 'The PWA does not exist yet.' Real work starts here."

---

### SHOT 4 — Vulcan Delivery Report (koad/vulcan#35 comment)
**What it proves:** Work is reported back in the same thread it was assigned. The delivery comment closes the loop: files shipped, decisions implemented, deploy instructions included.

**Capture:**
1. Scroll to the **final Vulcan delivery comment** in koad/vulcan#35 (the "🤖 Vulcan — 2026-04-04" comment)
2. Frame: the **"Files shipped"** table + the three "Blockers answered" checkboxes at the bottom
3. Emoji + date attribution ("🤖 Vulcan — 2026-04-04") must be visible

**Framing notes:**
- If table is cut off, capture as two vertically-stacked screenshots (label them 4a, 4b)
- The checkboxes (✅) are the tweet-ready visual — prioritize their visibility

**Tweet context:** "Tweet 5 — Vulcan reports delivery in the same thread. Six files. Three decisions implemented. Deploy instructions included. The thread is the handoff document."

---

### SHOT 5 — Veritas Flags the Post (koad/juno#25 Veritas comment, top half)
**What it proves:** Entities check each other. Veritas fact-checked the Day 4 blog post and issued a HOLD before Mercury could distribute. This is governance without a central authority.

**Capture:**
1. Scroll to the **Veritas verification report comment** in koad/juno#25
2. Frame: the comment header ("## Veritas Verification Report — Day 4 Reality Pillar Post") + the **verdict line** ("Verdict: HOLD — needs edits before distribution") + the Summary table at the bottom of the comment
3. Both the HOLD verdict AND the summary table (Confirmed / Flagged / Speculative rows) in one screenshot

**Framing notes:**
- The "HOLD" verdict is the hook — make it visible at top of frame
- Summary table provides the structure — capture it complete (5 rows)
- If comment is long, capture two frames: (5a) header + verdict, (5b) summary table

**Tweet context:** "Tweet 7 — Before Mercury published, Veritas ran a fact-check. Found one real problem. Issued a HOLD. That's governance on disk — no admin account needed."

---

### SHOT 6 — Veritas Calls Out the Hook Code (koad/juno#25 Veritas comment, hook diff table)
**What it proves:** The fact-check is specific and technical — not just "looks good / looks bad". The comparison table (Post claims vs. Actual file) is the proof that Veritas read the actual code.

**Capture:**
1. Within the same Veritas comment, scroll to the **comparison table** ("Post claims / Actual file" markdown table)
2. Frame: table header + all rows + the bolded "Required fix:" paragraph below it

**Framing notes:**
- Table must be fully readable — 7 rows × 2 columns
- The "Required fix:" paragraph anchors the technical credibility — include it
- This is a technical tweet; legibility beats aesthetics here

**Tweet context:** "Tweet 8 — The HOLD wasn't vague. Veritas built a diff table: what the post claimed vs. what the actual hook file contains. Seven line-by-line discrepancies. Fixed before publish."

---

### SHOT 7 — koad Confirms Fix, Mercury Unblocked (koad/juno#25 final comment)
**What it proves:** The fix was implemented and confirmed in the same thread. The chain closes: Juno assigns → Vulcan builds → Veritas holds → koad fixes → Mercury can distribute.

**Capture:**
1. Scroll to the **final koad comment** in koad/juno#25 ("Fixed. Commit c236261 on koad/faber...")
2. Frame the full comment — it's short (3–4 lines), capture completely
3. Ensure the commit hash (c236261) and repo (koad/faber) are readable

**Framing notes:**
- Pair with Shot 5 in the thread — "HOLD → Fixed" is the story arc
- Commit hash is the proof point — prioritize legibility

**Tweet context:** "Tweet 9 — Fix confirmed in the same thread. Commit hash on disk. Mercury now has a green light. The entire review cycle — hold → fix → confirm — took place in one public thread."

---

### SHOT 8 — Commit Logs Side by Side (terminal, 3-pane)
**What it proves:** Multiple entities worked in parallel. The git histories are independent but temporally overlapping — proof of autonomous coordination, not scripted sequencing.

**Capture setup (terminal on thinker):**
```bash
# Three-pane tmux layout (horizontal split × 2)
# Pane 1 (left): faber commit log
# Pane 2 (middle): vulcan commit log  
# Pane 3 (right): juno commit log

# Left pane
cd ~/.faber && git log --oneline --since="2026-04-03" --no-walk=unsorted \
  --format="%C(yellow)%h%Creset %C(cyan)%ad%Creset %s" --date=format:'%b %d %H:%M'

# Middle pane
cd ~/.vulcan && git log --oneline --since="2026-04-03" \
  --format="%C(yellow)%h%Creset %C(cyan)%ad%Creset %s" --date=format:'%b %d %H:%M'

# Right pane
cd ~/.juno && git log --oneline --since="2026-04-03" \
  --format="%C(yellow)%h%Creset %C(cyan)%ad%Creset %s" --date=format:'%b %d %H:%M'
```

**Framing notes:**
- All three panes visible simultaneously — do not collapse any pane
- Pane labels (manually set with tmux `select-pane -T` or a title card overlay in post): "faber", "vulcan", "juno"
- At least 5–8 commits per pane visible
- Date/time column is essential — shows concurrent activity
- If SSH'd into fourty4 from thinker, confirm entity dirs are accessible at ~/.vulcan etc.

**Tweet context:** "Tweet 6 — Three entity git logs, same 48-hour window. Faber writing. Vulcan building. Juno coordinating. Independent repos, overlapping timestamps. No shared scheduler. Just files."

---

### SHOT 9 — Entity Cross-Reference in Commit Messages (terminal)
**What it proves:** Entities name each other in commit messages — the references are the coordination layer. "faber" appears in juno commits; "juno#25" appears in vulcan commits.

**Capture:**
```bash
# On fourty4 or thinker, search commit messages for cross-entity references
cd ~/.vulcan && git log --oneline --all --grep="juno" \
  --format="%C(yellow)%h%Creset %C(green)vulcan%Creset %C(cyan)%ad%Creset %s" \
  --date=format:'%b %d'

echo "---"

cd ~/.faber && git log --oneline --all --grep="rufus\|vulcan\|juno" \
  --format="%C(yellow)%h%Creset %C(green)faber%Creset %C(cyan)%ad%Creset %s" \
  --date=format:'%b %d'
```

**Framing notes:**
- Run both commands sequentially in a single terminal pane (show the `---` separator)
- The cross-entity grep hits are the visual — each matching commit is a coordination event
- If no grep hits: fall back to showing `git log --oneline -10` for each entity with the relevant "Handoff: @vulcan" or "task juno-*" commits manually noted with a comment overlay

**Tweet context:** "Tweet 10 — Entities reference each other in commit messages. Search for 'juno' in vulcan's history. There it is. The coordination is in the log."

---

### SHOT 10 — The Full Thread View: koad/juno#25 Timeline
**What it proves:** The entire Alice build — from brief to delivery to fact-check to fix — is one GitHub issue thread. Complete audit trail. No external tools needed.

**Capture:**
1. Open `https://github.com/koad/juno/issues/25` in browser
2. Zoom out browser to 67% or 75% to fit the full comment timeline on screen
3. Frame: issue title bar + all comment avatars/timestamps in the sidebar or main thread, showing the complete chain of 5+ comments

**Framing notes:**
- This is the "closing shot" — emphasize the completeness of the record
- If the thread is too long at any zoom level, use a tall screenshot tool (or browser "save as PDF" then screenshot a full-page render) to capture the whole timeline
- Annotation option: add arrows in post-production pointing to each entity's comment (Vulcan, Juno, Veritas, koad) — label them for the tweet visual

**Tweet context:** "Final tweet — One GitHub issue. Five entities. Brief → build → delivery → fact-check → fix → publish. The whole coordination chain is public. Anyone can audit it."

---

## Capture Order (Field Sequence)

| # | Shot | Machine | Tool | Approx time |
|---|------|---------|------|------------|
| 1 | juno#25 issue body | thinker (browser) | Firefox | 2 min |
| 2 | Juno answers Vulcan | thinker (browser) | Firefox | 2 min |
| 3 | vulcan#35 issue body | thinker (browser) | Firefox | 2 min |
| 4 | Vulcan delivery report | thinker (browser) | Firefox | 3 min |
| 5 | Veritas HOLD verdict | thinker (browser) | Firefox | 3 min |
| 6 | Veritas diff table | thinker (browser) | Firefox | 2 min |
| 7 | koad confirms fix | thinker (browser) | Firefox | 1 min |
| 8 | Commit logs 3-pane | fourty4 (terminal) | tmux | 5 min |
| 9 | Cross-entity grep | fourty4 (terminal) | bash | 3 min |
| 10 | Full thread timeline | thinker (browser) | Firefox | 3 min |

**Total capture time:** ~26 min. Build the tmux layout for Shot 8 first (runs independently), then do all browser shots consecutively on thinker.

---

## File Naming Convention

```
shot-01-juno25-assignment.png
shot-02-juno25-juno-answers-blockers.png
shot-03-vulcan35-build-plan.png
shot-04-vulcan35-delivery-report.png
shot-05-juno25-veritas-hold.png
shot-06-juno25-veritas-diff-table.png
shot-07-juno25-fix-confirmed.png
shot-08-commit-logs-3pane.png
shot-09-cross-entity-grep.png
shot-10-juno25-full-thread.png
```

Drop all captures into:
`~/.rufus/productions/2026-04-08-coordination/assets/`

---

## Handoff to Faber

When all 10 shots are captured:
- Faber needs them to draft the tweet thread (10–15 tweets)
- Key framing Faber should use per shot is noted in "Tweet context" fields above
- Faber's primary argument: "No Slack, no meetings, no lost context — just files and git"
- Shot 8 (commit logs side by side) and Shot 5 (Veritas HOLD) are the two highest-impact visuals — Faber should feature these in tweets 1–2 to hook technical readers

## Handoff to Mercury

After Faber drafts the thread:
- Mercury schedules for Twitter/X #AIAgents #OpenSource + Mastodon #fediverse
- Retweet hook to #selfhosted community
- Thread goes out Tuesday April 8 — do not publish before Veritas clears Day 4 post (separate track)

---

## Backup Shots (if primary capture fails)

| Primary | Backup |
|---------|--------|
| Shot 8 (3-pane tmux) | Two separate terminal screenshots side by side (faber + juno), vulcan dropped |
| Shot 9 (grep hits) | Manual `git log --oneline -8` for each entity, annotated with arrows in post |
| Shot 10 (full thread) | Three sequential browser screenshots of juno#25 scrolled to different sections |
