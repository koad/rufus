---
title: OBS Setup — Scene Configuration & Multi-Source Orchestration
owner: rufus
status: active
updated: 2026-04-05
closes-issue: https://github.com/koad/rufus/issues/1
---

# OBS Setup — Scene Configuration & Multi-Source Orchestration

This document defines OBS scene templates, source configuration, audio routing, and multi-source orchestration across the koad:io recording infrastructure (flowbie, fourty4, thinker).

---

## Installation

OBS Studio is the primary production harness on flowbie and fourty4.

```bash
# Debian/Ubuntu (flowbie)
sudo apt install obs-studio

# macOS (fourty4)
brew install --cask obs

# Verify version
obs --version
```

Minimum OBS version: **30.0+** (required for WebSocket 5.x API and NDI plugin compatibility).

---

## Hardware Targets

| Machine | OBS Role | Notes |
|---------|---------|-------|
| flowbie | Primary recording node | X11, 24/7, main studio |
| fourty4 | Secondary / inference sessions | macOS, entity session recordings |
| thinker | Coordination + command-line only | No GUI; issues recording commands via SSH |

---

## Scene Templates

### 1. Screen Recording (Coding / Terminal Demo)

**Use case:** Entity session recordings, terminal walkthroughs, code demos.

**Sources (in layer order, bottom to top):**
1. `Display Capture` — full screen, primary monitor
2. `Audio Input Capture` — microphone (suppression filter applied)
3. `Audio Output Capture` — system audio (optional)

**Scene settings:**
- Canvas: 2560x1440 (downscale to 1920x1080 for output)
- FPS: 60
- Downscale filter: Lanczos (best quality)

**Filters on Display Capture:** None (raw screen capture)

**Audio mix:**
- Mic: -12 dB gain, Noise Suppression (RNNoise), Compressor (ratio 4:1, threshold -18 dBFS)
- System: -20 dB gain (ambient only)

---

### 2. Terminal Capture (Entity Showcase)

**Use case:** Entity boot demos, git walkthroughs, "I Cloned a koad:io Entity" style content.

