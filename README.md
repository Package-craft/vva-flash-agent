# VVA

[中文说明](README.zh-CN.md)

**Release preparation — this repository and all release drafts remain private.**

VVA brings a phone, a USB cable and a portable workspace together. The Android app
runs the agent; the Windows companion provides local desktop and background tools.
It builds on Hermes, with VVA-specific Android, USB and workflow capabilities.

The app is free to use. You supply your own model provider and API key; provider
usage may be billed separately. The development source is not being published at
this stage. The repository contains distribution documentation and release drafts.

## What to download when a release is ready

- The signed VVA APK for Android 11+.
- The complete Windows 10/11 x64 USB package in Chinese or English.
- Authorized redistributors use the separately prepared main/payload and two-script
  USB packages; see [distribution layout](DISTRIBUTION.md).

No VVA account, wireless connection or cloud synchronization is required. Model API
requests still need an internet connection. This preview does not promise full
Windows/Android compatibility across every device.

## Permissions and setup

## Requirements

- Windows 10/11 **x64**; Windows PowerShell 5.1.
- Android 11 or newer, the matching VVA app, and a USB **data** cable.
- A model provider and API key configured by the user in VVA. No shared API key is included. Model API usage may cost money even though VVA is free.
- Internet on the phone for model requests. The phone-to-PC channel uses USB and a loopback listener, not a cloud account or wireless remote-desktop service.

## Permissions: enable only what you use

| Feature | Required action |
|---|---|
| Install the APK | Allow installation from the browser/file manager used to open it, when Android asks. |
| Connect this phone to a PC | In Android Developer options, enable **USB debugging**. Unlock the phone and accept the computer's RSA authorization prompt. Use a data-capable cable; a manufacturer USB driver may be needed on Windows. |
| Control the PC | In Start.cmd, approve the session, then desktop access and/or command execution as needed. These are separate choices. |
| Control the phone's own screen | Enable VVA's Accessibility service. This is not required merely to control a PC through USB. Android may require Allow restricted settings for a sideloaded app. |
| Floating chat | Allow display over other apps. |
| Camera questions | Allow the camera when opening that feature. |
| Long-running tasks | Allow notifications so task status and Stop remain visible. If the phone vendor suspends VVA, allow background activity for VVA; no blanket battery/security changes are required. |
| Exact scheduled tasks | Allow exact alarms when Android requests it for a schedule that needs them. |
| Import documents/images | Select the specific files in the system picker; all-files access is not required. |

Root, an unlocked bootloader and Windows administrator access are **not required** for ordinary operation. Full Trust and Approve for me in VVA do not bypass Android permissions or Windows UAC.

## Start and stop

1. Extract the **complete** official USB package to a writable folder or USB drive. Do not run it inside the ZIP viewer.
2. Install the matching APK on the phone. If included, `Update-Phone.cmd` uses `adb install -r`; it does not uninstall the app or clear its data.
3. Connect and unlock the phone; accept USB debugging authorization.
4. Run **Start.cmd**, enter `START`, choose the desktop/command permissions, and select the intended USB phone even if only one is connected.
5. Keep the status window open while working. Press **S**, or run **Stop.cmd**, to end this package's session. `Clean.cmd` uses the same cleanup path after an unexpected window close.

For an explicitly requested administrator task, use `Start-Administrator.cmd` and personally confirm Windows UAC once. Ordinary startup keeps ordinary privileges. No Windows service or startup entry is installed.

If the default port is occupied, use `Start.cmd -Port 18746` and `Stop.cmd -Port 18746`. Do not stop unrelated processes to free it.

The one-time USB credential is imported through VVA's app-owned directory, encrypted in Android Keystore-backed storage and removed from the import directory. Release builds do not require `run-as` or a debuggable APK.


## Release status

Release signing, bilingual package reconstruction and isolated real-device pairing
have passed. The device test used a separately named non-debuggable build signed
with the release key; it did not replace the existing debug installation. Migration
of that old installation is still a separate step. This repository remains private.

See [signing](SIGNING.md), [privacy](PRIVACY.md) and [third-party notices](THIRD_PARTY_NOTICES.md).
