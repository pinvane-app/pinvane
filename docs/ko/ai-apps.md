# AI 앱 연결

[English](../en/ai-apps.md) · [사용 방법 처음](../../README.ko.md)

Pinvane은 AI가 쓰기 좋게 만든 도구입니다. AI는 Pinvane의 **로컬 MCP 서버**(AI 앱이 도구를 부르는 표준 방식)나 **명령줄**로 그리기 · 고치기 · 검사 · 내보내기를 하고, 정리된 답을 받습니다.

기능 대응표(2026-10-20 기준): 화면 기능 95개를 AI 지원 80 · 일부 1 · 해당 없음 14으로 나눴습니다. 「일부」는 부품에 SVG 그림 넣기입니다(AI는 PNG · JPEG · WebP를 넣을 수 있음). 「해당 없음」은 마우스로 고르기 · 격자 맞춤 · 밝게/어둡게처럼 AI에게 필요 없는 화면 편의 기능입니다.

## 로컬 MCP 서버

- 서버는 `pinvane mcp` 로 켜집니다. 기본으로 AI 앱이 **내 컴퓨터에서** 이것을 켜고 표준 입출력(stdio)으로 이야기합니다. 그 사이에 인터넷의 Pinvane 서버는 없습니다.
- 고르는 것: `pinvane mcp --http` 는 같은 도구를 `127.0.0.1` 에서만, 토큰과 Origin 검사를 붙여 엽니다.
- **AI 앱은 받은 내용을 그 앱의 설정 · 약관에 따라 자기 서비스로 보낼 수 있습니다.**

### AI의 고치기는 모두 제안입니다

**내가** 받아들이기 전에는 도면이 바뀌지 않습니다. AI가 고치기를 제안하면 Pinvane에 「AI 제안 n건이 왔습니다 — 기록 탭」이 뜹니다. **기록** 탭(또는 AI 탭)에서 미리 보기를 살펴보고 **받아들이기**를 누릅니다. 그 사이 다른 고치기와 충돌하는 제안에는 「받아들이면 안 됩니다」가 붙습니다.

AI가 자기 제안을 받아들이게 하려면 **AI 가 명령으로 받아들이기 허용**을 켭니다(또는 `pinvane mcp --allow-accept` 로 서버를 켬). 기본은 꺼짐입니다.

설계 · 도면 고치기는 **변경 묶음**입니다. 적용 전에 검사하고, 한 번에 되돌립니다(`pinvane undo` 또는 편집기의 되돌리기).

## AI 앱에 Pinvane 넣기

*자주 쓰는 AI 앱별 안내는 출시 때 더합니다.* 일반적인 순서:

1. Pinvane을 설치하고 한 번 엽니다.
2. 쓰시는 AI 앱의 MCP 설정에 **로컬(stdio) 서버**를 더하고, 명령은 `pinvane mcp` 를 실행하게 합니다.
3. AI에게 부품 목록과 메모를 주고 Pinvane으로 그려 달라고 합니다.
4. 동의하는 제안을 받아들이고, 확인 목록에 답하고, 편집기에서 살펴봅니다.

어떤 AI가 쓸 수 있나요? 로컬 MCP를 지원하는 AI 앱, 또는 명령을 실행할 수 있는 AI입니다. 우리는 Claude와 Codex로 시험합니다.

## 도구가 다루는 것

`pinvane tools` 가 도구 전부를 보여 주고, `pinvane call <도구> …` 는 도구 하나를 같은 인자 · 같은 결과로 명령줄에서 부릅니다. 명령줄과 MCP가 도구 목록 하나를 같이 씁니다.

| 묶음 | 도구 |
|---|---|
| 프로젝트 · 도면 | `open_project` · `new_project` · `new_drawing` · `build_drawing` · `get_drawing` · `snap_region`(장 보기) |
| 부품 · 선 | `list_parts` · `add_part` · `define_part` · `define_connector` · `list_definitions` · `connect_wire` · `change_wire` · `move_part` · `remove_items` · `add_splice` · `pair_connectors` · `name_halves` |
| 설계 정보 | `set_function` · `set_check_item` · `set_estop` · `set_design_facts` · `set_part_power` · `set_design_entry` |
| 검사 | `check_drawing` · `design_checks` · `tidy_drawing` · `compare_versions` |
| 제안 · 기록 | `propose_changes` · `list_proposals` · `accept_proposal` · `reject_proposal` · `list_history` · `undo_batch` |
| 용지 · 내보내기 | `set_title_block` · `set_paper` · `export_formats` · `export_outputs` |
| 그 밖 | `get_version` · `make_bug_report` |

## AI 창(내 키)

Pinvane에는 **내 API 키**(Anthropic · OpenAI · Google)로 쓰는 내장 AI 창도 있습니다. **기본은 꺼짐**이고, 쓰면 요청과 그 일의 설계 정보가 내가 고른 AI 회사로 갑니다.

## 좋은 초안을 위한 요령

- 아는 것을 주고, 모르는 것은 모른다고 말하세요. Pinvane은 모르는 값을 *미정*으로 두고 질문으로 바꿉니다 — 굵기나 색을 짐작해 채우지 않습니다.
- 자료의 「추정」 · 「도면」 · 「모름」 같은 말은 원문과 함께 근거 등급으로 남습니다.
- AI에게 제안을 넘기기 전에 검사를 돌리고 장을 살펴보게 하세요.
