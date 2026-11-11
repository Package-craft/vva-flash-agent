# VVA Agent — On your phone. Within reach of your PC.

[简体中文](README.zh-CN.md)

> Your personal AI assistant, based on your phone and ready for USB-connected PC work.

Find information, organize files, keep track of tasks, write scripts, prepare files for rooting a device, or investigate a PC that is behaving strangely—even one showing signs of malware. Tell VVA what you want to accomplish and work through it together.

VVA runs on an Android phone. To work on a PC, plug in your USB drive, connect the phone by USB, and start the bundled companion. Within the permissions you grant, VVA can read interfaces, operate applications, handle files, and run scripts.

**A phone, a USB cable, and a USB drive: a workspace you can carry with you.**

VVA is available as a public preview. This page describes the current implementation; each Release identifies its available build and validation status.

## Why VVA?

- **No VVA account or VVA-hosted relay.** The phone-to-PC connection uses USB. Conversations, task archives, and operation records stay on your devices or in your chosen workspace. Cloud models still require internet access on the phone and receive the task content included in requests.
- **Your choice of model.** Choose a provider and supply your own API key. Working on another PC does not require setting up your model account or API credentials there.
- **Keep what you learn from a task.** Save operation cards, scripts, and task archives locally for later retrieval and reuse. Repeated work can require less trial and error, although application updates and layout changes may need fresh inspection.
- **Free to use.** Your chosen model provider may charge separately for API usage.

## What can it do?

- Read pages, find information, operate Android apps, and work with images and files you import.
- Control a Windows PC over USB: find content across windows, enter text, and adjust settings.
- Write and run scripts, analyze logs, process files in batches, and help troubleshoot software—including running diagnostic tools you authorize.
- Organize material, save progress, and schedule tasks.
- Keep results, evidence, and handoff notes in the workspace so a new conversation can retrieve them and continue saved work.

These are starting points. Bring your own tasks, and let us know what is missing or awkward to use.

While a task is running, you can send more messages, add constraints, request a reassessment, or stop it. The floating chat keeps the conversation close at hand; detailed tool activity is folded into the details view. Stopping interrupts further execution; it does not automatically undo actions already submitted to another application.

## Quick start

You need **Android 11 or newer**, a USB **data** cable, and a **Windows 10/11 x64** PC. The USB package includes Python and ADB; the PC does not need a separate Python installation.

### Choose your download pair

| Channel | Main package | USB package |
| --- | --- | --- |
| Official download | `01-*.apk`: install on your phone | `02-*-USB-en.zip`: the complete USB folder |
| Redistribution | `03-*-Redistribution-Main-en.zip`: APK and companion payload | `04-*-Redistribution-USB-en.zip`: Start/Stop scripts only |

**Most users need only `01 + 02`, not every asset.** Pick either `-en.zip` or `-zh-CN.zip` within a group; the app itself includes language selection.

For redistributed downloads, use the same version and language of `03 + 04`. Extract both, then copy **all contents inside** `VVA-Main/usb-payload/` into `VVA-USB/`, beside `Start.cmd` and `Stop.cmd`. Do not nest the `usb-payload` folder itself. The tiny `04` archive intentionally contains only those two scripts. See the [USB guide](USB.en.md) for the full workflow.

`90` contains licensing material and `99-SHA256SUMS.txt` lists checksums; these appear last. Licensing material is also bundled in the app and USB packages.

