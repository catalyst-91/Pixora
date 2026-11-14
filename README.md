<div align="center">

# PIXORA

### Real-time video, LED mapping and show control

**by Booth Productions**

![Version](https://img.shields.io/badge/version-1.2.0-ff2d95)
![Platforms](https://img.shields.io/badge/platforms-Windows%20%7C%20macOS%20%7C%20Linux-6c5ce7)
![Build](https://github.com/catalyst-91/Pixora/actions/workflows/build-desktop.yml/badge.svg)
![License](https://img.shields.io/badge/license-proprietary-lightgrey)

[**Download**](https://github.com/catalyst-91/Pixora/releases/latest) · [Features](#features) · [Getting started](#getting-started) · [Show control](#show-control--integration) · [Building](#building-from-source)

</div>

---

## Overview

PIXORA is a professional media server and VJ engine for live events. It plays video, mixes it and maps it onto LED walls, projectors and displays. It covers everything from a single screen at a corporate event to a multi-surface festival stage.

It runs as a native desktop app on Windows, macOS and Linux. All decoding, compositing and effects run on your own computer's GPU. No cloud account or internet connection is needed. Lighting consoles, MIDI controllers, Companion / Stream Deck and phones can all control it over your local network.

> **Built for show day.** PIXORA includes show lock, automatic fallback clips, output health monitoring, content preflight and proof-of-play reporting, so the screens keep running whatever happens.

---

## Download

| Platform | Installer |
|---|---|
| **Windows 10 / 11** (x64) | `PIXORA-Setup-1.2.0.exe` (installer) or `PIXORA-1.2.0-portable.exe` |
| **macOS** Apple Silicon (M1–M4) | `PIXORA-1.2.0-mac-arm64.dmg` |
| **macOS** Intel | `PIXORA-1.2.0-mac-x64.dmg` |
| **Linux** (x64) | `PIXORA-1.2.0-linux-x86_64.AppImage` |

Get the latest installers from **[Releases](https://github.com/catalyst-91/Pixora/releases/latest)**.

<details>
<summary><b>First launch notes (unsigned builds)</b></summary>

- **macOS:** right-click **PIXORA.app** ▸ **Open** ▸ **Open**. This is only needed the first time.
- **Windows:** if SmartScreen appears, click **More info** ▸ **Run anyway**.
- **Linux:** `chmod +x PIXORA-*.AppImage`, then run it.

</details>

---

## Features

### Playback and compositing
- Composition at any resolution, with layers, blend modes, opacity and transitions
- A media library that reads local folders **and external drives**, with thumbnails and search
- **HAP, HAP Alpha and HAP Q** playback with GPU texture upload, plus H.264 / HEVC / VP9 / ProRes (converted by ffmpeg)
- Generators, GLSL shaders, effects chains and a RAM frame cache for smooth reverse and scrubbing
- Titles, a logo animator, scoreboard templates and live **data feeds** (`{{feed.key}}`)
- Web pages as sources: a proxy for sites that block embedding, plus zoom, auto-scroll, transparency, refresh and URL rotation

### LED and projection mapping
- LED panel mapping with a processor capacity check and a built-in **test-pattern generator**
- Per-screen routing, calibration and day/night brightness
- Projection mapping with a **Stage 3D** preview
- **MVR import**, so video screens from grandMA3 / Vectorworks / Capture appear in place
- LED content templates exported as PNG / SVG / PSD / spec sheet

### Show control and integration
- **DMX** over Art-Net and sACN (in and out), plus pixel mapping
- **CITP / MSEX**: consoles see clip thumbnails and live layer status
- **Timecode**: Art-Net timecode chase and generate, a timeline with automation, and cues
- **MIDI**: ready-made mappings for APC Mini mk2 and Launchpad Mini mk3 / X / Pro mk3, with pads coloured by clip type
- **OSC** in and out, an HTTP API, and a **Bitfocus Companion** module
- **GDTF export**, so PIXORA can be patched as a fixture on a lighting console
- **Phone remote** for running the show from the floor

### Show-day reliability
- **Show lock**: the setup is frozen while playback stays live
- **Safe loop**: a fallback clip cuts in if a clip fails, playback stalls or the GPU resets
- Live health cards for every output (fps, dropped frames, errors) and a diagnostics monitor
- **Content preflight**: checks resolution, aspect, fps, codec and bitrate, with one-click optimise and relink
- Multi-machine **frame sync**, plus a backup / failover server
- A show-day checklist and an LED test sequence

### Operations
- **Users and roles** (admin / operator / client / viewer) with sign-in
- Remote access through a Cloudflare tunnel
- Multi-operator presence, follow mode and layer locks
- Scheduler, sponsor rotation and **PDF show reports** (proof of play, incidents, changes)
- Output recording, audio-reactive scenes with auto BPM
- In-app updates, verified with SHA-256 and backed up automatically

---

## Getting started

1. **Install and open PIXORA.** The engine starts automatically and the controller window opens.
2. **Add media.** Drag files in, or go to **Show ▸ Add Media Folder…** to add a folder or external drive.
3. **Set up your screens.** Set the composition resolution, then map LED panels or outputs under **Outputs**.
4. **Send to displays.** **Outputs ▸ Open Output** puts an output on any connected display in full screen.
5. **Save the show.** **File ▸ Save Show** (`⌘S` / `Ctrl+S`) writes a `.pixora` file. Double-click it later to reopen.

The full **User Manual** is in **Help ▸ User Manual**, and also in `PIXORA-User-Manual.pdf`.

### Phone remote
Open `http://<computer-ip>:8080/remote` on any phone or tablet on the same network.

---

## Show control and integration

| Protocol | Direction | Default port |
|---|---|---|
| Web UI / HTTP API / WebSocket | in | TCP **8080** |
| OSC | in / out | UDP **7000** |
| Art-Net DMX and timecode | in / out | UDP **6454** |
| sACN (E1.31) | in / out | UDP **5568** |
| CITP / MSEX | out | UDP **4809** + one TCP port |

Allow these ports through your firewall if consoles or controllers are on another machine.

---

## Server mode (headless / Docker)

PIXORA can also run as a server without the desktop app, for example on a rack machine, a Docker host or a remote render node.

| Platform | Command |
|---|---|
| **Windows** | Install Node.js 18+ and ffmpeg, then run `start.ps1` |
| **macOS / Linux** | `./start.sh` |
| **Docker** | `docker compose up -d --build` |

Then open the controller at `http://localhost:8080/` and the output at `http://localhost:8080/output`.

<details>
<summary><b>Environment variables</b></summary>

| Variable | Default | Purpose |
|---|---|---|
| `PORT` | `8080` | Web / API port |
| `OSC_PORT` | `7000` | OSC input port |
| `PIN` / `VIEW_PIN` | – | Operator / viewer PIN |
| `MEDIA_DIR` | `./media` | Main media folder |
| `MEDIA_DIRS` | – | Extra media roots (`;`-separated) |
| `DATA_DIR` | `./data` | Saves, thumbnails, settings |
| `FFMPEG_PATH` | auto | Path to ffmpeg |

</details>

---

## Building from source

Every push of `PIXORA-src.zip` to `main` runs the **[Build PIXORA desktop app](.github/workflows/build-desktop.yml)** workflow. It builds the Windows, macOS and Linux installers in parallel and publishes them as a GitHub Release. You can also start it by hand from **Actions ▸ Build PIXORA desktop app ▸ Run workflow**.

To build locally:

```bash
cd desktop
npm install
npm run dist:mac      # or dist:win / dist:linux
```

The installers are written to `desktop/dist/`. See `BUILD-DESKTOP-APP.md` for code signing and notarisation.

<details>
<summary><b>Project layout</b></summary>

```
server.js           Engine server (HTTP, WebSocket, OSC, Art-Net/sACN, CITP, ffmpeg jobs)
server-pro3.js      v1.2 modules (roles, updates, reports, preflight, sync)
public/             Controller, output renderer, phone remote, manual
desktop/            Electron desktop app (menus, windows, displays, NDI)
companion-module/   Bitfocus Companion module
installers/         Installer build scripts and update packager
tests/              Integration test harnesses
```

</details>

---

## System requirements

| | Minimum | Recommended |
|---|---|---|
| **OS** | Windows 10, macOS 12, Ubuntu 22.04 | Windows 11, macOS 14+ |
| **GPU** | WebGL 2 capable | Dedicated GPU or Apple Silicon |
| **RAM** | 8 GB | 16 GB+ |
| **Network** | Optional | Gigabit Ethernet for consoles and multi-machine sync |

---

## Support

Booth Productions provides PIXORA. For licensing, support or custom builds, contact **Booth Productions**.

<div align="center">

**© Booth Productions. All rights reserved.**

</div>
