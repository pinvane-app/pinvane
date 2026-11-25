# What's new

[한국어](CHANGELOG.ko.md) · Also on https://pinvane.com/changelog/

Changes, newest first. The newest version is 1.0.3.

## 1.0.3 — for the person doing the wiring · 2026-11-25

Download from https://pinvane.com/download/ or [Releases](https://github.com/pinvane-app/pinvane/releases/tag/v1.0.3): `Pinvane-1.0.3-setup.exe`, 61,354,118 bytes, SHA-256 `4737121da754f1d63fc1461d02511e9fc25ba806f03971bd8cff5a76db1bec66`. Installer built 2026-11-25. Check the SHA-256 before you run it — see [Getting started → Install](docs/en/getting-started.md#install).

**For the person doing the wiring**
- New worker bundle: `pinvane export --for worker` (A3 by default, `--paper` to choose; MCP `export_outputs` with `worker=true`). An overview page comes first, then work sheets where wire labels and terminal names are at least 8 pt, with the viewer and the work tables. The print check fails a worker or production export with text below 8 pt. The older worker drawing that `--for worker` used to pick is now `--drawing worker`.
- Every gauge carries its unit (6 mm², 20 AWG). When line colors show circuit types, the label also names the insulation color, and the legend is built from the design data.
- One page numbering across the whole book. Off-sheet flags say where the wire goes: page, wire number, part and terminal (→ 7/12 · E06 …).

**Viewer**
- Tabs show the page number and sheet title, the header shows the design name and revision, and the first screen is the sheet list.
- Tap a wire for its work card: both ends, insulation color, gauge, cut length, end treatment and three check boxes (end A plugged, end B plugged, tested), saved in this browser.

**For AI**
- The design name can be changed: `design.set` takes `project` (MCP `set_design_facts title=…`).

## 1.0.2 — clearer sheets and drawing books · 2026-11-25

Download from https://pinvane.com/download/ or [Releases](https://github.com/pinvane-app/pinvane/releases/tag/v1.0.2): `Pinvane-1.0.2-setup.exe`, 61,334,066 bytes, SHA-256 `6c11a0ef97e4dde958f36cd3a4fe85e47cdfdf16e4ce9b2ca3e79fec644747e3`. Installer built 2026-11-25. Check the SHA-256 before you run it — see [Getting started → Install](docs/en/getting-started.md#install).

**Clearer sheets**
- Zones (boxes, chassis, plates) are now a light tint with a thin solid outline, so they no longer look like dashed CAN or signal wires. In DXF the outline is one continuous line.
- Every sheet has its own legend in the info column, with only the wire colors, line styles, gauges and chips used on that sheet. The separate legend page at the end is gone.
- A part with a photo now shows the photo inside its box, together with the part name and every terminal name.

**One book for several drawings**
- `pinvane export --book` puts several drawings into one print PDF and one viewer page: first the overview sheet with all the wiring, then the sheets by function or area. Sheet numbers count across the whole book. Save the order with `pinvane paper --book`; the export window and the MCP `export_outputs` tool then use it.

**Fixes**
- In the viewer, "Hide unrelated" now also hides zones, drawing notes and cable bundle marks that have nothing to do with the part or wire you clicked, and keeps a part's picture with the part. "Print this circuit" matches.

## 1.0.1 — print-ready output · 2026-11-24

Download from https://pinvane.com/download/ or [Releases](https://github.com/pinvane-app/pinvane/releases/tag/v1.0.1): `Pinvane-1.0.1-setup.exe`, 61,322,674 bytes, SHA-256 `6221ea3150efa35a33be81d6b5486680321f674859b0125daaf3ef750a07a38b`. Installer built 2026-11-24. Check the SHA-256 before you run it — see [Getting started → Install](docs/en/getting-started.md#install).