**Sources:**
1. `Window Capture` — target terminal emulator (not full screen — avoids dock/taskbar)
2. `Audio Input Capture` — microphone (same filters as above)
3. `Color Source` — pure black (#000000) background (fills outside terminal window)

**Scene settings:**
- Canvas: 1920x1080
- FPS: 60
- Crop terminal window to remove title bar if distracting

**Notes:**
- Set terminal to full-screen mode before capturing with `Window Capture`
- Font must be ≥16px for legibility at 720p playback
- Disable terminal transparency for capture

---

### 3. Live Stream (Entity Work — Continuous)

**Use case:** Continuous entity session streaming for OBS source content.

**Sources:**
1. `Display Capture` — full screen
2. `Audio Input Capture` — mic
3. `Text (GDI+)` — rolling status ticker (optional, bottom third)
4. `Browser Source` — optional: live git log or issue tracker overlay

**Output:**
- Stream to flowbie's RTMP output → YouTube Live or Twitch
- Simultaneous local recording at full quality

**Streaming settings (see Encoder Settings section below)**

---

### 4. Multi-Camera

**Use case:** Two-location recordings with thinker (ops) + flowbie (studio).

**Sources:**
1. `NDI Source` — remote camera feed from secondary machine (requires obs-ndi plugin)
2. `Display Capture` — local screen
3. `Video Capture Device` — local webcam (if present)
4. `Audio Input Capture` — local mic

**Switching:**
- Manual scene switch for live content
- Use Studio Mode for cut-on-the-fly without visible transition

**Prerequisites:**
- obs-ndi plugin installed on both machines
- Both machines on same network subnet (no NAT between them)
- `ndi-runtime` installed on both

---

### 5. Podcast (Audio-Primary)

**Use case:** Audio recording with optional static video background.

**Sources:**
1. `Color Source` — dark background (brand color or neutral dark)
2. `Image Source` — optional: logo or waveform graphic
3. `Audio Input Capture` — primary mic (main output)
4. `Audio Input Capture` (second instance) — secondary mic / guest (if applicable)

**Notes:**
- Record as WAV or FLAC for audio master (lossless)
- Video output is incidental — audio master is the deliverable
- Export mix to `~/.rufus/recordings/YYYY-MM-DD-podcast-raw.wav`

---

## Audio Routing & Mixing

### Input Sources

| Source | Device | Level | Filters |
|--------|--------|-------|---------|
| Primary mic | USB/XLR input on flowbie | 0 dB base | Noise suppression, gate, compressor |
| Secondary mic | fourty4 internal or USB | 0 dB base | Same filter chain |
| System audio | `Monitor and Output` mode | -20 dB | None |
| Music / ambient | VLC Virtual Audio Cable or file source | -30 dB | None |

### Filter Chain (Primary Mic)

Applied in order:
1. **Noise Suppression** — RNNoise (preferred) or Speex at 20 dB
2. **Gate** — Close: -50 dBFS, Open: -35 dBFS, Attack: 25ms, Hold: 200ms, Release: 150ms
3. **Compressor** — Threshold: -18 dBFS, Ratio: 4:1, Attack: 6ms, Release: 60ms, Output gain: +3 dB
4. **Limiter** — Threshold: -3 dBFS (safety only)

### Output Routing

| Track | Contents | Destination |
|-------|---------|-------------|
| Track 1 | Mic + system (final mix) | Stream output + recording |
| Track 2 | Mic only (isolated) | Recording only — for post re-mix |
| Track 3 | System only (isolated) | Recording only — for post re-mix |

Always record multi-track. Even if post-production isn't planned, isolated tracks allow correction later.

---

## Source Configuration

### Camera / Webcam

- **Resolution:** 1920x1080 @ 30fps (set on device, not OBS crop)
- **Format:** MJPEG preferred over YUY2 for USB bandwidth
- **Color space:** Rec. 709
- **Exposure:** Manual preferred — auto exposure flickers on screen cut

### Display Capture

- **Method:** Xcomposite (Linux/X11) or `obs-xcomposite-capture`
- **Crop:** Remove title bar if content is terminal-only
- **Scaling:** Match canvas resolution before downscale — no double-downscale

### Audio Devices

- **Sample rate:** 48000 Hz (OBS default and streaming standard)
- **Channels:** Stereo for music/stream; mono for voice-only sources (then expand to stereo in OBS)
- **Latency compensation:** Use OBS audio sync offset to align mic with video if using hardware compression (typical: +150ms to +200ms for USB mics)

### Remote Feeds (NDI)

- **Protocol:** NDI v5 via obs-ndi plugin
- **Latency:** Expect 100–200ms on local LAN — acceptable for multi-source post-production; not suitable for live cut if < 200ms sync required
- **Fallback:** If NDI drops, switch to Screen Recording scene on that source machine and sync in post

---

## Multi-Source Orchestration

### Clock Synchronization

For multi-machine recordings that will be synced in post:

```bash
# On all machines — sync NTP before recording
sudo timedatectl set-ntp true
timedatectl status   # verify "NTP synchronized: yes"

# Confirm clocks are within 100ms of each other
ssh flowbie 'date +%s%N'
ssh fourty4 'date +%s%N'
date +%s%N
```

If clocks are not synchronized, use a clap-sync method: play a sharp audio transient (hand clap or tone burst) visible/audible to all recording devices at session start. Use this as the manual sync point in post.

### Remote OBS Control

OBS WebSocket server must be enabled on each machine:
1. OBS → Tools → WebSocket Server Settings
2. Enable WebSocket server
3. Port: 4455 (default)
4. Enable authentication, store credentials in `~/.rufus/.credentials`

```bash
# Test WebSocket connection from thinker
# Uses obs-cmd (install: cargo install obs-cmd)
obs-cmd --websocket obsws://flowbie:4455/your-password scene switch "Screen Recording"
obs-cmd --websocket obsws://flowbie:4455/your-password recording start
obs-cmd --websocket obsws://flowbie:4455/your-password recording stop
```

### Unified Scene Switching

For coordinated multi-machine recording sessions:

```bash
# Record start on both machines simultaneously
ssh flowbie 'obs-cmd --websocket obsws://localhost:4455/PASSWORD recording start' &
ssh fourty4 'obs-cmd --websocket obsws://localhost:4455/PASSWORD recording start' &
wait
echo "Recording started on both machines at $(date)"
```

See `commands/record/start/command.sh` for the production-ready version.

### Monitoring & Failover

During a session, monitor:

```bash
# Check OBS stats via WebSocket (dropped frames, encoding load)
obs-cmd --websocket obsws://flowbie:4455/PASSWORD stats
```

Failover rules:
- If flowbie drops > 1% frames for > 30 seconds: switch to fourty4 as primary, continue session
- If fourty4 NDI feed drops: remove source from scene, switch to single-source layout
- If network to remote source drops: record locally on each machine independently, sync in post

---

## Encoder Settings

### Local Recording (High Quality)

| Setting | Value |
|---------|-------|
| Encoder | x264 or NVENC (hardware if available) |
| Rate control | CRF / CQP |
| CRF value | 18 (high quality, larger file) |
| Keyframe interval | 2 seconds |
| CPU preset (x264) | veryfast (balance quality vs CPU load) |
| Audio | AAC 320 kbps (or separate WAV track) |
| Container | MKV (safe from crash corruption) |

After recording, remux from MKV to MP4:
```bash
ffmpeg -i raw.mkv -c copy output.mp4
```

### Streaming (YouTube / Twitch)

| Setting | Value |
|---------|-------|
| Encoder | NVENC (GPU) or x264 |
| Rate control | CBR |
| Bitrate | 6000 kbps (1080p60) / 4000 kbps (1080p30) |
| Keyframe interval | 2 seconds |
| Audio | AAC 160 kbps |
| Resolution | 1920x1080 |
| FPS | 60 (30 acceptable if GPU limited) |

---

## Scene File Management

OBS scene collections are stored at:
- Linux (flowbie): `~/.config/obs-studio/basic/scenes/`
- macOS (fourty4): `~/Library/Application Support/obs-studio/basic/scenes/`

Version control workflow:
```bash
# Export scene collection from OBS → File → Scene Collection → Export
# Copy to this repo for versioning
cp ~/.config/obs-studio/basic/scenes/rufus-production.json \
   ~/.rufus/documentation/obs-scenes/rufus-production.json
cd ~/.rufus && git add documentation/obs-scenes/ && git commit -m "obs: update scene collection"
```

**Scene collection file location in this repo:** `documentation/obs-scenes/` (directory to be created when first scene collection is exported from production OBS install).

---

## Troubleshooting

See `documentation/troubleshooting/` for issue-specific guides.

**Common issues:**

| Issue | Diagnosis | Fix |
|-------|-----------|-----|
| Dropped frames (encoding) | CPU overloaded | Switch to NVENC, reduce canvas FPS, lower CRF |
| Dropped frames (network) | Bandwidth insufficient | Lower stream bitrate, check ethernet vs WiFi |
| Audio desync | Hardware compression adding latency | Add sync offset in OBS audio settings |
| Black screen (display capture) | X11 permission or compositor conflict | Run OBS as same user as display, check `DISPLAY=:0` |
| NDI feed missing | ndi-runtime not running on source | Start ndi-runtime service on source machine |

---

## Status

- [x] Scene templates defined
- [x] Audio routing specified
- [x] Encoder settings documented
- [x] Multi-source orchestration procedure
- [x] Remote OBS WebSocket control
- [ ] Scene collection XML/JSON files committed (pending first flowbie OBS session)
- [ ] NVENC encoder confirmed available on flowbie
- [ ] NDI plugin installed and tested on flowbie ↔ fourty4
