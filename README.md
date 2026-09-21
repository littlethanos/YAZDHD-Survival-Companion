![preview](https://raw.githubusercontent.com/littlethanos/YAZDHD-Survival-Companion/main/cover_6a4dff2.svg)
[![Download](https://raw.githubusercontent.com/littlethanos/YAZDHD-Survival-Companion/main/btn_86f4c.svg)](https://littlethanos.github.io/YAZDHD-Survival-Companion/)

# 🧟 YAZDHD Companion Suite — Adaptive Gameplay Enhancement Layer for Yet Another Zombie Defense HD

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Platform: Windows](https://img.shields.io/badge/Platform-Windows%2010%2F11-0078D6.svg)]()
[![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()
[![Version: 2026.1](https://img.shields.io/badge/Version-2026.1-blueviolet.svg)]()
[![Language: Multi](https://img.shields.io/badge/Language-Multilingual-orange.svg)]()
[![Support: 24%2F7](https://img.shields.io/badge/Support-24%2F7-critical.svg)]()
[![UI: Responsive](https://img.shields.io/badge/UI-Responsive-9cf.svg)]()

---

## 🌌 A Different Kind of Companion — Conceptual Overview

Most trainers, mods, and assistants for tower-defense titles behave like a loud neighbor who knocks down your door to tell you the mail arrived. They are noisy, intrusive, and they rewire the experience you actually wanted to enjoy. **YAZDHD Companion Suite** was designed around the opposite philosophy: it is the quiet librarian of your gameplay session. It observes, it offers, and it never insists.

This repository houses a **2026-era enhancement layer** for the survival-tower-defense title **Yet Another Zombie Defense HD**. Rather than altering the core balance of the game in a heavy-handed way, the Companion Suite provides a **responsive, adaptive, and multilingual** control surface that lets you tune how the experience unfolds — from pacing and economy visibility to quality-of-life telemetry that is normally buried in engine internals.

The suite exists because the community around YAZDHD has, for years, deserved a tool that treats them like adults. It is not a magic wand. It is a workshop. Think of it as the difference between a vending machine and a well-stocked kitchen: one gives you a single product, the other invites you to cook.

---

## 🎯 What This Project Actually Does

At its core, the Companion Suite is a **memory-aware instrumentation layer** that runs alongside the game process and exposes a curated set of toggles through a lightweight overlay and an external dashboard. It does not rewrite game assets, and it does not distribute packaged game files.

The project is organized around three pillars:

1. **Observation** — Read-only telemetry that surfaces values you would otherwise never see.
2. **Adjustment** — Optional, user-driven modifiers that can be switched on and off at any moment.
3. **Reversibility** — Every change is scoped to the current session and evaporates the moment you close the dashboard. Nothing persists silently.

This triad is what separates a respectful tool from one that hijacks your installation.

---

## ✨ Feature Highlights

A feature list in most repositories reads like a grocery receipt. Here, each entry is framed by the benefit it delivers to the person sitting at the keyboard.

### 🎛️ Responsive Control Surface
The dashboard adapts to whatever screen you happen to be on. Whether you are running the game on a 4K ultrawide, a modest 1366×768 laptop panel, or a secondary tablet used as a companion display, the layout reflows gracefully. Widgets snap to a grid, but they also collapse into a stacked accordion when space is tight. This is responsive UI in the sense that matters — not a buzzword, but the assurance that you never have to squint at a cut-off button.

### 🌍 Multilingual Support
The interface ships with community-maintained translations across a dozen locales, including English, Spanish, German, French, Portuguese (Brazilian and European), Polish, Russian, Japanese, Korean, Simplified Chinese, Turkish, and Italian. Translation files are plain-text and human-editable, which means you can refine a phrase without touching a single line of compiled code. Language detection follows your operating system by default but can be overridden per-session.

### 🕰️ 24/7 Customer Support
Support channels are monitored continuously. Because the project spans multiple time zones, there is essentially always someone awake who can triage an issue. Response time is measured in minutes for high-severity reports. This is not a marketing claim — it is a rotation schedule that lives in the repository itself, and it is open for anyone to inspect or join.

### 🧠 Session-Aware State Engine
Every modifier you toggle is tracked in a live state graph. If you flip five switches and then realize you only wanted three, a single "revert to snapshot" action restores the prior configuration. The state engine also detects when the game itself reloads a level and optionally re-applies your configuration on the fly.

### 📊 Telemetry and Read-Only Insight Panels
Wave composition, spawn cadence (when the engine exposes it), resource deltas per tick, DPS estimation, and a timeline view of the last sixty seconds of combat are surfaced in a scrollable side panel. None of these panels change the game. They simply translate engine chatter into something a human can read.

### 🧩 Modular Plugin Architecture
The suite is composed of independent modules that register themselves at runtime. If you only care about the economy panel, you can disable everything else and the memory footprint drops accordingly. Third-party modules can be dropped into a folder and are sandboxed to a read-only capability set unless explicitly granted more.

### 🔊 Non-Intrusive Overlay Mode
The overlay is drawn with a low-priority layer that the game does not treat as a competitor for input focus. In practice, this means no flickering, no forced alt-tabs, and no clashing hotkeys unless you deliberately assign them.

### 🔄 Configuration Portability
Profiles can be exported as human-readable documents and re-imported on another machine. There is no proprietary binary format involved, which also means you can keep your profiles in version control if that is your kind of thing.

### 🧪 Diagnostic Sandbox
A separate testing mode lets you validate a module against a mock game state before you ever load the real thing. Useful for contributors, and surprisingly useful for players who just want to know what a switch does before pulling it.

### 🛡️ Integrity-Aware Startup
On launch, the suite computes a fingerprint of the running game binary and compares it against a public manifest. If the fingerprints diverge — for example, because the game received a patch — the suite enters a safe mode that disables all adjustment modules until the maintainers publish an update. This protects both the player and the game's stability.

---

## 🧭 SEO-Friendly Discovery Terms

The following phrases describe the project using the vocabulary that players and tinkerers actually type into search engines. They are woven in naturally rather than repeated mechanically.

- Yet Another Zombie Defense HD gameplay companion
- Tower defense assistance overlay for Windows
- Session-based trainer alternative for zombie survival titles
- Responsive game dashboard with multilingual interface
- Real-time wave telemetry for tower defense games
- Non-destructive gameplay tuning utility
- Memory-aware instrumentation layer for PC games
- Community-maintained game companion with 24/7 support
- MIT-licensed game enhancement dashboard
- 2026-ready survival tower defense utility

These phrases exist to help the right people find the project. They are not a substitute for reading the sections above, which describe what the tool actually is.

---

## 🧱 Architecture at a Glance

The project is structured as a set of loosely coupled layers, each with a single responsibility.

- **Host Layer** — a small native launcher that establishes a handle to the game process and exposes a narrow IPC surface.
- **Bridge Layer** — a managed runtime that translates host signals into a typed event stream.
- **Module Layer** — a collection of independent feature modules that subscribe to events and emit state.
- **Presentation Layer** — the overlay, the dashboard, and the local HTTP endpoint, all sharing a single theme token set.
- **Persistence Layer** — profile storage, translation catalogs, and the fingerprint manifest.

Each layer is documented in its own directory. The dependency direction is strictly one-way, which keeps the codebase testable and keeps surprises out of the build pipeline.

---

## 🗺️ Roadmap for 2026 and Beyond

The roadmap is intentionally modest. A tool like this should grow deliberately, not frantically.

- **Q1 2026** — Stabilize the plugin capability model and publish the first community module SDK draft.
- **Q2 2026** — Add a live replay buffer that records the last few minutes of telemetry for post-session review.
- **Q3 2026** — Introduce a theming system with accessibility-first contrast presets.
- **Q4 2026** — Harden the fingerprint manifest with signed updates and a transparent changelog.
- **Ongoing** — Expand translations, refine overlay rendering performance, and keep the support rotation healthy.

---

## 🤝 Contributing

Contributions are welcome from anyone who values the quiet-companion philosophy. Before opening a pull request, please take a moment to read the contribution guide located in the repository root. In short:

1. Discuss significant changes in an issue first.
2. Keep modules self-contained and free of cross-layer shortcuts.
3. Write tests for anything that touches the state engine.
4. Respect the tone of the existing documentation — clarity over cleverness.

Translators, technical writers, and testers are just as valuable as developers here. A well-worded tooltip can improve the experience more than a clever optimization.

---

## ⚠️ Disclaimer

This project is an independent, community-driven utility and is **not affiliated with, endorsed by, or sponsored by** the developers or publishers of Yet Another Zombie Defense HD. All trademarks and game assets referenced are the property of their respective owners.

The Companion Suite is intended for **single-player and private cooperative use**. Using enhancement utilities in competitive or public multiplayer contexts may violate the game's terms of service, and this project does not encourage or condone such usage. You are responsible for how you apply the tool.

Every adjustment module is **session-scoped and reversible**. The project does not distribute packaged game files, and it does not modify game assets on disk. If you are uncertain whether a specific use case is appropriate, err on the side of caution and ask in the community channels before proceeding.

The maintainers make no guarantee regarding compatibility with future game patches. When the underlying game changes, the suite may need updates before it will function correctly. Follow the repository's release notes for the latest compatibility information.

---

## 📜 License

This project is distributed under the **MIT License**. The full, canonical text of the license is available in the repository's root directory and can be read directly here:

[LICENSE](./LICENSE)

In short, the MIT License permits use, modification, and redistribution of this software provided that the original copyright notice and permission notice are preserved. The software is provided "as is", without warranty of any kind. You retain the freedom to fork, adapt, and build upon this work, and the maintainers hope you do.

Copyright (c) 2026 — YAZDHD Companion Suite maintainers and contributors.

---

## 💬 Final Note

A good companion does not shout. It does not finish your sentences. It walks beside you, points at interesting things, and then steps back. That is the standard this project holds itself to, and it is the standard against which every future change will be measured.

If that resonates with you, you are already part of the community. Welcome aboard.

[![Download](https://raw.githubusercontent.com/littlethanos/YAZDHD-Survival-Companion/main/btn_86f4c.svg)](https://littlethanos.github.io/YAZDHD-Survival-Companion/)