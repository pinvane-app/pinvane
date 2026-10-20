# Getting started

[한국어](../ko/getting-started.md) · [Guide home](../../README.md)

> Pinvane is in pre-release testing. Installation steps will be completed with the first release.

## What you need

- **Windows (64-bit).** Supported versions will be listed at release.
- **Google Chrome or Microsoft Edge** installed — Pinvane's window uses one of them with its own separate profile.
- **No internet for drawing.** Drawing and exporting work offline. The automatic licence check runs at most once a day; activating and releasing devices also make a request.
- **For AI (optional):** an AI app that supports local MCP servers, or your own API key for the built-in AI window.

## Install

*At release.* Download the installer only from https://pinvane.com/download/ or this repository's [Releases](https://github.com/pinvane-app/pinvane/releases) page, and compare its SHA-256 with the published value before running it:

```powershell
Get-FileHash .\<installer file>
```

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

## Next

- [Check list and outputs](check-list-and-outputs.md) — what the check list asks and what you can export.
- [Help](help.md) — FAQ, update check and problem reports.
