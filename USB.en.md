# VVA Flash Agent USB companion

Use your Android phone as an agent terminal, with a USB cable and a portable Windows workspace. The companion includes Python and ADB; the PC does not need a separate Python installation.

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

## Files you keep

- `device-workspace/tasks/`: handoffs and progress.
- `device-workspace/scripts/` and `reports/`: scripts and results.
- `device-workspace/collected/`: files collected with authorization; samples are not automatically executed.
- `device-workspace/.hermes-control/`: evidence, receipts, checkpoints and backups. The historical internal directory name is retained for compatibility.
- `tools-pack-for-model/`: your editable toolbox. Full Trust makes its tools available; copying a file here does not execute it.

Stop/Clean does not delete this workspace or the phone's conversations. Before sharing the drive, make a clean distribution using the release package; a used drive may contain personal reports and evidence. Close the session before copying or manually deleting your own workspace files.

## Troubleshooting

- **No device:** unlock it, check the data cable/USB driver and accept the RSA prompt. Wireless ADB and emulators are not selected by this launcher.
- **Pairing not confirmed:** install/open the matching VVA version, then start again. Do not paste API keys or pairing tokens into an issue report.
- **Signature mismatch while updating:** stop. The preview's old debug key and the official release key are different. This package never solves that by uninstalling the app. Existing test users need a separate data-migration plan before replacing their installation.
- **Permission denied:** approve the specific feature on the phone or restart this PC session with the required permission. UAC is a Windows confirmation, not a VVA button.
- **Connection lost:** reconnect, check status and the last action receipt before continuing. Do not replay an uncertain submit/delete action.
- **Windows cannot boot:** read `OFFLINE-RECOVERY.md`. This is a Windows companion, not a bootable rescue disk or a BIOS controller.

## Redistribution edition

Official downloads contain a complete app package and a complete USB package. In the authorized redistribution edition, **the main package contains `usb-payload/` (the app is `usb-payload/VVA.apk`); the small USB package contains only Start.cmd and Stop.cmd**. Copy the *contents* of `usb-payload/` beside those two scripts, preserving subdirectories. Do not place an extra `usb-payload` directory between the scripts and `runtime/` / `scripts/`.

This is a packaging arrangement, not encryption or proof that a third-party download is safe. See `DISTRIBUTION.md` for the VVA-specific rules; all third-party licenses remain in effect.

Official repository: https://github.com/sunnyfox-qinghu/vva-flash-agent.
