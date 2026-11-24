# Getting started

[한국어](../ko/getting-started.md) · [Guide home](../../README.md)

> Pinvane 1.0.2 is out. Try every feature free for 14 days, no card needed.

## What you need

- **Windows 10 or Windows 11, 64-bit.**
- **Microsoft Edge (part of Windows) or Google Chrome** — Pinvane's window uses one of them with its own separate profile.
- **No internet for drawing.** Drawing and exporting work offline. The automatic license check runs at most once a day; activating and releasing devices also make a request.
- **For AI (optional):** an AI app that supports local MCP servers, or your own API key for the built-in AI window. AI connection is in Pro and in the trial ([plans](https://pinvane.com/pricing/)).

## Install

Pinvane installs for your Windows user only and needs no administrator rights.

**1. Download** the installer only from https://pinvane.com/download/ or this repository's [Releases](https://github.com/pinvane-app/pinvane/releases/tag/v1.0.2) page.

| | |
|---|---|
| File | `Pinvane-1.0.2-setup.exe` |
| Version | 1.0.2 |
| Size | 58.5 MB (61,334,066 bytes) |
| SHA-256 | `6c11a0ef97e4dde958f36cd3a4fe85e47cdfdf16e4ce9b2ca3e79fec644747e3` |
| Code signature | Not yet — see step 3 |

**2. Check the file before you run it.** Open PowerShell in your Downloads folder and run:

```powershell
(Get-FileHash .\Pinvane-1.0.2-setup.exe -Algorithm SHA256).Hash
```

The result must be the same 64 characters as the SHA-256 above (upper or lower case does not matter). If it differs, do not run the file — delete it and tell us at support@pinvane.com.

**3. If Windows says "Windows protected your PC".** The installer is not code-signed yet, so Windows Defender SmartScreen may stop it and show "Unknown publisher". Once the SHA-256 matches:

1. Click **More info**.
2. Check that the app name is the file you downloaded (`Pinvane-1.0.2-setup.exe`).
3. Click **Run anyway**.

Your browser may also warn that the file is not commonly downloaded. Keep it only after the checksum matches.

## Open Pinvane

Open Pinvane from its desktop icon. It opens your last project in the editor window; the first time, it opens a new, empty project. When you close the window, Pinvane stops by itself.

The screen opens in English. One button next to **Help** switches it to Korean and remembers your choice. The language of a drawing's outputs follows its title block.

## Two ways to make a drawing

### Let an AI draw the first draft

1. [Connect your AI app](ai-apps.md) to Pinvane.
2. Give the AI your parts list, connection table and notes, and ask it to draw with Pinvane.
3. Most of the AI's drawing changes arrive as **proposals**. Look at them and press **Accept** (in **History** or the AI tab). Some steps, such as a new drawing and its first layout, are saved directly — see [Connect your AI app](ai-apps.md#most-ai-edits-are-proposals).
4. Answer the [check list](check-list-and-outputs.md) and fix the drawing in the editor.

If your parts list and connection table are already CSV files, one command imports both and lays out the diagram — see [Command line → Import a CSV table](command-line.md#import-a-csv-table).

### Draw by hand

The editor has everything for drawing by hand:

- **Parts** — part library with drag and drop, your own parts, a connector wizard.
- **Wires** — terminal to terminal, with bends and joints; bundles, twisted pairs and shields.
- **Sheets** — text, shapes, zones, several sheets per drawing; paper A4–A0 or a custom size, portrait or landscape, with an editable title block.
- **Checks** — design checks while you work, auto-tidy, undo and history. Changes made by an AI are recorded with who made them.

A wire you draw by hand starts with **no colour or gauge**: an empty value is a real value in Pinvane, not a default. Reusing your last values is a switch you turn on.

## Uninstall

- Windows 11: **Settings › Apps › Installed apps**, then **⋯** next to Pinvane › **Uninstall**.
- Windows 10: **Settings › Apps › Apps & features** › Pinvane › **Uninstall**.

The uninstaller removes only the files it installed. Your drawings stay where you saved them, and your license and preferences stay in `%APPDATA%\Pinvane` — delete that folder yourself if you want them gone.

## Next

- [Check list and outputs](check-list-and-outputs.md) — what the check list asks and what you can export.
- [Help](help.md) — FAQ, update check and problem reports.
