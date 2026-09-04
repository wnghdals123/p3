# Domain Docs

엔지니어링 스킬들이 코드베이스를 탐색할 때 이 리포의 도메인 문서를 어떻게 소비해야 하는지에 대한 규칙.

## Before exploring, read these

- 리포 루트의 **`CONTEXT.md`**, 또는
- 리포 루트에 있다면 **`CONTEXT-MAP.md`**: context마다 `CONTEXT.md` 하나를 가리킵니다. 주제와 관련된 것을 각각 읽으세요.
- **`docs/adr/`**: 작업하려는 영역과 맞닿은 ADR을 읽으세요. multi-context 리포에서는 context 범위의 결정을 담은 `src/<context>/docs/adr/`도 확인합니다.

이 파일들이 없으면 **조용히 진행**하세요. 부재를 지적하지 말고, 미리 만들자고 제안하지도 마세요. `/domain-modeling` 스킬(`/grill-with-docs`, `/improve-codebase-architecture`를 통해 도달)이 용어나 결정이 실제로 정리될 때 필요에 따라 생성합니다.

## File structure

Single-context 리포 (대부분의 리포):

```
/
├── CONTEXT.md
├── docs/adr/
│   ├── 0001-event-sourced-orders.md
│   └── 0002-postgres-for-write-model.md
└── src/
```

Multi-context 리포 (루트에 `CONTEXT-MAP.md`가 존재):

```
/
├── CONTEXT-MAP.md
├── docs/adr/                          ← system-wide 결정
└── src/
    ├── ordering/
    │   ├── CONTEXT.md
    │   └── docs/adr/                  ← context-specific 결정
    └── billing/
        ├── CONTEXT.md
        └── docs/adr/
```

## Use the glossary's vocabulary

출력이 도메인 개념을 지칭할 때(이슈 제목, 리팩터 제안, 가설, 테스트 이름 등), `CONTEXT.md`에 정의된 용어를 사용하세요. glossary가 명시적으로 피하는 동의어로 흘러가지 마세요.

필요한 개념이 아직 glossary에 없다면 그것은 신호입니다: 프로젝트가 쓰지 않는 언어를 지어내고 있거나(재고), 실제 공백이 있거나(`/domain-modeling`을 위해 기록).

## Flag ADR conflicts

출력이 기존 ADR과 모순되면, 조용히 덮어쓰지 말고 명시적으로 드러내세요:

> _ADR-0007 (event-sourced orders)과 모순되지만, 다시 논의할 가치가 있는 이유는…_
