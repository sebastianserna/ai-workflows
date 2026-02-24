# 규칙: draft/

> 초안은 아이디어 뱅크: 계획 초안, 기술적 결정, 탐색적 메모.

## 이 폴더의 내용

- 아직 backlog에 넣을 준비가 되지 않은 초기 단계의 아이디어
- 기술적 결정 기록
- 탐색적 메모 및 리서치

## 명명 규칙

```
DRAFT-YYYY-MM-DD-description.md
```

트래커 설정에 관계없이 초안에는 이슈 식별자를 **절대** 붙이지 않습니다.

## 주요 규칙

- 각 초안에는 `state: "draft"`이 포함된 YAML frontmatter가 있어야 함 (형식은 `workplan/README.md` 참고)
- 초안은 BACKLOG → CODING → DONE 워크플로를 **따르지 않음**
- 초안이 충분히 성숙하면 `backlog/`에 정식 계획으로 승격
- 전체 참조는 `workplan/README.md` 참고

## 참고

- `backlog/RULES.md` — 대기 중인 계획의 규칙
- `coding/RULES.md` — 진행 중인 계획의 규칙
- `done/RULES.md` — 완료된 계획의 규칙
