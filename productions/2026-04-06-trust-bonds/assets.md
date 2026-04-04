---
production: "Trust Bonds Aren't Policy—They're Cryptography"
date: 2026-04-06
pillar: Reality
owner: Rufus (production assets)
faber-brief: ~/.faber/content-calendar/REALITY-2026-04-03.md (Sunday April 6 section)
status: ready
---

# Production Assets — April 6 Trust Bonds Post

Faber writes the post. Rufus supplies the visual evidence. Everything below is captured on **thinker** unless noted.

---

## 1. Screenshot Shot List

### 1a. Bond Directory Structure
**Goal:** Show that trust bonds are real files on disk, not admin settings.

```
~/.juno/trust/bonds/
```

**Capture:** `ls -la ~/.juno/trust/bonds/` — shows paired `.md` + `.md.asc` files side by side, file sizes, timestamps. Terminal width ~120 cols, clean prompt, no scrollback clutter.

**Key visual:** The `.md` / `.md.asc` pairing — human-readable policy next to cryptographic proof, sitting right alongside each other.

Suggested shot sequence:
1. `ls -la ~/.juno/trust/bonds/` — full listing, all bonds visible
2. Zoom/highlight: one pair (`juno-to-faber.md` + `juno-to-faber.md.asc`) to show the naming convention clearly

---

### 1b. The Bond File Itself (`.md`)
**Goal:** Show the YAML frontmatter + readable authorization scope.

File: `~/.juno/trust/bonds/koad-to-juno.md`

**Capture:** `cat ~/.juno/trust/bonds/koad-to-juno.md` scrolled to show:
- YAML header (`type`, `from`, `to`, `status`, `created`, `renewal`)
- Bond Statement paragraph
- The `Authorized Actions` section (most compelling — concrete list of what IS and IS NOT allowed)

Two screenshots if it doesn't fit in one frame:
1. Top: frontmatter + bond statement
2. Bottom: authorized/not-authorized lists + signing block

---

### 1c. The Signature File (`.md.asc`)
**Goal:** Show the PGP signature block — this is the cryptographic artifact.

File: `~/.juno/trust/bonds/koad-to-juno.md.asc`

**Capture:** `cat ~/.juno/trust/bonds/koad-to-juno.md.asc` — reader sees `-----BEGIN PGP SIGNED MESSAGE-----` header, the bond content, then `-----BEGIN PGP SIGNATURE-----` block.

**Key visual:** The signature block itself (`wsFcBAEBCAAQ...`) — this is what makes it cryptographic, not a pinky promise.

---

### 1d. Live Verification Command
**Goal:** Show `gpg --verify` succeeding in real time.

**Capture:** Run the command (see Section 2 below), screenshot the output showing `Good signature from "Juno <juno@kingofalldata.com>"` or the koad key.

This is the money shot — verification passing = trust bond is real.

---

### 1e. Trust Chain Visualization
**Goal:** Show how bonds chain from root to entities.

**Capture:** The trust chain diagram from inside `koad-to-juno.md` (already ASCII-rendered):

```
koad (root authority, creator)
  └── Juno (authorized-agent)
        ├── Vulcan (authorized-builder)
        ├── Mercury (peer)
        ├── Veritas (peer)
        ├── Muse (peer)
        └── Sibyl (peer)
```

Either screenshot the `cat` output showing this block, or Faber can embed it directly in the post from the code block in Section 3 below.

---

### 1f. File Count / Ecosystem Scale
**Goal:** Show breadth — this isn't one bond, it's a whole trust graph.

**Capture:**
```bash
ls ~/.juno/trust/bonds/*.md | wc -l
```
Then follow with:
```bash
ls ~/.juno/trust/bonds/*.md | sed 's/.*bonds\///' | sed 's/\.md//'
```
Shows all bond names (koad-to-juno, juno-to-faber, juno-to-rufus, etc.) as a clean list.

---

## 2. Terminal Commands — Screenshot-Worthy Verification Sequence

Run these in order on **thinker**. Use a clean terminal session (new window, `clear` before each command). Font: monospace 14pt+, dark theme preferred.

### Command 1 — List the bond directory
```bash
ls -la ~/.juno/trust/bonds/
```
Expected output: paired `.md` / `.md.asc` files, timestamps from 2026-04-02 and 2026-04-03.

---

### Command 2 — Show a bond file header
```bash
head -20 ~/.juno/trust/bonds/koad-to-juno.md
```
Shows YAML frontmatter and bond statement cleanly without scrolling.

---

### Command 3 — Show the signature file
```bash
cat ~/.juno/trust/bonds/koad-to-juno.md.asc | head -10
echo "..."
tail -10 ~/.juno/trust/bonds/koad-to-juno.md.asc
```
Shows opening PGP header and closing signature block in one clean frame.

