---
status: draft
owner: rufus
priority: high
description: Guide and coordinate post-production editing, color grading, and audio mixing
started: 2026-04-03
---

## Purpose

After raw recording, Rufus guides the post-production direction: editing instructions, color correction, audio mixing, caption generation, and asset delivery. While Faber may perform editing, Rufus owns the creative direction and quality standards.

## Specification

**Input:** Raw recording asset and metadata

**Output:** Editing instruction document, color/audio mix notes, delivery checklist

**Post-Production Tasks:**

1. **Editing Instructions:**
   - Identify good takes and bad takes
   - Mark sections to trim or remove
   - Flag segments for caption generation
   - Specify music/ambient audio placement
   - Note graphics or overlay requirements

2. **Color Grading:**
   - Define color space and tone (warm, cool, neutral, cinematic)
   - Provide reference images or color grades
   - Specify brightness/contrast/saturation targets
   - Flag any color correction issues in raw footage

3. **Audio Mixing:**
   - Balance speaker levels
   - Remove background noise or hum
   - Specify EQ or compression targets
   - Place background music/ambient audio
   - Normalize loudness to standards (LUFS)

4. **Caption & Transcript:**
   - Provide or generate transcript
   - Generate captions (SRT or VTT)
   - Flag important terms or technical words for accuracy
   - Note speaker identification requirements

5. **Delivery Checklist:**
   - Verify final duration matches target
   - Confirm encoding matches distribution standards
   - Validate captions/metadata completeness
   - Generate final asset manifest
   - Hand off to Mercury for publication

**Behavior:**
- Review raw recording immediately after capture
- Generate editing notes document (Markdown) within 24 hours
- Provide color reference images or grades
- Coordinate with Faber on editorial decisions
- Quality gate before Mercury receives final asset

**Edge cases:**
- Recording has major technical issues → recommend re-recording or partial salvage
- Raw footage longer than expected → prioritize sections or request editing decisions
- Audio quality poor → determine if salvageable with mixing or needs re-recording

## Implementation

Not yet built. Needs:
1. post-production-template.md (editing instruction template)
2. review-recording.sh (automated quality assessment)
3. generate-edit-notes.sh (instruction document generation)

## Dependencies

- Recording workflows (need raw assets)
- Asset naming conventions (track versions through editing)
- Encoding standards (final delivery specifications)

## Testing

Acceptance criteria:
- [ ] Recording reviewed within 24 hours of capture
- [ ] Editing notes generated and delivered to Faber
- [ ] Color/audio corrections applied successfully
- [ ] Final asset meets quality standards
- [ ] Captions verified for accuracy
- [ ] Handoff to Mercury accepted without revisions

## Status Note

Concept defined but process not yet operationalized. Requires integration with Faber and Mercury.
