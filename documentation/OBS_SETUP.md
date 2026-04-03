# OBS_SETUP.md — Scene Configuration & Multi-Source Routing

**Status:** In progress (VESTA-SPEC-013 placeholder)

This document specifies OBS scene templates, source configuration, audio routing, and multi-source orchestration across flowbie, fourty4, and other recording hardware.

## Content

### Scene Templates
- **Interview** — Two-camera or web-cam focused, guest + host layout
- **Screen Recording** — Code walkthrough or demo with optional face-cam
- **Live Stream** — Twitch/YouTube streaming with audience interaction
- **Multi-Camera** — Coordinated recording from multiple physical locations
- **Podcast** — Audio-focused with optional video (speaker video or static background)

### Audio Routing & Mixing
- **Input sources** — Microphones, system audio, guest feeds
- **Mixing levels** — Speaker balance, background audio, music placement
- **Filters & effects** — Noise suppression, compression, EQ
- **Output routing** — Stream bitrate, local recording file, remote streaming

### Source Configuration
- **Cameras** — Resolution, frame rate, color space, focus/exposure settings
- **Display capture** — Screen scaling, refresh rate optimization
- **Audio devices** — Sample rate, channel configuration, latency compensation
- **Remote feeds** — NDI, RTMP, or other network sources from other hardware

### Multi-Source Orchestration
- **Clock synchronization** — NTP sync across devices for smooth multi-source editing
- **Remote OBS control** — Command and monitor OBS instances on remote hardware
- **Unified switching** — Scene switching across distributed sources
- **Monitoring & failover** — Detect dropped sources, switch to fallback

### Quality Monitoring
- **Bitrate & dropped frames** — Real-time monitoring during stream/record
- **CPU usage** — Alert if encoding falls behind
- **Network bandwidth** — Track stream quality vs. available bandwidth
- **Storage** — Monitor disk space on all recording devices

See `../features/` for related specifications:
- `obs-configuration-management.md` — Scene config management and version control
- `hardware-orchestration.md` — Multi-device coordination
- `encoding-standards.md` — Codec and bitrate presets

---

**To be filled in:** OBS scene templates must be designed and tested on flowbie. This document will contain exported OBS XML configurations and setup procedures once finalized.
