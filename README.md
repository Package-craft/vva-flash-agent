# VVA Flash Agent

[简体中文](README.zh-CN.md)

**Android AI agent for phone automation and Windows computer use over USB.**

**I wanted an AI workspace I could carry in my pocket. So I built VVA Flash Agent.**

**On your phone. Within reach of your PC.**

It lives on your Android phone, helping you find information, organize files, write scripts, and operate apps.

When there is work to do on a Windows PC, connect a USB cable and plug in your USB drive. With your permission, VVA can operate software, read logs, and help troubleshoot problems.

**A phone, a cable, and a USB drive. Bring your files—and an assistant ready to work with them.**

There is no VVA account to register and no VVA-hosted control relay. Records stay on your devices, and you choose the model. When you use a cloud model, relevant task content is still sent to that provider.

The software is free, but you need to supply your own API key.

This is my first public project, and it is still growing. Try it on real tasks and tell me what feels smooth, what feels clumsy, and what surprises you. I would love to hear about it.

[Download the public preview](https://github.com/Package-craft/vva-flash-agent/releases/tag/v0.1.79-preview.1) · [Send feedback](mailto:vvaofficial@outlook.com)

Build availability and validation status are documented in the Release notes.

## Why VVA?

- **Local and private:** We will not receive any information about you.
- **A portable workspace:** A phone, a USB cable, and a USB drive let you operate a compatible Windows PC, with the runtime included. End the session with one action to clean up temporary files and keep your work.
- **Built for faster operation:** Direct control-text reads, background scripts, batched actions, and precise targeting reduce screenshots and unnecessary round trips.
- **Make it your own:** Customize SOUL, skills, Hooks, compatible plugins, and your USB toolbox to suit your needs.
- **⚡ Put your phone to work:** Experimental Lightning mode supports parallel local computation and subagent delegation, sharing the workload across the devices you carry.

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

### Download order

| Order | Download |
| --- | --- |
| 01 | [App APK (follows the phone language)](https://github.com/Package-craft/vva-flash-agent/releases/download/v0.1.79-preview.1/01-VVA-0.1.79-preview.1.apk) |
| 02 | [Complete USB package — Chinese](https://github.com/Package-craft/vva-flash-agent/releases/download/v0.1.79-preview.1/02-VVA-0.1.79-preview.1-USB-zh-CN.zip) |
| 03 | [Complete USB package — English](https://github.com/Package-craft/vva-flash-agent/releases/download/v0.1.79-preview.1/03-VVA-0.1.79-preview.1-USB-en.zip) |
| 04 | [Universal redistribution main (same APK and companion payload)](https://github.com/Package-craft/vva-flash-agent/releases/download/v0.1.79-preview.1/04-VVA-0.1.79-preview.1-Redistribution-Main.zip) |
| 05 | [Redistribution USB — Chinese](https://github.com/Package-craft/vva-flash-agent/releases/download/v0.1.79-preview.1/05-VVA-0.1.79-preview.1-Redistribution-USB-zh-CN.zip) |
| 06 | [Redistribution USB — English](https://github.com/Package-craft/vva-flash-agent/releases/download/v0.1.79-preview.1/06-VVA-0.1.79-preview.1-Redistribution-USB-en.zip) |

**There is one app APK, with Chinese and English and automatic phone-language selection. No separate English app is needed.**

Official downloads: **01 + 02 (Chinese)** or **01 + 03 (English)**.

Redistributed downloads: **04 + 05 (Chinese)** or **04 + 06 (English)**. Copy **all contents of** `VVA-Main/usb-payload/` beside the two entry scripts in `VVA-USB/`, including `.vva-language/`. The chosen launcher prepares the corresponding PC language files automatically. Each redistribution USB archive contains only its Start/Stop scripts.

`90` contains licensing material and `99-SHA256SUMS.txt` contains checksums; both appear last.

1. Get the matching APK and complete USB package from the official [Releases](https://github.com/Package-craft/vva-flash-agent/releases).
2. Install the APK, select a model provider in the app, and enter your own API key.
3. Extract the complete USB package into a writable folder on your USB drive. Do not run it inside an archive preview.
4. Enable Developer options and **USB debugging** in Android settings. Connect and unlock your phone, then accept that PC's debugging authorization.
5. On a PC you own or are authorized to use, connect the drive and phone, run `Start.cmd`, enter `START`, grant desktop and/or command access as needed, and select the correct phone. Keep the connection and launcher window open while working.
6. When finished, press **S** in the launcher or run `Stop.cmd`. After an unexpected exit, use `Clean.cmd`. The Chinese package uses `启动.cmd`, `终止.cmd`, and `清理.cmd` respectively.

Controlling the phone's own interface requires Accessibility permission; floating chat requires permission to display over other apps. Long-running and scheduled tasks may also need notification, background-execution, and alarm permissions as prompted by Android. Controlling only the PC over USB does not require enabling the phone's Accessibility service.

See the [USB setup guide](USB.en.md) for permissions and troubleshooting. You can turn off USB debugging when it is not in use; do not authorize debugging on an untrusted PC.

## How it gets faster

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

## Safety and permissions

- **Use only devices you own or are authorized to operate.**
- **Define the scope of administrator work.** Use `Start-Administrator.cmd` (`启动-管理员.cmd` in the Chinese package) and confirm Windows UAC yourself. Full Trust and Approve for me do not grant operating-system administrator rights.
- **Please make sure you are using the official software.**
- **End the session; keep the work.** `Stop.cmd` stops this package's companion, releases its session channel, and cleans its temporary session state. Workspaces, reports, and phone conversations remain. It does not erase all operating-system or third-party logs, caches, or changes, and it does not promise a traceless session. Incomplete cleanup is reported.
- **Write down protection rules.** Put requirements in SOUL, skills, or task instructions—for example, “do not modify this directory,” “keep a backup before overwriting,” or “do not send this document to a cloud model.” Use permissions and backups as well; written instructions do not replace them. Keep passwords and API keys out of public feedback.

## Make it yours

- Edit **SOUL**, write **skills**, configure **Hooks**, or install compatible plugins.
- Prepare a folder named `tools-pack-for-model` on your USB drive with tools, scripts, and instructions you want the model to use. Full Trust exposes the toolbox invocation entry points. You can edit the supplied template or select another directory with the same name. Third-party tools may require a separate download or acceptance of their terms.
- Ask the model to write and test script extensions, then activate or roll them back with authorization.

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
