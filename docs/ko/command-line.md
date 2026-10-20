# 명령줄

[English](../en/command-line.md) · [사용 방법 처음](../../README.ko.md)

AI가 MCP로 하는 일은 모두 `pinvane` 명령으로도 할 수 있습니다 — 명령을 실행할 수 있는 AI도, 사람도.

- 결과는 기본으로 **JSON** 입니다. 읽는 글로 보려면 `--text`.
- `--lang ko` · `--lang en` 은 알림 글의 언어를 고릅니다.
- `pinvane <명령> --help` 가 모든 선택을 보여 줍니다.

> 설치한 뒤 `pinvane` 을 실행하는 정확한 방법(폴더 · 명령)은 출시 때 적습니다.

## CSV 두 개로 첫 도면

[examples/demo-cart-24v](../../examples/demo-cart-24v)의 가상 데모 순서입니다.

```text
pinvane new demo-cart --drawing full --name "데모 수레 24 V (가상)" --company "Pinvane demo"
pinvane import-table demo-cart --parts examples/demo-cart-24v/ko/parts.csv --wires examples/demo-cart-24v/ko/wires.csv
pinvane export demo-cart
```

1. `new` 는 도면 한 장짜리 빈 프로젝트 폴더를 만듭니다.
2. `import-table` 은 부품 목록과 결선표를 **변경 묶음 하나**로 가져와 도면에 배치합니다.
3. `export` 는 도면과 작업표를 새 묶음 폴더에 씁니다.

출력을 영어로 내려면 내보내기 전에 `pinvane title demo-cart lang=en` 으로 표제란의 출력 언어를 바꿉니다(기본은 한국어).

## CSV 표 가져오기

```text
pinvane import-table <프로젝트> [--parts parts.csv] --wires wires.csv [--map columns.json] [--new] [--dry-run]
```

- **결선표**(꼭 필요) — 선 하나가 한 줄. 데모의 열 이름:
  `번호, 묶음, 출발 부품, 출발 단자, 도착 부품, 도착 단자, 색, 굵기, 근거, 비고`
- **부품 목록**(고르는 것) — 데모는 `키, 이름, 형번, 자리`. 없으면 결선표의 부품 이름이 부품이 됩니다.
- 열 이름을 못 알아보면 `--map` 으로 작은 JSON 을 줍니다: `{"parts": {"<칸>": "<내 열>"}, "wires": {"<칸>": "<내 열>"}}`.
- 표에 없는 값 — 굵기 · 색 · 단자 — 은 **미정**으로 남아 확인 목록의 질문이 됩니다. Pinvane은 기본값을 채우지 않습니다.
- 근거 · 값 칸의 「추정」 · 「도면」 · 「모름」 같은 말은 근거 등급으로 남습니다.
- `--new` 는 프로젝트가 없으면 먼저 만들고, `--dry-run` 은 도면은 건드리지 않고 `out/` 에만 결과를 씁니다.
- 가져오기 전체를 되돌리려면 `pinvane undo <프로젝트>`.

## 자주 쓰는 명령

| 명령 | 하는 일 |
|---|---|
| `new <폴더>` | 도면 한 장짜리 빈 프로젝트(`--name` · `--company` · `--paper A4…A0` · `--orientation`) |
| `import-table <프로젝트>` | 부품 목록 + 결선표(CSV) → 변경 묶음 하나 + 배치된 도면 |
| `check <프로젝트>` | 저장된 도면 그대로 도면 검사 · 설계 검사 |
| `export <프로젝트>` | 도면 PDF · SVG · PNG · DXF 와 작업표(HTML · CSV · 엑셀 · PDF) |
| `title <프로젝트> 칸=값 …` | 표제란 칸(예 `drawing_no=…` · `lang=en`) |
| `paper <프로젝트>` | 용지 크기 · 방향 · 맞추기 · 도면 틀 |
| `edit <프로젝트>` · `open <프로젝트>` | 편집기 · 읽기 전용 보기(`127.0.0.1`) |
| `start [<프로젝트>]` | 바탕화면 아이콘이 하는 일: 편집기 창, 창을 닫으면 끝 |
| `history` · `undo` · `redo` | 고치기 기록(변경 묶음, 새것부터) · 되돌리기 · 다시 하기 |
| `tools` · `call <도구>` | MCP 도구 목록 · MCP 도구 하나를 명령줄에서 부르기 |
| `report-bug` | 내가 읽고 직접 보내는 문제 보고서 만들기([도움](help.md#문제-알리기)) |
| `update --check` | 요청할 때 새 판 확인([도움](help.md#업데이트-확인)) |
| `version` | Pinvane 판 · 자료 형식 |

## 내보내기 선택

```text
pinvane export <프로젝트> [--formats pdf,svg,png,dxf] [--no-tables] [--purpose test|production]
                          [--paper A4|A3|A2|A1|A0|custom] [--orientation landscape|portrait|auto] [--fit scale|respace|split]
```

- `--list-formats` 는 내보낼 수 있는 것과 나오는 파일을 보여 줍니다 — 내보내기 창과 같은 목록.
- `--purpose test` 는 검사 오류가 있어도 내보내고 표시하며, `--purpose production` 은 검사 오류가 남으면 멈춥니다.
- 내보내기마다 `<프로젝트>/out/export/` 아래에 따로 폴더가 생기고 `manifest.json`(파일 목록 · 지문)이 함께 들어갑니다.
- 용지 선택은 이번 내보내기에만 쓰입니다. 프로젝트에 저장하려면 `pinvane paper`.
