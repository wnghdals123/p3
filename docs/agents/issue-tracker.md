# Issue tracker: Local Markdown

이 리포의 이슈와 스펙은 `.scratch/` 아래 마크다운 파일로 존재합니다.

## Conventions

- 기능(feature) 하나당 디렉터리 하나: `.scratch/<feature-slug>/`
- 스펙은 `.scratch/<feature-slug>/spec.md`
- 구현 이슈는 티켓 하나당 파일 하나로 `.scratch/<feature-slug>/issues/<NN>-<slug>.md`에 두며, `01`부터 번호를 매기고, 여러 티켓을 한 파일에 합치지 않습니다
- Triage 상태는 각 이슈 파일 상단 근처의 `Status:` 줄로 기록합니다 (role 문자열은 `triage-labels.md` 참고)
- 코멘트와 대화 이력은 파일 하단 `## Comments` 헤딩 아래에 덧붙입니다

## When a skill says "publish to the issue tracker"

`.scratch/<feature-slug>/` 아래에 새 파일을 만듭니다 (필요하면 디렉터리도 생성).

## When a skill says "fetch the relevant ticket"

참조된 경로의 파일을 읽습니다. 보통 사용자가 경로나 이슈 번호를 직접 전달합니다.

## Wayfinding operations

`/wayfinder`가 사용합니다. **map**은 티켓마다 **child** 파일 하나를 갖는 파일입니다.

- **Map**: `.scratch/<effort>/map.md` (Notes / Decisions-so-far / Fog 본문).
- **Child ticket**: `.scratch/<effort>/issues/NN-<slug>.md`, `01`부터 번호를 매기고 본문에 질문을 담습니다. `Type:` 줄은 티켓 유형(`research`/`prototype`/`grilling`/`task`)을, `Status:` 줄은 `claimed`/`resolved`를 기록합니다.
- **Blocking**: 상단 근처의 `Blocked by: NN, NN` 줄. 나열된 모든 파일이 `resolved`이면 티켓의 블로킹이 해제됩니다.
- **Frontier**: `.scratch/<effort>/issues/`를 훑어 open · 블로킹 해제 · unclaimed 상태인 파일을 찾고, 번호가 가장 앞선 것이 우선입니다.
- **Claim**: 작업 전에 `Status: claimed`로 설정하고 저장합니다.
- **Resolve**: `## Answer` 헤딩 아래에 답을 덧붙이고 `Status: resolved`로 설정한 뒤, `map.md`의 Decisions-so-far에 컨텍스트 포인터(gist + 링크)를 덧붙입니다.
