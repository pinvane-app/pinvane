# Connect your AI app

[한국어](../ko/ai-apps.md) · [Guide home](../../README.md)

Pinvane is made for AI to use. An AI can draw, change, check and export through Pinvane's **local MCP server** (the standard way AI apps call tools) or the **command line**, and gets structured answers back.

Feature map (2026-10-20): 95 screen features classified — 80 supported for AI, 1 partly, 14 not applicable. "Partly" is adding an SVG picture to a part (an AI can add PNG, JPEG or WebP). "Not applicable" are screen conveniences an AI does not need, such as mouse selection, grid snapping or the light/dark switch.

## The local MCP server

- The server is started with `pinvane mcp`. By default your AI app starts it **on your computer** and talks to it over standard input and output (stdio). There is no Pinvane server on the internet in between.
- Optional: `pinvane mcp --http` serves the same tools on `127.0.0.1` only, with a token and an Origin check.
- **Your AI app may send what it receives to its own service**, under that app's own settings and terms.

### Every AI edit is a proposal

Nothing in your drawing changes until **you** accept it. When an AI proposes a change, Pinvane shows "AI proposal(s) arrived — History". Open **History** (or the AI tab), look at the preview and press **Accept**. A proposal that conflicts with a newer edit is marked "do not accept".

If you want the AI to accept its own proposals, turn on **Let the AI accept by command** (or start the server with `pinvane mcp --allow-accept`). It is off by default.

Design and drawing changes are **change sets**: checked before they apply and undone as one step (`pinvane undo`, or Undo in the editor).

## Add Pinvane to your AI app

*Step-by-step guides for common AI apps will be added at release.* In general:

1. Install Pinvane and open it once.
2. In your AI app's MCP settings, add a **local (stdio) server** whose command runs `pinvane mcp`.
3. Give the AI your parts list and notes, and ask it to draw with Pinvane.
4. Accept the proposals you agree with, answer the check list, and review the drawing in the editor.

Which AI can use Pinvane? AI apps that support local MCP servers, or any AI that can run commands. We test with Claude and Codex.

## What the tools cover

`pinvane tools` lists every tool; `pinvane call <tool> …` runs one from the command line with the same arguments and results. The command line and MCP share one tool list.

| Group | Tools |
|---|---|
| Projects and drawings | `open_project` · `new_project` · `new_drawing` · `build_drawing` · `get_drawing` · `snap_region` (look at a sheet) |
| Parts and wires | `list_parts` · `add_part` · `define_part` · `define_connector` · `list_definitions` · `connect_wire` · `change_wire` · `move_part` · `remove_items` · `add_splice` · `pair_connectors` · `name_halves` |
| Design information | `set_function` · `set_check_item` · `set_estop` · `set_design_facts` · `set_part_power` · `set_design_entry` |
| Checks | `check_drawing` · `design_checks` · `tidy_drawing` · `compare_versions` |
| Proposals and history | `propose_changes` · `list_proposals` · `accept_proposal` · `reject_proposal` · `list_history` · `undo_batch` |
| Paper and outputs | `set_title_block` · `set_paper` · `export_formats` · `export_outputs` |
| Other | `get_version` · `make_bug_report` |

## The AI window (your own key)

Pinvane also has a built-in AI window that uses **your own API key** from Anthropic, OpenAI or Google. It is **off by default**. When you use it, your request and the design information for that job go to the AI provider you chose.

## Tips for good drafts

- Give the AI what you know and say what you do not know. Pinvane keeps unknown values as *not set* and turns them into questions; it does not guess a gauge or colour for you.
- Words in your material such as "estimated", "from the drawing" or "unknown" are kept as evidence grades with the original text.
- Ask the AI to run the checks and look at the sheet before it hands the proposal over.
