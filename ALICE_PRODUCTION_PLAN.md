# Alice Content Production Plan

**Status:** Planning phase  
**Priority:** Faber's 2-week calendar, Week 1  
**Owner:** Rufus (production) + Faber (content creation)  
**Target:** Record first three pieces of Alice content this week

---

## Content Pieces (Faber's 2-Week Focus)

### 1. "Come Meet Alice" (5–10 min intro)
**What:** Introduction to Alice and the 12-level curriculum  
**Who:** Faber + one learner (guest)  
**Screen Content:** 
- Brief conceptual explainer about Alice's role
- Visual walkthrough of the 12 levels (could be text overlay, slides, or diagram)
- Guest perspective: "Why would I take this journey?"

**Format Options:**
- **Option A (Lean):** Terminal-based walkthrough showing the livy CLI, with voiceover
- **Option B (Polished):** Simple presentation with slides + talking heads video of Faber/guest
- **Recommended:** Option A — raw and honest, shows the actual tool, no PWA dependency

**Recording Setup:** flowbie + screen capture + guest audio (local mic or remote)

---

### 2. "Alice Walks Through Level 1: What Is Sovereignty?" (15–20 min)
**What:** A guided walkthrough of the first level — reading the concept, thinking out loud, reflecting on ownership

**Who:** Faber (guide) + one learner (protagonist)  
**Screen Content:**
- Level 1 curriculum text (from ~/.livy/documentation/alice-curriculum/01-sovereignty.md)
- Reflection exercise: "What do I own right now?" (handwritten notes, typed response, or verbal)
- Terminal showing livy interface (if available)

**Flow:**
1. Introduction: "Here's what you're about to explore"
2. Read Level 1 together (Faber reads or provides voiceover)
3. Reflection: Learner thinks out loud about what they own
4. Mentor moment: Faber (as Alice) helps deepen understanding
5. Transition: "You're ready for Level 2"

**Format:** Screen recording (document/text) + talking heads + voiceover

**Recording Setup:** flowbie + screen capture + dual audio (Faber + learner)

---

### 3. "The Graduation Moment" (5–10 min)
**What:** Alice signs the mastery certificate — the moment a learner becomes sovereign

**Who:** Faber (as Alice) + one learner  
**Screen Content:**
- Terminal showing the mastery challenge submission (`livy master --submit`)
- Alice reviewing the work (conceptual — could be voiceover)
- Certificate signing (`livy master --approve [name]`)
- Certificate verification (showing the file, explaining what it proves)

**Emotional Arc:**
1. Learner submits their mastery work (nervous, hopeful)
2. Alice reviews (thoughtful narration)
3. Alice signs the certificate (cryptographic moment — make it feel significant)
4. Learner sees their name in the signature (celebration)
5. Verification: "This is real. You can share this. You're ready."

**Format:** Terminal walkthrough + narration + reaction/celebration

**Recording Setup:** flowbie + screen capture + guest audio

---

## Screen & UI Assumptions

**Alice has NO PWA yet.** So we're recording:
1. **Terminal/CLI interface** (livy tool) — the actual user interaction
2. **Text editor** (curriculum reading) — the learning material
3. **Talking heads** (Faber + learner) — the relationship/mentorship dynamic
4. **Voiceover narration** — connecting the pieces

**Visual Strategy:**
- Keep terminal clean (dark background, large readable font)
- Show curriculum text clearly (20pt minimum for readability)
- Record talking heads on clean background (flowbie studio setup)
- Overlay graphics: level numbers, key concepts, timers if needed
- Use captions for terminal commands (for clarity)

---

## Can We Record This Week? YES

**What's ready:**
- ✅ Curriculum exists (complete, drafted by Livy)
- ✅ livy CLI exists and can be executed
- ✅ Hardware available (flowbie + guest connection)
- ✅ OBS on flowbie for screen capture
- ✅ Actors available (Faber as mentor, guest learner)

**What's NOT ready (OK to skip for now):**
- ❌ PWA interface (Phase 2 — not needed for terminal recordings)
- ❌ Cryptographic signing implementation (likely works, verify with livy)
- ❌ Formal asset pipeline (Mercury can ingest raw footage)

**Blocker check:**
- Can livy sign certificates? → Must verify with Livy team
- Do we have a guest learner? → Faber to arrange
- Is flowbie ready for 2+ hour recording session? → Check hardware status

---

