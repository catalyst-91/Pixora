<div align="center">

# PIXORA

### Real-time video, LED mapping and show control

**by Booth Productions**

![Version](https://img.shields.io/badge/version-1.6.0-ff2d95)
![Platforms](https://img.shields.io/badge/platforms-Windows%20%7C%20macOS%20%7C%20Linux-6c5ce7)
![Build](https://github.com/catalyst-91/Pixora/actions/workflows/build-desktop.yml/badge.svg)
![License](https://img.shields.io/badge/license-proprietary-lightgrey)

[**Download**](https://github.com/catalyst-91/Pixora/releases/latest) · [Features](#features) · [Recording](#local-recording) · [Getting started](#getting-started) · [Show control](#show-control--integration) · [Building](#building-from-source)

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
| **Windows 10 / 11** (x64) | `PIXORA-Setup-1.6.0.exe` (installer) or `PIXORA-1.6.0-portable.exe` |
| **macOS** Apple Silicon (M1–M4) | `PIXORA-1.6.0-mac-arm64.dmg` |
| **macOS** Intel | `PIXORA-1.6.0-mac-x64.dmg` |
| **Linux** (x64) | `PIXORA-1.6.0-linux-x86_64.AppImage` |

Get the latest installers from **[Releases](https://github.com/catalyst-91/Pixora/releases/latest)**.

<details>
<summary><b>First launch notes (unsigned builds)</b></summary>

- **macOS:** open the DMG and drag PIXORA to Applications, then double-click it. The first time, macOS says it can't verify the developer: click **Done**, open **System Settings ▸ Privacy & Security**, scroll down and click **Open Anyway** next to PIXORA. This is only needed once. (PIXORA is ad-hoc signed; a paid Apple Developer ID removes this step.)
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
- Titles, a logo animator, scoreboard templates and live **data feeds** (`{{feed.key}}`) from JSON, CSV, Google Sheets, HTTP push and OSC, with a live values editor and rows that cycle or list (`{{row.Name}}`)
- **Show templates** for weddings, conferences, sports, DJ nights, corporate events and theatre
- **Timeline mode**: clips with fade-ins and fade-outs, plus OSC, DMX, cue and device events, locked to timecode
- **Live captions**: speech-to-text in Chrome or Edge, or from any captioner over HTTP / OSC, with a second-language translation and TXT / SRT transcripts
- Web pages as sources: a proxy for sites that block embedding, plus zoom, auto-scroll, transparency, refresh and URL rotation

### LED and projection mapping
- LED panel mapping with a processor capacity check and a built-in **test-pattern generator**
- Per-screen routing, calibration and day/night brightness
- **Projector tools**: corner pin, **mesh warp** (up to 16×16, smoothed) for curved screens, soft-edge blending, **black-level compensation**, feathered **masks** and alignment test patterns
- **Camera auto-alignment**: point a webcam at the screen, and PIXORA works out every projector's corner pin, edge blends, brightness match and black level
- **PJLink** projector control: power, input, shutter, freeze, lamp hours and error alerts
- **Stage 3D** preview, with the **MVR** scene's trusses, set pieces and fixtures (beams included)
- **MVR import**, so video screens from grandMA3 / Vectorworks / Capture appear in place
- **LED processor control**: Novastar (COEX, MCTRL / VX / NovaPro, H series), Megapixel HELIOS and any DMX-controlled processor (Brompton Tessera, ROE…): brightness, blackout, freeze, presets, test patterns, inputs, plus **health monitoring** (temperatures, cards, ports)
- **Processor setup pack**: a cabling sheet per screen, raster and port CSVs and step-by-step notes for NovaLCT, VMP, Tessera, HELIOS and Colorlight
- LED content templates exported as PNG / SVG / PSD / spec sheet

### NDI®
- **NDI® built in**: every output can be an NDI source, with clip audio, live receiver count and custom names
- **NDI-only outputs**: rendered off-screen, so no display is needed. Good for feeding vision mixers, OBS, vMix or recorders
- **NDI® in**: sources on the network become clips, with effects and mapping
- Extra IPs and groups for networks where discovery is blocked
- **Spout** (Windows) and **Syphon** (macOS) built into the desktop app: send any output, and use other apps' senders as sources

### Live production
- **Views** that change the layout for the job (VJ, LED, Show Operator, Production, Replay, Stream, Signage, Setup, Perform), plus custom saved views
- A **switcher** with preview / program, CUT, AUTO and a T-bar, with fade, dip, wipe, split and stinger transitions
- Four **overlay** channels (lower thirds, logo bugs, full-screen graphics), shared **timers** and a keyboard **shortcut** editor
- An **audio mixer** with per-layer faders, meters and audio-follows-video
- **Instant replay** with four angles, events, slow motion from 5% and a jog, plus **replay export** to MP4 / WebM (any angle, slow motion included)
- **Playlists** of videos and stills as one input, from a list, a folder or an .m3u / .pls file
- **Remote guests**: presenters join from a browser link (WebRTC) and become sources
- **Live streaming** to YouTube, Facebook, Twitch, Vimeo, Kick, custom RTMP and SRT at once, with Blackmagic Streaming XML import

### Devices and cameras
- **Blackmagic**: ATEM switchers (incl. camera control), HyperDeck, Videohub, Web Presenter / Streaming Encoder, cameras via REST, **DeckLink / UltraStudio** in and out
- **PTZ**: BirdDog, Panasonic (with Auto Tracking), VISCA-over-IP and NDI PTZ, with presets and an on-screen pad

### Show control and integration
- **Pioneer PRO DJ LINK** (direct, or through the PRO DJ LINK Bridge over TCNet): follow the master deck's tempo and phase, lock clips to a deck, and show track titles
- **Ableton Link**: share tempo and phase with Live, Traktor, Resolume and other Link apps
- **QForge**: QForge's PIXORA cue fires PIXORA, and PIXORA sends clip progress back so the cue can follow the clip
- **grandMA3 package**: a USB-stick package with the GDTF, a plugin and a macro for every PIXORA action (with clip thumbnails as appearances), plus a "grandMA3 command" action the other way
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
- Multi-machine **frame sync** and **render nodes**: extra machines follow the show and its clock and drive more outputs, with each node's frame rate and drift on the primary
- **Main / backup failover**: automatic or manual takeover with takeover actions (switch the ATEM, the LED processor input…), hand-back that brings the show back to the main machine, and controllers that follow
- A show-day checklist and an LED test sequence

### Recording
- Record the output exactly as the audience sees it, **with audio**, or record **audio only**, all on your own computer
- Audio from playing clips, a live input such as a FOH feed, or both
- Chosen folder (any drive), file name, auto-stop timer, and optional raw master
- Start and stop from the panel, `⌘⇧R` / `Ctrl+Shift+R`, OSC or HTTP

### Operations
- **Users and roles** (admin / operator / client / viewer) with sign-in
- Remote access through a Cloudflare tunnel
- Multi-operator presence, follow mode and layer locks
- Scheduler, sponsor rotation and **PDF show reports** (proof of play, incidents, changes)
- Audio-reactive scenes with auto BPM
- **Automatic updates** from GitHub Releases, checked against GitHub's checksum; it asks before installing and never restarts during a show
- **Crash recovery**: the server restarts itself and output windows reload, then PIXORA offers an opt-in crash report (a pre-filled GitHub issue you check before sending)

---

## Local recording

Go to **Output ▸ Local recording**, pick a format and an audio source, then press **● Record**. The capture is written to disk as it records, and ffmpeg (included in the desktop app) finishes the file on the same computer.

| Format | Video | Audio | Best for |
|---|---|---|---|
| **MP4** | H.264 | AAC | Plays everywhere: client previews, socials, phones |
| **MOV · ProRes** | ProRes 422 HQ | PCM 24-bit | Editing in Premiere, Final Cut, Resolve |
| **MOV · HAP** | HAP | PCM 16-bit | Media-server playback (PIXORA, Resolume) |
| **MKV** | H.264 | FLAC (lossless) | Archive |
| **WebM** | VP9 | Opus | Web, small files |
| **WAV** | – | PCM 24-bit 48 kHz | Sound only: lossless |
| **MP3** | – | 320 kb/s | Sound only: small files |
| **FLAC** | – | Lossless | Sound only: about half the size of WAV |

**Audio sources:** clip audio · clip audio + audio input · audio input only · none. Sound-only recordings are captured losslessly.

**Remote control:** OSC `/pixora/rec 1|0`, `/pixora/rec/start <format>`, `/pixora/rec/stop` · HTTP `/api/rec/start?format=wav&audio=input`, `/api/rec/stop`, `/api/rec/status`.

---

## Getting started

1. **Install and open PIXORA.** The engine starts automatically and the controller window opens.
2. **Add media.** Drag files in, or go to **Show ▸ Add Media Folder…** to add a folder or external drive.
3. **Set up your screens.** Set the composition resolution, then map LED panels or outputs under **Outputs**.
4. **Send to displays.** **Outputs ▸ Open Output** puts an output on any connected display in full screen.
5. **Save the show.** **File ▸ Save Show** (`⌘S` / `Ctrl+S`) writes a `.pixora` file. Double-click it later to reopen.

The full **User Manual** is in **Help ▸ User Manual**, and as a PDF with every [release](https://github.com/catalyst-91/Pixora/releases/latest) (`PIXORA-User-Manual.pdf`).

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
| NDI® | in / out | TCP **5960** and up, mDNS UDP **5353** |

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

Every push of `PIXORA-src.zip` to `main` runs the **[Build PIXORA desktop app](.github/workflows/build-desktop.yml)** workflow. It first runs the automatic tests (`node tests/run-all.js`); if any fail, nothing is built or released. Then it builds the Windows, macOS and Linux installers in parallel and publishes them as a GitHub Release. You can also start it by hand from **Actions ▸ Build PIXORA desktop app ▸ Run workflow**.

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
server-rec.js       Local recording (formats, ffmpeg finishing, API)
server-*.js         Feature modules: devices, ATEM, replay, playlists, production, guests, streaming,
                    DJ Link / TCNet, Ableton Link, QForge, grandMA3
public/             Controller, output renderer, phone remote, manual
desktop/            Electron desktop app (menus, windows, displays)
desktop/native/ndi/ PIXORA's NDI® module (C, Node-API); the NDI runtime is added at build time
companion-module/   Bitfocus Companion module
installers/         Installer build scripts and update packager
tests/              Automatic tests (node tests/run-all.js), run by every build before anything is released
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

## Licences

PIXORA is © Booth Productions; see the EULA shown by the installer (`desktop/build/EULA.txt`).

This product uses **NDI®** technology. NDI® is a registered trademark of Vizrt NDI AB. More information: [ndi.video](https://ndi.video/). The NDI runtime library is © Vizrt NDI AB. It is downloaded from NDI during the build and is never stored in this repository. The NDI header files in `desktop/native/ndi/include` are MIT-licensed by Vizrt NDI AB.

Includes FFmpeg (GPL), run as a separate program, and Electron/Chromium (open-source licences).

**Art-Net™** Designed by and Copyright Artistic Licence Holdings Ltd.

**Blackmagic Design**, ATEM, DeckLink, HyperDeck, Videohub and Web Presenter are trademarks of Blackmagic Design Pty. Ltd. Device control uses Blackmagic's published developer protocols and SDKs under their licence terms. Only the DeckLink SDK header files are included (`desktop/native/decklink/include`, redistributable under the licence printed at the top of each file); the rest of the SDK and the Desktop Video driver are not stored in this repository.

**TCNet** is an open protocol by Event Imagineering Group. PRO DJ LINK™ and Pioneer DJ are trademarks of AlphaTheta Corporation. PIXORA talks to the players directly or to Pioneer DJ's PRO DJ LINK Bridge over TCNet, and is not affiliated with or endorsed by AlphaTheta. Direct Pro DJ Link support follows the protocol research by [Deep Symmetry (beat-link)](https://github.com/Deep-Symmetry/beat-link), EPL-2.0; PIXORA's implementation is its own and contains no beat-link code.

**Ableton Link** support uses [Carabiner](https://github.com/Deep-Symmetry/carabiner) by Deep Symmetry, which includes [Ableton Link](https://github.com/Ableton/link). Both are GPL-2.0. Carabiner runs as a separate program that PIXORA talks to over a local socket, and the exact source of each build is attached to every release as `carabiner-source.tar.gz`. Ableton and Link are trademarks of Ableton AG.

**Spout** (Windows) uses the [Spout SDK](https://github.com/leadedge/Spout2) by Lynn Jarvis, BSD-2-Clause; **Syphon** (macOS) uses [Syphon.framework](https://github.com/Syphon/Syphon-Framework) by Tom Butterworth and Anton Marini, BSD-2-Clause. Both are built from source during the desktop build and shipped with their licence files.

The Novastar controller command tables (`server-ledproc-novastar.js`) come from Bitfocus Companion's [companion-module-novastar-controller](https://github.com/bitfocus/companion-module-novastar-controller), MIT License, Copyright (c) 2020 Bitfocus AS. Novastar, HELIOS (Megapixel VR) and PJLink (JBMIA) are trademarks of their owners; PIXORA uses their published control protocols and is not affiliated with them.

BirdDog, Panasonic, VISCA (Sony) and grandMA3 (MA Lighting) are trademarks of their owners and are named only to describe compatibility. The same notices appear on the desktop app's splash screen and in Help ▸ About PIXORA (`desktop/credits.js`).

---

## Support

Booth Productions provides PIXORA. For licensing, support or custom builds, contact **Booth Productions**.

<div align="center">

**© Booth Productions. All rights reserved.**

</div>
