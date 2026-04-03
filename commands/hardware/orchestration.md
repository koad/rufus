---
status: draft
owner: rufus
priority: critical
description: Check hardware status, health diagnostics, and multi-device orchestration
---

## Purpose

Rufus must query and manage the health of all recording hardware (flowbie, fourty4, thinker). This command provides real-time status, diagnostics, and coordination capabilities for multi-source recording sessions.

## Interface

**Commands:**
- `rufus hardware status` — Show current status of all devices
- `rufus hardware health` — Run full diagnostics on all hardware
- `rufus hardware sync` — Synchronize clocks across devices for multi-source recording
- `rufus hardware inventory` — List all devices, capabilities, and storage

**Output:** JSON with device status, resource usage, capabilities

## Specification

**Device Status Response:**
```json
{
  "timestamp": "2026-04-03T14:30:00Z",
  "devices": {
    "flowbie": {
      "status": "online",
      "uptime_hours": 342,
      "os": "linux",
      "cpu_percent": 15,
      "memory_percent": 42,
      "disk_free_gb": 450,
      "network_latency_ms": 2,
      "obs_status": "ready",
      "cameras": 2,
      "microphones": 3
    },
    "fourty4": {
      "status": "online",
      "uptime_hours": 18,
      "os": "macos",
      "cpu_percent": 28,
      "memory_percent": 65,
      "disk_free_gb": 120,
      "network_latency_ms": 8,
      "recording_capable": true
    },
    "thinker": {
      "status": "online",
      "uptime_hours": 96,
      "os": "linux",
      "cpu_percent": 5,
      "memory_percent": 22,
      "disk_free_gb": 850,
      "network_latency_ms": 0
    }
  },
  "summary": {
    "all_online": true,
    "critical_alerts": 0,
    "warnings": ["fourty4 disk space low"]
  }
}
```

**Health Diagnostics:**
- CPU load and temperature
- Memory usage and available swap
- Disk space and I/O performance
- Network connectivity and latency
- OBS status and encoding capability
- Camera/microphone availability
- Clock offset from NTP reference

**Clock Synchronization:**
- Check clock offset on all devices
- Resync via NTP if drift > 100ms
- Report precision achieved post-sync

**Edge cases:**
- Device unreachable → mark as offline, don't block other devices
- High latency detected → warn about streaming implications
- Clock drift excessive → require re-sync before multi-device recording
- Storage critically low → alert and suggest cleanup

## Dependencies

- `hardware-orchestration.md` (device definitions)
- `HARDWARE_MANIFEST.md` (inventory reference)

## Status Note

Not yet built. Requires SSH/trust bond access to all hardware devices.
