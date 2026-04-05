---
title: "Director's Notes — Show HN: Agent Home Directory"
video: 2026-04-10-show-hn-agent-home-directory
author: Rufus
date: 2026-04-05
status: production-ready
---

# Director's Notes: "Show HN: Agent Home Directory"

## Why This Video Matters

This video is designed for the HackerNews audience — people who distrust marketing, run their own infrastructure, and will verify every claim you make. Three commands. No narrated demo. No pitch. Identity file, cryptographic authorization, commit history. The entire koad:io argument condensed to four and a half minutes of terminal output that anyone can reproduce.

---

## System State at the Start of Recording

This video has fewer moving parts than the Sibyl video, but the one that matters — GPG verification — cannot be faked, worked around, or retaken in isolation. If `gpg --verify` does not return "Good signature," there is no video.

**Machine: thinker. Preferred.**
The video's thesis is that this runs on ordinary hardware. Recording on thinker, named thinker, is part of the argument. If you must record on another machine, the git log author check and entity path still work — but the machine narrative is weakened.

**What must be true before recording begins:**

- `~/.juno` is current: `cd ~/.juno && git pull` — run this, verify no merge conflicts
- `git log --author="Juno" --oneline` returns output: run this before recording and note the commit count. You will reference a specific number on camera. Do not be surprised mid-take.
- GPG key for Juno is imported locally: `gpg --list-keys juno@kingofalldata.com` — if it is not found, import it now. Do not discover this during the take.
- `gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc` returns "Good signature from Juno" — run this in a separate terminal before recording. If it fails, stop. Do not proceed to recording until this returns clean.
- `~/.juno/trust/bonds/juno-to-sibyl.md` exists and is readable: `cat ~/.juno/trust/bonds/juno-to-sibyl.md` — confirm it is not empty.
- `~/.juno/memories/001-identity.md` exists and is current.

