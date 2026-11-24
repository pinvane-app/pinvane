# Command line

[한국어](../ko/command-line.md) · [Guide home](../../README.md)

Everything an AI does through MCP can also be done with the `pinvane` command — by an AI that can run commands, or by you.

- Results are **JSON** by default. Add `--text` for readable text.
- `--lang en` or `--lang ko` chooses the language of the messages.
- `pinvane <command> --help` shows every option.

> This guide does not yet give the folder and command for running `pinvane` after installing.

## A first drawing from two CSV files

This is the flow of the fictional demo in [examples/demo-cart-24v](../../examples/demo-cart-24v):

```text
pinvane new demo-cart --drawing full --name "Demo cart 24 V (fictional)" --company "Pinvane demo"
pinvane import-table demo-cart --parts examples/demo-cart-24v/en/parts.csv --wires examples/demo-cart-24v/en/wires.csv
pinvane title demo-cart lang=en
pinvane export demo-cart
```

1. `new` makes an empty project folder with one drawing.
2. `import-table` imports the parts list and the connection table as **one change set** and lays out the diagram.
3. `title … lang=en` sets the output language in the title block (the default output language is Korean).
4. `export` writes the drawing and the work tables into a new bundle folder.

## Import a CSV table

```text
pinvane import-table <project> [--parts parts.csv] --wires wires.csv [--map columns.json] [--new] [--dry-run]
```

- **Connection table** (required) — one row per wire. The demo uses these columns:
  `no, group, from, from terminal, to, to terminal, colour, gauge, evidence, note`
- **Parts list** (optional) — the demo uses `key, name, spec, where`. Without it, the part names in the connection table become the parts.
- If Pinvane does not recognise your column names, give a small JSON file with `--map`: `{"parts": {"<field>": "<your column>"}, "wires": {"<field>": "<your column>"}}`.
- A value your table does not give — a gauge, a colour, a terminal — stays **not set** and becomes a question on the check list. Pinvane does not fill in a default.
- Words such as "estimated", "from the drawing" or "unknown" in the evidence or value columns are kept as evidence grades.
- `--new` creates the project if it does not exist; `--dry-run` writes results to `out/` only and leaves the drawing alone.
- Undo the whole import with `pinvane undo <project>`.

## Common commands

| Command | What it does |
|---|---|
| `new <folder>` | Empty project with one drawing (`--name`, `--company`, `--paper A4…A0`, `--orientation`) |
| `import-table <project>` | Parts list + connection table (CSV) → one change set + laid-out diagram |
| `check <project>` | Drawing checks and design checks on the saved drawing |
| `export <project>` | Drawing as PDF · SVG · PNG (print, the default) or also DXF (`--style drawing`, for CAD), and the work tables (HTML · CSV · Excel · PDF); `--book` puts several drawings into one PDF and one viewer page, overview first |
| `title <project> field=value …` | Title-block fields (for example `drawing_no=…`, `lang=en`) |
| `paper <project>` | Paper size, orientation, fit, drawing frame and output style (`--style`) |
| `edit <project>` · `open <project>` | The editor · a read-only viewer, on `127.0.0.1` |
| `start [<project>]` | What the desktop icon runs: the editor window, ending when it closes |
| `history` · `undo` · `redo` | Edit history (change sets, newest first) and undo / redo |
| `tools` · `call <tool>` | The MCP tool list · run one MCP tool from the command line |
| `report-bug` | Write a problem report for you to read and send yourself ([Help](help.md#report-a-problem)) |
| `update --check` | Check for a new version when you ask ([Help](help.md#check-for-updates)) |
| `version` | Pinvane version and data format |

## Export options

```text
pinvane export <project> [--formats pdf,svg,png,dxf] [--no-tables] [--purpose test|production]
                         [--paper A4|A3|A2|A1|A0|custom] [--orientation landscape|portrait|auto] [--fit scale|respace|split]
```

- `--list-formats` lists what can be exported and which files come out — the same list as the export window.
- `--purpose test` exports even with check errors and marks them; `--purpose production` stops the export while check errors remain.
- Each export goes into its own folder under `<project>/out/export/` with a `manifest.json` (file list and fingerprints).
- Paper options apply to this export only; `pinvane paper` saves them in the project.
