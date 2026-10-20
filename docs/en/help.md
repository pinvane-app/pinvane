# Help, updates and problem reports

[한국어](../ko/help.md) · [Guide home](../../README.md)

Help without handing over your drawings. Pinvane has no automatic error reporting.

## Report a problem

1. Make a report: **Help → Report a problem…** in Pinvane, or `pinvane report-bug --steps "what I did" --out report.txt` (an AI app can call `make_bug_report`).
2. Pinvane fills in the automatic part with only the app version, data format, build, operating system, window browser, screen language, plan, and fixed error codes with module, line and count. Names, file paths, keys and drawing content are not among the automatically collected items. The steps you type are added below.
3. What you write or change is included in the report, so **read the whole report** and delete anything you do not want to share.
4. Send it yourself (**Copy**, **Open in my mail** or a saved file): open an [issue](https://github.com/pinvane-app/pinvane/issues/new/choose) or write to support@pinvane.com. Pinvane sends nothing to a support server. When an AI app makes the report through MCP, the report text also goes to that AI app.

No report? Write the Pinvane version (`pinvane version`), your Windows version, what you did, what happened and the error text — remove any names or paths you do not want to share.

**Please never attach drawings, project files, customer names or file paths.** If a problem must be shown, make a small sample project with a few parts that shows the same thing.

## Check for updates

*Release preparation: the public key for checking update signatures is added at release — until then every check says it could not check.*

- **Help → Check for updates** in Pinvane, or `pinvane update --check`, fetches one public, signed update file from pinvane.com and compares it with your version **on your computer**. The request carries no app version, licence, device ID or project.
- The server that handles the connection processes your IP address, the time and the requested path.
- Pinvane checks only when you ask — never at start-up or on a schedule. It only checks update information and never downloads or installs an installer by itself.
- What changed in each version: [CHANGELOG.md](../../CHANGELOG.md) and https://pinvane.com/changelog/.

## Common questions

**I have never drawn a wiring diagram. Can I use Pinvane?**
Yes — that is who it is for. Give your AI the parts and what they should do; the AI draws with Pinvane and the check list asks you, in plain words, what is still unknown. Someone who knows the machine must still confirm lengths, contacts and terminals before building.

**Which AI can use Pinvane?**
AI apps that support local MCP servers, or any AI that can run commands. We test with Claude and Codex. You can also use the built-in AI window with your own API key from Anthropic, OpenAI or Google.

**Can I draw by hand without any AI?**
Yes. The editor has everything for drawing by hand: parts, wires, bundles, text, title block, paper sizes, checks and exports.

**Does Pinvane send my drawings anywhere?**
Not during ordinary drawing, editing and exporting. If you use the AI features, your request and design information go to the AI provider you chose; the phone view shows a drawing to a device on your local network. A privacy page listing everything that can leave your computer will be published on pinvane.com.

**Which files can I export?**
Drawings as PDF, SVG, PNG and DXF; work tables as HTML, CSV, Excel and PDF.

**Does it work without internet?**
Drawing and exporting work offline. The automatic licence check runs at most once a day; within the licence period you can work up to 30 days offline, and after the subscription end or the check deadline there are 7 days of grace. AI services need a connection.

**What happens when my subscription ends?**
You can still open, view and export your drawings (exports may carry a mark). Subscribe again to edit and use AI, or move to the free plan to edit within its limits, without AI.

**Which paper sizes are supported?**
A4, A3, A2, A1, A0 and custom sizes, in portrait or landscape, with an editable title block.

Plans and prices (planned, before sale): https://pinvane.com/pricing/.

## Contact

- **Public questions and problem reports:** [Issues](https://github.com/pinvane-app/pinvane/issues/new/choose) — please never attach drawings there.
- **Private matters:** support@pinvane.com — answers in Korean or English, aiming for two business days (Korean time). Replies are written by Pinvane's support AI and say so; write "person" if you want a person to look. A reply may come from a different address than support@pinvane.com.
- **Security problems:** report privately — see [SECURITY.md](https://github.com/pinvane-app/.github/blob/main/SECURITY.md).