**Window arrangement:**
- One fullscreen terminal. Nothing else on screen.
- Shell prompt: bare minimum — `PS1='$ '` or `PS1='thinker $ '`. No git branch display, no powerline, no color escapes. The HN audience will notice powerline glyphs.
- Font: 16–18px monospace. White on black (#000000). Confirmed legible at 720p — test this before recording.
- Scrollback buffer: 10,000+ lines. The git log may produce 200+ lines; none of them should fall out of buffer during the take.
- No notifications. No other windows. No browser tabs. Nothing that could steal focus or produce a notification sound.

**Immediately before hitting record:**
```bash
clear && printf '\033[3J'
```
Then start asciinema or OBS. Then wait 3 seconds in silence. Then speak.

---

## The Three Money Shot Moments

### Money Shot 1: "Good signature from Juno" (Shot 3, ~1:05–1:20)

The GPG verify output returning "Good signature from Juno \<juno@kingofalldata.com\>" is the moment that separates this video from every other AI agent demo. It is not a config file. It is not a role parameter. It is a cryptographic authorization that can be independently verified by any viewer who clones the repo and has GPG installed. When that line appears — stop speaking. Let the viewer read it. Then speak.

**What needs to be visible:** The full gpg verify output: signature made date, key ID, and "Good signature from..." line. All three lines. Do not cut before all three are on screen.

**What to say after the line appears:** "Good signature. That's not a config setting. That's a signed authorization agreement, verifiable by anyone." Then move to `cat` the bond file. Do not rush.

### Money Shot 2: The git log filling the screen (Shot 4, ~2:00–3:30)

The commit history scrolling — 200+ lines, six days of named decisions — is the emotional core of the video. The density of that scroll is the argument. More than any voice-over line, more than any title card, watching that log fill the terminal and keep going is what makes the viewer stop and reconsider the premise. This shot cannot be cut. Cannot be sped. Cannot be piped to head.

**What needs to be visible:** The full git log scroll, continuous, until it reaches the terminal bottom or the first commit. The commit messages themselves — not a count, not a summary — scrolling past. Your VO should call out 3–4 specific commit messages by name as they pass. Pick ones that tell a story: the gestation commit, an Alice delivery, a Chiron bootstrap, a trust bond commit.

**What to resist:** The urge to stop the scroll and zoom in on one commit. Do not stop the scroll. Do not annotate live. Name commits in VO as they pass and keep going.

### Money Shot 3: The clone close (Shot 6, ~4:00–4:45)

`git clone https://github.com/koad/juno` typed slowly, executed, and then `cat juno/memories/001-identity.md` showing the same identity file the video opened with — this is the call to action disguised as a demonstration. The viewer sees that the entire thing is one `git clone` away from being on their machine. The closing VO lines ("Not vaporware. Not a demo. Commits.") each land on their own breath. The pauses between them are not dead air — they are editorial beats.

**What needs to be visible:** The clone command executing cleanly, the cat command showing the identity file content matching Shot 2's output. The parallelism is the point — the video opened with `cat ~/.juno/memories/001-identity.md` and closes with `cat juno/memories/001-identity.md`. Same file. Different path. That is the entire pitch.

**What to say:** Exactly what is in the script. No additions. The three closing lines are already at the minimum necessary length.

---

## Fallback Plan If a Demo Command Fails

### If GPG verify returns anything other than "Good signature"
- Stop recording immediately. This is the hardest failure condition because it may happen mid-take, after Shot 2.
- In a separate terminal, diagnose: `gpg --list-keys juno@kingofalldata.com` — is the key present? `gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc` — what is the exact error?
- Common causes: key not imported, expired key, bond file modified without re-signing.
- Do not publish any recording where GPG verify did not return "Good signature." The video's credibility claim is entirely dependent on this line.
- Restart from Shot 1 once the issue is resolved and a clean verify is confirmed.

### If git log returns zero commits or wrong author
- Stop recording. In a separate terminal: `git -C ~/.juno log --author="Juno" --oneline | head -5` — verify the author string is exactly "Juno" (capital J, no email).
- The `--author` flag matches on a substring — if commits were made with a different author string, adjust the flag: `--author="juno@kingofalldata.com"` or use `--all-match` with both name and email.
- If the log is genuinely empty, the working directory is wrong. Confirm `~/.juno` is the correct path and it is current via `git pull`.

### If the take runs past 6 minutes
- Most likely cause: over-narrating Shot 2 (identity file) or adding commentary inside the git log scroll.
- Shot 2 fix: reduce VO to two sentences — one when the file starts, one when it finishes. Do not narrate individual sections of the file.
- Shot 4 fix: call out 3 commits only. Not 6. Name them as they scroll and stop. The scroll carries the rest.
- Do not shorten the closing pauses (Shot 6). Do not cut the git log scroll. Trim VO, not footage.

### If `git clone` fails during Shot 6 (network error)
- This is the least critical failure — it is the last shot and the video's argument is already made by this point.
- Stop recording, wait for network, retry from Shot 6 only. You do not need to redo Shots 1–5.
- If the clone is genuinely unavailable (GitHub outage), acknowledge it in VO naturally: "The repo is at github.com/koad/juno — if you're watching this later, it'll be there." Then cut.

### If a window notification or focus event appears during recording
- Stop recording. This is non-negotiable for a video targeting the HN audience — they will notice and comment.
- Disable all notifications before beginning. Check: Do Not Disturb enabled, Slack/Discord closed, no scheduled cron output, no email alerts.
- Restart from Shot 1.

---

## Pacing Guide

| Shot | Pace | Why |
|------|------|-----|
| Shot 1 (empty terminal) | 3 seconds silence, then one sentence | Clean cut point; opening line lands in silence |
| Shot 2 (cat identity) | Let file scroll, VO in two beats | Don't race; the length of the file is its own credential |
| Shot 3 (gpg verify) | PAUSE after "Good signature" | Let viewer read the line; then speak |
| Shot 3 (cat bond) | Medium — let it display | The bond contents are readable; give viewer time |
| Shot 4 (git log) | SLOWEST narration — one commit cluster at a time | Volume is the evidence; the scroll is the argument |
| Shot 4 (wc -l) | Slow type, hold on output | Let viewer do the math; don't race past the number |
| Shot 5 (remote -v) | Brief, deliberate | Bridge shot; set up the close cleanly |
| Shot 6 (clone) | Deliberate typing, clean execution | This is the call to action; unhurried confidence |
| Shot 6 (cat close) | SLOWEST — one sentence per breath | Three closing lines, three pauses; do not compress |
| Shot 7 (fade) | Hold 1–2 seconds before cut | Clean ending; no rush |

The single pacing mistake this video is most likely to make: speaking over the git log scroll. The scroll is the argument. Your voice is supplementary annotation. If you are narrating continuously while the log scrolls, you are competing with it. Call out 3 commits, then stay quiet until the scroll finishes.

---

## Production-Specific Warnings

**The HN audience reads code.** Any typo, any corrected command, any `^C` mid-take will be commented on. The retake trigger for this video is "any typo requiring more than one backspace." Stage every command before recording — have them in a notes file, not typed from memory. The four core commands are: `cat ~/.juno/memories/001-identity.md`, `gpg --verify ~/.juno/trust/bonds/juno-to-sibyl.md.asc`, `cat ~/.juno/trust/bonds/juno-to-sibyl.md`, `git -C ~/.juno log --author="Juno" --oneline`. Have these exact strings in clipboard rotation before recording.

**No music. No end card.** This is the one video in the schedule that explicitly ends on silence and fade to black. Music would undercut the HN positioning. An end card would look like marketing. The HN audience came for the terminal. Give them terminal.

**Know the commit count before you speak it.** Run `git -C ~/.juno log --author="Juno" --oneline | wc -l` in a separate terminal before recording. Whatever that number is, it is the number you say on camera. Do not guess, do not round. Say the exact number.

**The asciinema title in the recording command contains the phrase "Three Commands."** That framing must match the VO — Shot 1 opens with "Three commands. That's all I'm going to run." If the VO changes, update the asciinema title before recording. Mismatched metadata looks sloppy and the HN audience will notice.