1. Get the matching APK and complete USB package from the official [Releases](https://github.com/sunnyfox-qinghu/VVA/releases).
2. Install the APK, select a model provider in the app, and enter your own API key.
3. Extract the complete USB package into a writable folder on your USB drive. Do not run it inside an archive preview.
4. Enable Developer options and **USB debugging** in Android settings. Connect and unlock your phone, then accept that PC's debugging authorization.
5. On a PC you own or are authorized to use, connect the drive and phone, run `Start.cmd`, enter `START`, grant desktop and/or command access as needed, and select the correct phone. Keep the connection and launcher window open while working.
6. When finished, press **S** in the launcher or run `Stop.cmd`. After an unexpected exit, use `Clean.cmd`. The Chinese package uses `启动.cmd`, `终止.cmd`, and `清理.cmd` respectively.

Controlling the phone's own interface requires Accessibility permission; floating chat requires permission to display over other apps. Long-running and scheduled tasks may also need notification, background-execution, and alarm permissions as prompted by Android. Controlling only the PC over USB does not require enabling the phone's Accessibility service.

See the [USB setup guide](USB.en.md) for permissions and troubleshooting. You can turn off USB debugging when it is not in use; do not authorize debugging on an untrusted PC.

## Making work faster

VVA takes its name from the VVA-14. We have worked on the different paths an assistant can take through a task:

- Read control text directly when available, use background scripts where appropriate, and use screenshots, OCR, or local crops when visual inspection is needed.
- Use semantic targeting, element indexing, action batches, background-window reads, and action receipts on the PC.
- Verify input when readback is available, check the target when switching windows, and inspect the actual state after reconnecting to reduce mistakes and duplicate submissions.

The aim is simple: fewer screenshots, less repeated searching for controls, and fewer unnecessary round trips—so the assistant can establish what happened and what comes next.

The phone contributes too: local computation, information processing, and background jobs can run there. When the data is already on the PC, it can be processed in place, with only the needed results sent back.

## ⚡ Lightning mode — experimental

Lightning mode lets the main agent delegate independent subtasks and, when device resources permit, increases local compute concurrency. Analysis, computation, and waiting can overlap. The main agent still coordinates device input.

| Approach | Median elapsed time |
| --- | ---: |
| One agent, one batch | About 39.3 seconds |
| Three subagents in Lightning mode | About 29.5 seconds |

This is a **small-sample comparison from revision 73**: the same phone, DeepSeek Flash with max reasoning, and the same four independent data-processing tasks, with two runs per approach. Outputs passed checks against independently computed answers. Timing covers prearranged compute batches, excluding additional planning and synthesis by the main model. Not every task can be divided, and other models may perform differently. See the [benchmark notes](BENCHMARKS.md).

Lightning mode can increase model usage, battery drain, and heat. Enable it when the task benefits from parallel work.

## Privacy: your workspace stays in your hands

**VVA does not require you to move your private workspace into our cloud. There is no VVA account, VVA-hosted conversation storage, or VVA server relaying phone-to-PC control.**

- **The control connection is local.** The phone and PC communicate over USB, with the companion listening on the PC's loopback interface. Device control does not need a VVA cloud relay.
- **Records stay on your own devices.** Conversations, task archives, evidence, and operation records are stored on the phone or in your chosen workspace. You can manage, back up, and clear them yourself. Material saved in the USB workspace travels with the drive.
- **Model credentials stay on the phone.** API keys use Android Keystore-backed encrypted storage. Normal pairing does not require configuring your model account or API key on the target PC.
- **No permanent PC service is required.** The companion starts for the session; it does not register a Windows service or startup entry. You can stop the session connection when finished.

**Local operation does not mean a cloud model cannot see task content.** Messages, file contents, screenshots, and tool results included in model requests may be sent to your chosen provider and are subject to its data policy. VVA does not run that relay or control the provider's retention policy.

OCR runs on-device, but its SDK may send operational metrics; see the [privacy notice](PRIVACY.md). Used workspaces can contain sensitive information. Share clean distribution packages and redact private details before posting feedback.

## Safety and permissions

- **Use only devices you own or are authorized to operate.** Ordinary tasks do not require Android root or Windows administrator rights.
- **Define the scope of administrator work.** Use `Start-Administrator.cmd` (`启动-管理员.cmd` in the Chinese package) and confirm Windows UAC yourself. Full Trust and Approve for me do not grant operating-system administrator rights.
- **Use official downloads.** VVA can perform privileged operations. Check the source, version, and signature information in the [signing guide](SIGNING.md).
- **End the session; keep the work.** `Stop.cmd` stops this package's companion, releases its session channel, and cleans its temporary session state. Workspaces, reports, and phone conversations remain. It does not erase all operating-system or third-party logs, caches, or changes, and it does not promise a traceless session. Incomplete cleanup is reported.
- **Write down protection rules.** Put requirements in SOUL, skills, or task instructions—for example, “do not modify this directory,” “keep a backup before overwriting,” or “do not send this document to a cloud model.” Use permissions and backups as well; written instructions do not replace them. Keep passwords and API keys out of public feedback.

## Make it yours

- Edit **SOUL**, write **skills**, configure **Hooks**, or install compatible plugins. Native dependencies intended for desktop systems may not work on Android.
- Prepare a folder named `tools-pack-for-model` on your USB drive with tools, scripts, and instructions you want the model to use. Full Trust exposes the toolbox invocation entry points. You can edit the supplied template or select another directory with the same name. Third-party tools may require a separate download or acceptance of their terms.
- Ask the model to write and test script extensions, then activate or roll them back with authorization. This is different from automatically modifying, rebuilding, or upgrading the entire app; that is not a promised release capability.

## Platforms

| Platform | Status |
| --- | --- |
| Android 11+ — phone | Supported; background and permission behavior varies by manufacturer |
| Windows 10/11 x64 — PC | Supported |
| macOS / Linux — PC | No companion provided yet |
| iOS | Not currently supported |

## Credits and licensing

VVA develops the mobile interface, device control, task recovery, local archives, and extension capabilities around a phone, USB, and portable workspace. Its runtime reuses core code from Nous Research's [Hermes Agent](https://github.com/NousResearch/hermes-agent), including the agent loop and native context compression, under the MIT license, with VVA-specific adaptations and mechanisms. VVA is not affiliated with Nous Research.

**VVA is currently free to use; its development source is not publicly released.** Distribution rules for VVA-authored components are in [DISTRIBUTION](DISTRIBUTION.md). Third-party components and their own licenses are listed in [THIRD_PARTY_NOTICES](THIRD_PARTY_NOTICES.md).

## Feedback

We love this project and use it ourselves. Questions, suggestions, and ambitious ideas are welcome.

Official contact: [vvaofficial@outlook.com](mailto:vvaofficial@outlook.com).

Include the version, device model, reproduction steps, and redacted error details when reporting a problem.

This is my first publicly released project. I hope you enjoy it.
