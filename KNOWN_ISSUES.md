# Known Issues

Japanese KNOWN_ISSUES: [KNOWN_ISSUES.ja.md](KNOWN_ISSUES.ja.md)

## Installation

- If `/Applications/Send Control.app` already exists, launching a copy from another folder redirects to the installed app.
- Only one instance with the same bundle identifier can run at a time. A second copy exits automatically.

## Permissions

- Accessibility and Input Monitoring are both required. If either permission is missing, the event tap remains OFF.
- After changing permission settings, you may need to quit and relaunch the app before protection becomes active.

## App Compatibility

- Behavior may differ across target apps depending on how each app handles Return and Shift+Return.
- Terminal apps with modifyOtherKeys or kitty protocol may require terminal-safe remapping (handled automatically via AppTreatment).

## Not Supported

- This app cannot be distributed via the Mac App Store. CGEvent tap requires Accessibility permission, which is unavailable inside App Sandbox.
- There is no auto-updater. Check [GitHub Releases](https://github.com/u23ken/app-sendcontrol/releases) for updates.
