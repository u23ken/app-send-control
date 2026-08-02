<p align="center">
  <img src="SendControl/assets/sendcontrol-icon-macos-1024.png" width="128" height="128" alt="Send Control icon">
</p>

<h1 align="center">Send Control</h1>

<p align="center">
  Prevents accidental message sends caused by pressing Enter during Japanese IME conversion in ChatGPT, Claude, Gemini, and more on macOS. No configuration needed.
  <br><br>
  <a href="README.ja.md">日本語</a>
</p>

<p align="center">
  <a href="https://github.com/u23ken/app-sendcontrol/releases"><img src="https://img.shields.io/github/v/release/u23ken/app-sendcontrol" alt="Release"></a>
  <a href="https://github.com/u23ken/app-sendcontrol/releases"><img src="https://img.shields.io/github/downloads/u23ken/app-sendcontrol/total" alt="Downloads"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/u23ken/app-sendcontrol" alt="License"></a>
  <img src="https://img.shields.io/badge/macOS-13%2B-blue" alt="macOS 13+">
</p>

<p align="center"><img src="docs/screenshot.png" width="360" alt="Send Control menu"></p>

## The Problem

While typing Japanese in ChatGPT, Claude, or Gemini, you press Enter to confirm a conversion — and the unfinished message gets sent immediately.

Send Control eliminates this frustration. Save wasted tokens and the time spent re-doing prompts.

## How It Works

Send Control swaps the behavior of Return and Shift+Return:

- **Return** → line break (does not send)
- **Shift+Return** → send

Works with ChatGPT, Claude, Gemini, Messenger, and other apps with the same problem. To disable the swap for specific apps, add them to the exclusion list from the menu bar.

## Download

<a href="https://github.com/u23ken/app-sendcontrol/releases/latest">
  <strong>⬇ Download latest release</strong>
</a>

## Install

1. Download `Send-Control-v*.zip` from [Releases](https://github.com/u23ken/app-sendcontrol/releases)
2. Unzip and move `Send Control.app` to `/Applications/`
3. Launch and grant two permissions:
   - **Accessibility** (`System Settings > Privacy & Security > Accessibility`)
   - **Input Monitoring** (`System Settings > Privacy & Security > Input Monitoring`)

See [INSTALL.md](INSTALL.md) for detailed steps.

## Features

- Toggle ON/OFF with one click from the menu bar
- Works system-wide across all macOS apps
- Per-app exclusion list
- Permission setup guide on first launch
- Installs without Gatekeeper warnings (Developer ID signed and notarized by Apple)
- Designed for simplicity. No dependencies, minimal resource usage

## For Developers

- Intercepts Return (keyCode 36) and keypad Enter (76) via CGEvent tap (`.defaultTap`), toggling the Shift flag
- Terminal-safe mode for apps using modifyOtherKeys / kitty protocol
- ~1400 LOC, pure AppKit, no dependencies
- Apache-2.0 license

## Documents

| | English | 日本語 |
|---|---|---|
| Install | [INSTALL.md](INSTALL.md) | [INSTALL.ja.md](INSTALL.ja.md) |
| Privacy | [PRIVACY.md](PRIVACY.md) | [PRIVACY.ja.md](PRIVACY.ja.md) |
| Known Issues | [KNOWN_ISSUES.md](KNOWN_ISSUES.md) | [KNOWN_ISSUES.ja.md](KNOWN_ISSUES.ja.md) |
| Quick Start | — | [QUICKSTART_BEGINNER.ja.md](QUICKSTART_BEGINNER.ja.md) |

## License

[Apache-2.0](LICENSE)
