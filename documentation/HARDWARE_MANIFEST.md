---
title: Hardware Manifest — Recording Equipment Inventory
owner: rufus
status: active
updated: 2026-04-05
closes-issue: https://github.com/koad/rufus/issues/2
---

# Hardware Manifest — Recording Equipment Inventory

This document inventories all hardware available to Rufus for recording, streaming, and content production. Last verified: 2026-04-05.

---

## Machine Inventory

### thinker — Primary Ops Node

| Field | Value |
|-------|-------|
| Role | Primary coordination, ops, Claude Code sessions |
| OS | Linux (Debian-based) |
| Hostname | thinker |
| Network | Ethernet (primary), trusted LAN |
| Recording capability | Screen recording via asciinema / ffmpeg; no dedicated OBS instance |
| GPU | Unknown — check `lspci | grep -i vga` |
| Audio | Internal or USB — confirm before recording sessions |
| Storage | Primary home disk — recordings to `~/.rufus/recordings/` |
| SSH access | Direct (primary machine) |
| Operator | koad, Juno |

**Recording role:** Terminal capture for entity demos (asciinema). Script coordination. Not a studio machine — does not run OBS.

---

### flowbie — 24/7 Studio Node

| Field | Value |
|-------|-------|
| Role | Always-on studio, OBS source, content production |
| OS | Linux (X11 desktop) |
| Hostname | flowbie |
| Network | Ethernet (confirmed) |
| Recording capability | OBS Studio (primary), webcam, screen capture, microphone |
| X11 Display | `:0` (confirm with `echo $DISPLAY` on flowbie) |
| GPU | TBD — run `lspci | grep -i vga` on flowbie to confirm NVENC availability |
| Audio | USB microphone (confirm device name with `arecord -l`) |
| Storage | Local disk — recordings to flowbie home, retrieved via SCP/rsync to thinker post-session |
| SSH access | `ssh flowbie` (via ~/.koad-io/bin SSH wrapper) |
| OBS WebSocket | Port 4455 (to be configured) |
| Operator | Rufus (remote), koad (physical access) |

**Recording role:** Primary studio. OBS instance runs here for all video production. 24/7 availability means sessions can be scheduled without worrying about wake cycles.

**Commands to verify status:**
```bash
ssh flowbie 'obs --version 2>/dev/null || echo "OBS not installed"'
ssh flowbie 'arecord -l'
ssh flowbie 'lspci | grep -i vga'
ssh flowbie 'df -h /home'
```

---

### fourty4 — Mac Mini / Inference Node

| Field | Value |
|-------|-------|
| Role | Local inference (ollama), OpenClaw messaging bridge, entity session recording |
| OS | macOS |
| Hostname | fourty4 |
| Network | Ethernet (confirmed) |
| Recording capability | QuickTime or OBS for macOS, terminal capture via asciinema |
| GPU | Apple Silicon or Intel — confirm with `system_profiler SPDisplaysDataType` |
| Audio | Internal mic or USB (TBD) |
| Storage | SSD — recordings to ~/rufus-recordings/ or confirm path |
| SSH access | `ssh fourty4` (via ~/.koad-io/bin SSH wrapper) |
| Inference | ollama — models include deepseek-r1 (confirm with `ollama list`) |
| Additional | OpenClaw (messaging bridge), GitClaw (GitHub event watcher) |
| Operator | Rufus (remote for recording), autonomous entity sessions |

**Recording role:** Entity session recordings when inference is on-device (e.g., "Sibyl Does Research" sessions using local ollama). Recording and inference on the same machine eliminates network latency artifacts.

**Commands to verify status:**
```bash
ssh fourty4 'ollama list'
ssh fourty4 'ollama ps'
ssh fourty4 'df -h ~'
ssh fourty4 'obs --version 2>/dev/null || echo "OBS not installed"'
```

---

## Audio Equipment

### Current Inventory

| Device | Location | Type | Interface | Status |
|--------|---------|------|-----------|--------|
| TBD — USB mic | flowbie | Condenser (assumed) | USB | Assumed connected — verify with `arecord -l` on flowbie |
| Laptop internal mic | thinker | Built-in | Internal | Low quality — emergency fallback only |
| fourty4 internal | fourty4 | Built-in (macOS) | Internal | Acceptable for entity session audio |

**To document:** When on flowbie, run `arecord -l` and update this table with the actual device name, model, and USB ID.

### Audio Capture Standards

- **Preferred:** External USB condenser microphone on flowbie
- **Acceptable:** External USB on fourty4
- **Fallback:** Internal mic (mark recording as "low quality audio" in metadata)
- **Sample rate:** 48000 Hz (all cases)
- **Format for master:** WAV (uncompressed) or FLAC — not MP3 or AAC for original capture

