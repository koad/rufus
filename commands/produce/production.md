---
status: draft
owner: rufus
priority: high
description: End-to-end production orchestration from content brief through Mercury delivery
---

## Purpose

The `produce` command is the high-level production orchestrator. It guides operators through the entire production workflow: session planning, hardware setup, recording, post-production coordination, and asset delivery. This is the primary user-facing command for end-to-end content production.

## Interface

**Commands:**
- `rufus produce start <SESSION_NAME>` — Begin new production session
- `rufus produce status` — Show current production status
- `rufus produce complete` — Finalize and hand off to Mercury

**Arguments:**
- `SESSION_NAME`: Human-readable session identifier (e.g., "interview-kubernetes-scaling")
- `--type` (required): video-interview | podcast-audio | live-stream | screen-recording
- `--creator` (optional): Content creator entity (default: faber)
- `--duration` (optional): Expected session duration in minutes
- `--hardware` (optional): Override default hardware selection
- `--checklist` (optional): Show pre-production checklist

**Output:** Production session manifest with next steps and guidance

## Specification

**Production Workflow:**

1. **Planning Phase**
   - Create production session with metadata
   - Load workflow type template
   - Review hardware requirements
   - Generate pre-production checklist

2. **Setup Phase**
   - Check hardware health (all devices online)
   - Synchronize clocks across devices
   - Load OBS scene for workflow type
   - Run test recording (quick verification)
   - Verify all sources (cameras, mics, screen capture)

3. **Recording Phase**
   - Confirm operator ready
   - Start recording on all devices
   - Monitor real-time metrics (bitrate, dropped frames, CPU)
   - Alert on issues (microphone failure, storage full, etc.)
   - Collect feedback from participants

4. **Finalization Phase**
   - Stop recording across all devices
   - Verify all recordings completed successfully
   - Compute checksums and generate asset manifest
   - Organize files per asset-naming-conventions.md
   - Create asset summary

5. **Post-Production Coordination**
   - Prepare editing notes (color, audio, pacing)
   - Assign to Faber if needed (or use archive version)
   - Set deadlines and expectations
   - Track editing progress

6. **Export & Delivery**
   - Transcode to all platform formats (YouTube, podcast, etc.)
   - Validate all exports
   - Create delivery package
   - Hand off to Mercury
   - Archive raw recording

**Session Manifest:**
```json
{
  "session_id": "2026-04-03-interview-kubernetes-scaling",
  "type": "video-interview",
  "creator": "faber",
  "start_time": "2026-04-03T14:00:00Z",
  "expected_duration_minutes": 45,
  "hardware": ["flowbie", "fourty4"],
  "phase": "post_production",
  "checklist": {
    "planning": {"status": "complete"},
    "setup": {"status": "complete"},
    "recording": {"status": "complete", "recordings": 2},
    "finalization": {"status": "complete"},
    "post_production": {"status": "in_progress"},
    "export": {"status": "pending"},
    "delivery": {"status": "pending"}
  },
  "assets": [
    {
      "id": "2026-04-03-faber-interview-kubernetes-scaling-001",
      "file": "/home/koad/.rufus/media/2026/04/raw/2026-04-03-faber-interview-001.mp4",
      "status": "raw"
    }
  ],
  "next_steps": [
    "Review post-production notes",
    "Coordinate with Faber on editing timeline",
    "Transcode for distribution when ready"
  ]
}
```

**Behavior:**
1. Load workflow template based on session type
2. Execute checklist items in sequence (with operator prompts)
3. Delegate to specialized commands (record, hardware, obs, asset)
4. Track overall progress through phases
5. Provide guidance and next steps at each phase
6. Log all decisions and metadata for audit trail
7. Alert on deviations from template (missing checks, timeouts, etc.)

**Guidance & Rollback:**
- Show helpful tips for each phase
- Suggest recovery procedures for common issues
- Allow rollback to previous phase if needed
- Preserve decision audit trail

**Edge cases:**
- Participant cancels → archive recordings, mark session as partial
- Technical failure → rollback to last successful phase, retry
- Post-production delayed → escalate and request timeline update
- Hardware failure mid-session → fail gracefully, preserve recordings from working devices

## Dependencies

- `recording-workflows.md` (workflow templates)
- `hardware-orchestration.md` (device health and sync)
- `obs-configuration-management.md` (scene management)
- `asset-naming-conventions.md` (file organization)
- `post-production-direction.md` (editing guidance)
- `export-standards.md` (delivery formats)

## Status Note

Not yet built. This is the top-level orchestration command that ties together all Rufus capabilities.
