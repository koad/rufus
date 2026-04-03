# HARDWARE_MANIFEST.md — Recording Equipment Inventory

**Status:** In progress (VESTA-SPEC-013 placeholder)

This document inventories all hardware used by Rufus for recording and streaming: locations, devices, capabilities, network topology, and operational status.

## Content

### Locations & Devices
- **flowbie** — 24/7 studio (Linux, X11, OBS instance, connected cameras/mics)
- **fourty4** — Mac Mini with inference (macOS, ollama, recording capability)
- **thinker** — Primary coordination and ops node
- **Cameras, microphones, capture devices** — Network connectivity, format support

### Device Capabilities
- Recording formats (video resolution, frame rate, codecs)
- Audio input channels and formats
- Network bandwidth and latency
- Storage capacity and network access
- Encoding and streaming capability

### Network Topology
- Inter-device communication (Ethernet, WiFi)
- Latency and synchronization requirements
- Firewall and trust bond configuration
- Backup and failover paths

### Operational Status
- Device health monitoring
- Disk space and resource usage
- Clock synchronization across devices
- Recent changes and maintenance log

See `../features/` for related specifications:
- `hardware-orchestration.md` — Device coordination logic
- `obs-configuration-management.md` — OBS setup per location

---

**To be filled in:** Hardware inventory must be compiled from operational survey. See CLAUDE.md section "Hardware orchestration" for initial device list.