---

## Video Equipment

### Current Inventory

| Device | Location | Type | Resolution | Interface | Status |
|--------|---------|------|-----------|-----------|--------|
| TBD — webcam | flowbie | USB webcam (assumed) | TBD | USB | Verify with `lsusb` on flowbie |
| Screen capture | All machines | Software (OBS / asciinema) | Native display res | N/A | Active |
| Terminal capture | thinker / fourty4 | asciinema | Text-based | N/A | Active |

**To document:** Verify webcam model on flowbie with `lsusb` and `v4l2-ctl --list-devices`.

### Capture Software

| Tool | Platform | Use case | Status |
|------|---------|---------|--------|
| OBS Studio | flowbie, fourty4 | Full video production | To be confirmed installed |
| asciinema | thinker, fourty4 | Terminal session capture | Active — confirmed working |
| ffmpeg | All | Format conversion, remux | Required — install if missing |
| QuickTime | fourty4 | macOS screen/audio capture | Available by default |

---

## Network Topology

```
[thinker] ─── Ethernet ─── [LAN switch/router]
[flowbie] ─── Ethernet ─── [LAN switch/router]
[fourty4] ─── Ethernet ─── [LAN switch/router]
```

All three machines are on the same physical LAN. SSH connections are available machine-to-machine via `~/.koad-io/bin` SSH wrappers.

**NDI (for OBS multi-source):** NDI requires all machines on the same subnet (or multicast-enabled routing). On this LAN, NDI between flowbie and fourty4 should work without additional configuration.

**Bandwidth:**
- Gigabit Ethernet assumed (verify with `ethtool <iface>`)
- NDI requires approximately 100–200 Mbps per source — well within gigabit capacity
- USB mic/cam: no network bandwidth consideration

---

## Storage Architecture

| Machine | Recording Storage Path | Estimated Available | Notes |
|---------|----------------------|---------------------|-------|
| thinker | `~/.rufus/recordings/` | TBD | Check with `df -h ~/.rufus` |
| flowbie | `~/recordings/` (remote) | TBD | SSH-retrieved to thinker post-session |
| fourty4 | `~/rufus-recordings/` (remote) | TBD | SSH-retrieved to thinker post-session |

**Master archive:** All final recordings land on thinker under `~/.rufus/recordings/YYYY-MM-DD-<slug>/`.

**Post-session retrieval command:**
```bash
# After flowbie session
rsync -avz flowbie:~/recordings/ ~/.rufus/recordings/raw/flowbie/

# After fourty4 session
rsync -avz fourty4:~/rufus-recordings/ ~/.rufus/recordings/raw/fourty4/
```

---

## Operational Status

Run this block before any recording session to check all hardware:

```bash
#!/usr/bin/env bash
echo "=== Hardware Status Check — $(date) ==="

echo ""
echo "--- thinker (local) ---"
df -h ~/.rufus/recordings 2>/dev/null || echo "recordings dir not found"
arecord -l 2>&1 | grep -i card || echo "no audio capture devices listed"

echo ""
echo "--- flowbie ---"
ssh -o ConnectTimeout=5 flowbie 'echo "online: $(hostname)" && df -h ~/recordings 2>/dev/null || mkdir -p ~/recordings && df -h ~/recordings && arecord -l 2>&1 | grep -i card' 2>/dev/null || echo "flowbie: unreachable"

echo ""
echo "--- fourty4 ---"
ssh -o ConnectTimeout=5 fourty4 'echo "online: $(hostname)" && df -h ~/rufus-recordings 2>/dev/null || mkdir -p ~/rufus-recordings && df -h ~/rufus-recordings' 2>/dev/null || echo "fourty4: unreachable"

echo ""
echo "=== Status check complete ==="
```

---

## Maintenance Log

| Date | Machine | Action | Notes |
|------|---------|--------|-------|
| 2026-04-05 | All | Initial manifest drafted | Physical survey pending |

---

## Pending Verification

These items need physical confirmation on the target hardware:

- [ ] flowbie: OBS version (`obs --version`)
- [ ] flowbie: Webcam model and resolution (`v4l2-ctl --list-devices`)
- [ ] flowbie: Microphone model (`arecord -l`)
- [ ] flowbie: GPU / NVENC availability (`lspci | grep -i vga`)
- [ ] flowbie: Available disk space (`df -h ~`)
- [ ] fourty4: OBS installed (`obs --version` or check Applications)
- [ ] fourty4: ollama models (`ollama list`)
- [ ] fourty4: Available disk space (`df -h ~`)
- [ ] All machines: NTP synchronized (`timedatectl status`)
- [ ] LAN: NDI multicast working between flowbie and fourty4
