# What's new

[한국어](CHANGELOG.ko.md) · Also on https://pinvane.com/changelog/

Pinvane is in pre-release testing. Changes, newest first.

## 0.2.0 — pre-release · internal builds

Builds of 2026-10-18 to 2026-10-20. The version number will go up with the first release.

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
- Feature map: 80 of 95 screen features supported through MCP and the command line, 1 partly, 14 not applicable (2026-10-20).
- Connector wizard, functions, checks and emergency-stop data through MCP; the command line and MCP share one tool list.

**Drawings and checks**
- Design checks grouped by job type (documenting an existing machine or a new design), with how to fix each group.
- Sheets split by function and area; voltage colours also marked on the wires; long texts wrap.

## First complete build — 2026-10-18

- Automatic layout from design data; hand-drawing editor; AI connection (local MCP server and the AI window with your own key); phone view.
- Exports: PDF, SVG, PNG, DXF and work tables; drawing frame with an editable title block; paper A4–A0 and custom.
- Screen in English or Korean with one button; screen colour chosen with colour-vision simulation and contrast checks.

## Known limits and issues

- A worker cannot yet work from the tables alone: lengths, terminations, terminal assignment and test criteria still need people (independent review, 2026-10-20).
- English output: some table texts and the legend's colour names are still Korean, and some print checks fail.
- Adding an SVG picture to a part works on screen only; an AI can add PNG, JPEG or WebP pictures.
