# Install Send Control

Japanese INSTALL: [INSTALL.ja.md](INSTALL.ja.md)

## Requirements

- macOS 13 (Ventura) or later
- Accessibility and Input Monitoring permissions

## 1. Download And Verify

1. Download `Send-Control-v*.zip` and `SHA256SUMS.txt` from [GitHub Releases](https://github.com/u23ken/app-sendcontrol/releases).
2. Verify the ZIP checksum:

```bash
shasum -a 256 "Send-Control-v*.zip"
```

3. Compare the output with the entry in `SHA256SUMS.txt`.

## 2. Install

1. Unzip the downloaded file.
2. Move `Send Control.app` to `/Applications/`.

## 3. Open The App

1. Double-click `Send Control.app` in `/Applications/`.
2. The app is signed with Developer ID and notarized by Apple. Gatekeeper should allow it without warnings.

## 4. Grant Required Permissions

Send Control requires both permissions below:

1. `System Settings > Privacy & Security > Accessibility`
2. `System Settings > Privacy & Security > Input Monitoring`

After granting permission, relaunch the app if protection does not turn on by itself.

## 5. Confirm It Is Running

1. Look for the Send Control menu bar icon.
2. Open the menu bar item and confirm protection is ON.
3. Test Return and Shift+Return in the target app you care about.

## 6. Uninstall

1. Quit Send Control from the menu bar.
2. Delete `Send Control.app` from `/Applications/`.
3. Remove Accessibility and Input Monitoring permission entries if you no longer want them enabled. See [PRIVACY.md](PRIVACY.md).