---

### Command 4 — Verify the bond (the key screenshot)
```bash
gpg --verify ~/.juno/trust/bonds/koad-to-juno.md.asc
```
Expected output:
```
gpg: Signature made Thu Apr  2 ...
gpg: using RSA key A07F8CFECBF6B982EEDAC4F362D5C4866C247E00
gpg: Good signature from "koad (Jason Zvaniga) <koad@koad.sh>"
```
**This is the post's hero screenshot.** "Good signature" in green (if terminal colorizes gpg output) is the proof point.

---

### Command 5 — Show bond count
```bash
echo "Active trust bonds:" && ls ~/.juno/trust/bonds/*.md | wc -l
```
Then the bond name list:
```bash
ls ~/.juno/trust/bonds/*.md | xargs -I{} basename {} .md
```

---

### Command 6 — Show the bond is part of git history
```bash
cd ~/.juno && git log --oneline -- trust/bonds/koad-to-juno.md
```
Shows when the bond was committed — proof it's version-controlled, not just a loose file.

---

## 3. Bond File Format — Code Block for Post

Use `juno-to-faber.md` + its `.asc` as the example (peer bond, illustrates the Faber authorization that Faber's readers will find meaningful).

### The Bond (`.md`)

```markdown
---
type: peer
from: Juno (juno@kingofalldata.com)
to: Faber (faber@kingofalldata.com)
status: ACTIVE — signed by Juno 2026-04-03
visibility: private
created: 2026-04-03
renewal: Annual (2027-04-03)
---

## Bond Statement

> I, Juno, recognize Faber as a peer entity in the koad:io team. Faber is the content
> strategist and creative director — named for the Latin craftsman. Faber owns the content
> strategy layer: what content gets made, for whom, and why. Faber works upstream of Rufus
> (who produces) and Mercury (who distributes). Juno gestated Faber and is his mother entity,
> but Faber operates autonomously within his specialty.

## Scope

Faber is authorized to:
- Own content strategy and creative direction for the koad:io ecosystem
- Commission Sibyl for audience and market research
- Direct Rufus on what to produce
- Coordinate with Mercury on content calendar
- Align with Iris on brand voice and positioning
- File issues on any team repo related to content strategy

Faber is NOT authorized to:
- Publish directly to external platforms (Mercury owns publish)
- Override Iris's brand positioning decisions
- Sign trust bonds on Juno's behalf

---

*Signed: Juno, 2026-04-03*
```

### The Signature (`.md.asc`) — truncated for readability

```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA512

[bond content above]

-----BEGIN PGP SIGNATURE-----

iQJLBAEBCgA1FiEEIKdMHsC2prkZ5S2bECA499BndawFAmnQEBwXHGp1bm9Aa2lu
Z29mYWxsZGF0YS5jb20ACgkQECA499Bndaz8/Q/+N70/jfNk+yb1tLP0vrumZIKa
[... signature body ...]
p4b3UROicSSJ/OtqIcc=
=MFnj
-----END PGP SIGNATURE-----
```

### The verification command

```bash
gpg --verify ~/.juno/trust/bonds/juno-to-faber.md.asc
```

Faber can tell readers: "That signature block is what makes this cryptographic governance, not just a Notion doc someone can edit."

---

## 4. Production Notes

- **Machine:** thinker (primary ops) — bond files live in `~/.juno/trust/bonds/`
- **Terminal setup:** new window, `clear`, dark theme, 14pt+ monospace
- **Scroll position:** show full command + output in single frame where possible; if output wraps, crop cleanly at the bottom
- **gpg output color:** if thinker's gpg colorizes "Good signature" in green, capture that — it reads clearly in screenshots
- **No personal info:** `koad-to-juno.md` shows `koad@koad.sh` and `Jason Zvaniga` — these are already public in the bond files and git history; confirm with koad before publishing if he wants these obscured in screenshots
- **Fallback:** if gpg verify fails on thinker (key not imported locally), use `juno-to-faber.md.asc` with Juno's key — or note in the post that readers can verify with the public key at keybase.io/koad

---

## 5. Handoff to Faber

Once screenshots are captured:
1. Drop screenshots into this directory: `~/.rufus/productions/2026-04-06-trust-bonds/screenshots/`
2. Faber references them from `~/.faber/posts/2026-04-06-trust-bonds.md`
3. Mercury schedules distribution (HackerNews, Dev.to, Mastodon) per the calendar

Bond file source of truth: `~/.juno/trust/bonds/` — Faber can link directly to these in the public GitHub repo when the post goes live.
