# Demo cart 24 V (fictional)

[한국어](#한국어)

A **fictional** 24 V cart — 12 parts and 24 wires — used in Pinvane's screenshots and videos. It is not a real machine and not customer data. Some values are left out or marked "estimated" on purpose, so you can see how Pinvane turns them into questions.

| Folder | Files |
|---|---|
| `en/` | `parts.csv` (key, name, spec, where) · `wires.csv` (no, group, from, from terminal, to, to terminal, colour, gauge, evidence, note) |
| `ko/` | The same cart with Korean names and column titles |

Try it with the [command line](../../docs/en/command-line.md#a-first-drawing-from-two-csv-files):

```text
pinvane new demo-cart --drawing full --name "Demo cart 24 V (fictional)" --company "Pinvane demo"
pinvane import-table demo-cart --parts en/parts.csv --wires en/wires.csv
pinvane title demo-cart lang=en
pinvane export demo-cart
```

Or give the two files to your AI app and ask it to draw the cart with Pinvane.

## 한국어

**가상** 24 V 수레(부품 12 · 선 24)입니다. Pinvane 화면 사진과 영상에 씁니다. 실제 장비도, 손님 자료도 아닙니다. 일부 값은 일부러 비우거나 「추정」으로 적어, Pinvane 이 그것을 질문으로 바꾸는 모습을 볼 수 있게 했습니다.

```text
pinvane new demo-cart --drawing full --name "데모 수레 24 V (가상)" --company "Pinvane demo"
pinvane import-table demo-cart --parts ko/parts.csv --wires ko/wires.csv
pinvane export demo-cart
```

자세한 설명: [명령줄](../../docs/ko/command-line.md#csv-두-개로-첫-도면)
