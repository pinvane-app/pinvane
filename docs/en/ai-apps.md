# Connect your AI app

[한국어](../ko/ai-apps.md) · [Guide home](../../README.md)

Pinvane is made for AI to use. An AI can draw, change, check and export through Pinvane's **local MCP server** (the standard way AI apps call tools) or the **command line**, and gets structured answers back.

The MCP server carries a usage guide for your AI and ready-made prompts: draw from a parts list, work through the check list, export the work tables. AI connection is in Pro and in the 14-day trial ([plans](https://pinvane.com/pricing/)). One known limit: adding an SVG picture to a part works on screen only; an AI can add PNG, JPEG or WebP pictures.

## The local MCP server

- The server is started with `pinvane mcp`. By default your AI app starts it **on your computer** and talks to it over standard input and output (stdio). There is no Pinvane server on the internet in between.
- Optional: `pinvane mcp --http` serves the same tools on `127.0.0.1` only, with a token and an Origin check.
- Your AI app tells Pinvane which project folder to work on, but **the person sets the boundary for project data.** It starts with the default Pinvane folder and the folders added through `pinvane mcp-allow` or the `PINVANE_MCP_ALLOW` environment variable (with `--project`, that folder plus the added ones), and a path an AI passes as a tool argument is not added to the allow list. A connection started without `--project` narrows its default boundary to the real path of the first project opened or created, including descendants; the folders the person added remain available. The shared library is separately readable, and writing to it needs separate permission. Pinvane-made temporary copies for previews and comparisons are also used during those operations. Common file-access points and the final export folder are checked by real path. This boundary does not apply to the screen, the ordinary command line or the in-app AI window, and an AI program with shell access can run `mcp-allow` with the person's own rights.
- **Your AI app may send what it receives to its own service**, under that app's own settings and terms.

### Most AI edits are proposals

Changes to a drawing — placing, connecting, changing, moving and removing parts and wires, tidying, design information, title block and paper — arrive as **proposals**. When an AI proposes a change, Pinvane shows "AI proposal(s) arrived — History". Open **History** (or the AI tab), look at the preview and press **Accept**. A proposal that conflicts with a newer edit is marked "do not accept".

Some AI steps are **saved directly**, without a proposal: creating a new project or a new drawing, the first automatic layout of a drawing, defining a part or a connector (connector wizard), and writing export files. Placing a part on the drawing comes as a proposal, but if that step creates a new part definition, the definition can be saved first.

If you turn on **Let the AI accept by command** (off by default; or start the server with `pinvane mcp --allow-accept`), the AI can also accept proposals itself. Accepting by command uses this separate setting. Before acceptance, Pinvane checks the server-made connection identity against the proposal's session, the real project path, the proposal ID and the revision that connection last recorded. Acceptance by a person on screen is separate from this connection-ownership check.

Design and drawing changes are **change sets**: checked before they apply and undone as one step (`pinvane undo`, or Undo in the editor).

## Add Pinvane to your AI app

The exact steps depend on your AI app; this guide does not have app-by-app steps yet. In general:

1. Install Pinvane and open it once.
2. In your AI app's MCP settings, add a **local (stdio) server** whose command runs `pinvane mcp`. To let it work on a project outside the default Pinvane folder, first allow that folder yourself with `pinvane mcp-allow`.
3. Give the AI your parts list and notes, and ask it to draw with Pinvane.
4. Accept the proposals you agree with, answer the check list, and review the drawing in the editor.

Which AI can use Pinvane? AI apps that support local MCP servers, or any AI that can run commands. We test with Claude and Codex.

## What the tools cover

The main tools are below; `pinvane tools` lists every tool; `pinvane call <tool> …` runs one from the command line with the same arguments and results. The command line and MCP share one tool list.

| Group | Tools |
|---|---|
| Projects and drawings | `open_project` · `new_project` · `new_drawing` · `build_drawing` · `get_drawing` · `snap_region` (look at a sheet) |
| Parts and wires | `list_parts` · `add_part` · `define_part` · `define_connector` · `list_definitions` · `connect_wire` · `change_wire` · `move_part` · `remove_items` · `add_splice` · `set_splice` · `pair_connectors` · `name_halves` |
| Design information | `set_function` · `set_check_item` · `set_estop` · `set_design_facts` · `set_part_power` · `set_design_entry` |
| Checks | `check_drawing` · `design_checks` · `tidy_drawing` · `compare_versions` |
| Proposals and history | `propose_changes` · `list_proposals` · `accept_proposal` · `reject_proposal` · `list_history` · `undo_batch` |
| Paper and outputs | `set_title_block` · `set_paper` · `export_formats` · `export_outputs` |
| Other | `get_version` · `make_bug_report` |

## The AI window (your own key)

Pinvane also has a built-in AI window that uses **your own API key** from Anthropic, OpenAI or Google. It is **off by default**. When you use it, your request and the design information for that job go to the AI provider you chose, after you confirm a request card. The request card shows what goes first, what is never sent, the tools the AI may use with their argument names and the top-level fields tool results may carry. The initial design facts are prepared from your selected scope (the drawing you asked about, or only your selection). Later tool results are assembled from per-tool allowed fields. Pinvane checks the tools and top-level argument names offered for this request, and compares the part IDs in connection ends (from, to) against the approved scope. Nested structures are checked to a depth of 8; deeper structures are refused. Parts and wires added by the AI in this request join the scope for later calls. Other nested values are not checked against the scope. A tool error goes as a fixed code and sentence. Shared part-library search results can also go; each shared-library part row is rebuilt from a definition on Pinvane's shipped list whose content fingerprint matches. Your request goes as you typed it. See the [privacy page](https://pinvane.com/privacy/) for the full list.

## Tips for good drafts

- Give the AI what you know and say what you do not know. Pinvane keeps unknown values as *not set* and turns them into questions; it does not guess a gauge or colour for you.
- Words in your material such as "estimated", "from the drawing" or "unknown" are kept as evidence grades with the original text.
- Ask the AI to run the checks and look at the sheet before it hands the proposal over.