## Minimum Viable Recording Setup (flowbie)

### Hardware:
- **Display:** Primary monitor (1920x1080 minimum)
- **Camera:** USB webcam or built-in for talking heads (1080p, 30fps)
- **Microphones:** 
  - Lavalier mic for main guest (Faber) — isolation from room noise
  - USB condenser or headset for remote guest (if applicable)
- **Audio Interface:** USB mixer or direct USB audio

### OBS Configuration:
**Scene 1: Terminal Walkthrough**
- Source 1: Screen capture (terminal + text editor)
- Source 2: Camera feed (optional, picture-in-picture or not)
- Audio: System audio (terminal, voiceover) + Mic 1 (Faber talking)

**Scene 2: Talking Heads**
- Source 1: Camera feed (close-up, clean background)
- Source 2: Lower-third graphics (name, title)
- Audio: Mic 1 (main) + Mic 2 (guest, if remote)

**Scene 3: Composite (if needed)**
- Screen + talking heads side-by-side
- Audio: Both feeds mixed

### Encoding:
- **Format:** ProRes 422 HQ or h.264 (flowbie can handle both)
- **Resolution:** 1920x1080 @ 30fps (scalable to 4K if hardware allows)
- **Audio:** 48kHz, stereo or multichannel

### Storage:
- **Location:** flowbie local drive (check available space)
- **Estimated Size:** 
  - 30 min at 1080p/30fps ProRes 422 ≈ 200GB
  - 30 min at 1080p/30fps h.264 (8Mbps) ≈ 1.8GB
  - → Use h.264 for this week, transcode to ProRes if needed

---

## Shooting Schedule (This Week)

### Pre-Production (Today—Tomorrow):
- [ ] Verify livy certificate signing capability
- [ ] Arrange guest learner with Faber
- [ ] Test flowbie OBS setup (camera, audio, screen capture)
- [ ] Do a test recording (2–3 min dry run)
- [ ] Prepare curriculum text (format for readability on screen)

### Production (Wed–Fri):
- [ ] Record "Come Meet Alice" (Session 1, ~1 hour recording time)
- [ ] Record "Level 1 Walkthrough" (Session 2, ~1.5 hour recording time)
- [ ] Record "Graduation Moment" (Session 3, ~1 hour recording time)

### Post-Production (Next Week):
- [ ] Color grade & audio mix (Mercury takes over)
- [ ] Add captions & graphics (Mercury)
- [ ] Arrange for upload to distribution channels (Mercury)

---

## Deliverables (By End of Week)

1. **Raw footage** — Three video files (MP4 or ProRes), time-logged
2. **Audio stems** — Separate tracks for voiceover, guest, ambience (if applicable)
3. **Curriculum transcript** — What was read/shown on screen (for captions)
4. **Production notes** — Timestamps, retakes, audio levels, technical notes
5. **Asset metadata** — Title, duration, participants, hardware used

---

## Known Unknowns

1. **livy certificate signing** — Does it work? Is it cryptographically sound?
2. **Flowbie storage** — How much space available? Do we need to record to external drive?
3. **Guest availability** — Who is the learner? When are they available?
4. **Remote audio** — If guest is remote, do we have quality audio capture?
5. **Editing time** — Mercury's availability for post-production this week

---

## Next Steps

1. **Verify technical blockers** (Livy team on certificate signing)
2. **Coordinate with Faber** (guest learner, shooting availability)
3. **Test flowbie setup** (OBS, audio, screen capture)
4. **File GitHub issue** on koad/juno with this plan + blockers

---

## Rationale

**Why this approach:**
- Terminal recordings are **raw and honest** — no fancy PWA to hide behind
- Shows **real koad:io interaction** — livy CLI is the actual tool
- **Scalable:** Can improve visuals later (graphics, editing) without re-shooting
- **Learner-centric:** Focus on the relationship (mentor + student), not UI gloss
- **This week feasible:** No PWA dependency, no infrastructure changes needed

**Why these three pieces:**
- "Come meet Alice" → Explains the concept (why someone would learn)
- "Level 1 walkthrough" → Shows the experience (what learning feels like)
- "Graduation moment" → Inspires hope (you can get there, it's real)

Together, they tell a complete story: Who is Alice? What will you learn? What does mastery look like?

---

**Plan filed:** 2026-04-03  
**Status:** Ready for Faber + technical verification  
**Next milestone:** Blockers cleared → Recording session scheduled  
