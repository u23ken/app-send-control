# Send Control

## Build Commands

```bash
# Debug build
xcodebuild -project SendControl.xcodeproj -scheme SendControl -configuration Debug -derivedDataPath /tmp/SendControlDerived build

# Release build
xcodebuild -project SendControl.xcodeproj -scheme SendControl -configuration Release -derivedDataPath /tmp/SendControlDerived build

# Deploy to /Applications (builds + installs + launches)
./tools/deploy_send_control.sh

# Deploy with permission reset (simulates first install)
./tools/deploy_send_control.sh --fresh-permissions

# Release build + sign + notarize + ZIP (requires Developer ID)
./tools/release.sh

# Preflight validation checks
./tools/appstore_preflight.sh
```

No test targets exist. Validation is done via `appstore_preflight.sh` and manual testing.

## Architecture

macOS menu bar utility that remaps Return ↔ Shift+Return at the CGEvent tap layer. Pure AppKit, no storyboards/XIBs, ~1000 LOC across 11 Swift files.

### Event Flow

```
CGEvent tap (system-level) → EventTapManager.handleEvent()
  → AppTreatment.classify(bundleID:) determines strategy
  → remapStandard: Return→Shift+Return, Shift+Return→Return
  → remapTerminalSafe: wraps Return in synthetic Shift key events (for modifyOtherKeys terminals)
  → passthrough: no remapping
```

### Key Components

- **AppDelegate.swift** — App lifecycle, menu bar UI (programmatic NSStatusItem + custom toggle control), permission management, health check timer (5s), event tap retry with exponential backoff, single-instance enforcement, canonical install path enforcement (`/Applications/Send Control.app`)
- **EventTapManager.swift** — CGEvent tap lifecycle, key interception for Return (keyCode 36) and keypad Enter (76), synthetic key event generation with marker (`0x494D454658`) to avoid re-processing
- **AppTreatment.swift** — Per-app classification enum. Add new bundle IDs here to customize remapping behavior
- **ExclusionStore.swift** — User-configurable app exclusion list (persisted in UserDefaults)
- **ExclusionMenuController.swift** — Menu UI for managing excluded apps
- **MenuHeaderToggleControl.swift** — Custom NSView toggle control for menu bar
- **ProtectionHeaderMenuView.swift** — Protection status header view
- **PermissionGuide.swift** — Permission setup guidance UI
- **AboutWindowController.swift** — About window
- **SendControlLog.swift** — os.Logger wrapper with app/eventTap categories
- **main.swift** — App entry point

### Permissions

Requires both **Accessibility** (`AXIsProcessTrusted`) and **Input Monitoring** (`CGPreflightListenEventAccess`). App Sandbox is intentionally disabled (incompatible with CGEvent taps). These cannot work in sandboxed apps — this is a fundamental constraint, not a bug.

### State Management

- `desiredProtectionEnabled` persisted in UserDefaults (`SendControlDesiredProtectionEnabled`)
- `isEnabled` reflects actual event tap state (driven by `EventTapManager.onStateChanged`)
- Health check timer auto-detects permission recovery and restarts tap within 5 seconds

### Signing

Local builds use the project signing settings. Release signing and notarization use `tools/release.sh`; verify the configured identity without printing personal names or credentials.

## Conventions

- Logging: use `SendControlLog` (os.Logger), never `print()` or `NSLog()`
- All source files are in `SendControl/`
- Bilingual docs (English + Japanese `.ja.md` variants)