**Print-ready by default**
- Exports are now big, easy-to-read wiring diagrams. Pinvane picks the paper size and orientation and scales the wiring up to fill the page, with a thick border and an info column for the title, edition, date and legend.
- To edit a sheet in AutoCAD or another CAD program, choose the drawing format (the export window's "Output style", `pinvane export --style drawing`, or MCP `export_outputs` with `style="drawing"`): the 1.0.0 output with an ISO frame, a title block, 1:1 scale and DXF. DXF comes only in the drawing format.

**For AI**
- The guide your AI reads now asks it to help people who have never drawn a wiring diagram: plain words, one question at a time, no made-up values, and print-ready output unless you want to edit in CAD.

**Fixes**
- Export no longer stops when a bus speed is written as a number; it now reads "250 kbps" or "1 Mbps".

## 1.0.0 — first release · 2026-11-22

Download from https://pinvane.com/download/ or [Releases](https://github.com/pinvane-app/pinvane/releases/tag/v1.0.0): `Pinvane-1.0.0-setup.exe`, 61,298,103 bytes, SHA-256 `f06f4d6b49ad9fa63568328b5c3066f3e5a6a537f0f7ee76e6e308011ec8adfb`. Installer built 2026-11-19. Check the SHA-256 before you run it — see [Getting started → Install](docs/en/getting-started.md#install).

**Passes, not subscriptions**
- Pro is a 30-day or 1-year pass paid once: nothing renews by itself. Buying again adds the new pass to the end of the time you have left.
- The app tells you 7 days and 1 day before a pass ends. After it ends there are 7 days to wrap up with every feature; after that you can still open, view and export your drawings.

**English output**
- The tool's own words in English tables and drawings are now English throughout, with US spelling.
- English test sheets now carry the same rows as the Korean ones — some rows were missing from them before.

**Test sheets and checks**
- Fixes from scoring and four deep reviews on six fictional test designs, among them: a voltage check for a converter missing from the power list, a separate emergency-stop test for each button, Ethernet and USB communication checks, and drive checks for lamps and contactors. [Test results](https://pinvane.com/evidence/)

**For AI**
- The MCP server carries a usage guide for your AI and ready-made prompts: draw from a parts list, work through the check list, export the work tables.

## 0.2.0 — pre-release history · internal builds

Internal builds of 2026-10-18 to 2026-10-20, before the first release. They were not published for download.

**Work tables a worker can follow**
- Worker-facing texts fixed after the independent review of internal test round 4 — label lists without reading notes, source wire colours kept, estimated gauges marked on the drawing, notes carried to the work tables — and re-checked.
- Cut-list, pin-table and test-sheet rows show their evidence state and related check numbers; undecided cells say "not set".
- "Unknown" is a real value: CSV import, wires added by an AI (MCP) and new wires drawn by hand no longer get a default gauge or colour; reusing the last values is an opt-in switch.
- Evidence words in English tables ("drawing", "estimated", "unknown" …) are graded like the Korean ones; a terminal named "-" or "+" keeps its name.
- Security: the local editor and viewer refuse requests from other sites; the AI window refuses later tool calls that name another drawing or out-of-scope parts and wires, omits the designated note, author and evidence fields and masks recognised file paths in later results, and refuses provider redirects.
- A pre-plug check table and a work order that match the other tables.
- The check list asks in plain words: what to confirm, where to look, what to bring, who decides, which work it unlocks.

**For AI**
- After creating a project, one command (`import-table`) imports a parts list and a connection table (CSV) and lays out the diagram.
- Feature map: 80 of 95 screen features supported through MCP and the command line, 1 partly, 14 not applicable.
- Connector wizard, functions, checks and emergency-stop data through MCP; the command line and MCP share one tool list.

**Drawings and checks**
- Design checks grouped by job type (documenting an existing machine or a new design), with how to fix each group.
- Sheets split by function and area; voltage colours also marked on the wires; long texts wrap.

## First complete build — 2026-10-18

- Automatic layout from design data; hand-drawing editor; AI connection (local MCP server and the AI window with your own key); phone view.
- Exports: PDF, SVG, PNG, DXF and work tables; drawing frame with an editable title block; paper A4–A0 and custom.
- Screen in English or Korean with one button; screen colour chosen with colour-vision simulation and contrast checks.
- Network audit test: a scripted local workflow makes no connection beyond this computer ([scope](https://pinvane.com/privacy/)).

## Known limits and issues

- No worker has wired a real machine from Pinvane's tables yet: our six test designs are fictional, and lengths, contacts and terminals still need people ([evidence](https://pinvane.com/evidence/#e3)).
- On a drawing's main sheet, the text in some part boxes can be cut short.
- English output: a few texts from less common cases may still appear in Korean.
- Adding an SVG picture to a part works on screen only; an AI can add PNG, JPEG or WebP pictures.
