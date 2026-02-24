# 규칙: done/

> 완료된 계획 — 보관 및 참조.

## 이 폴더의 내용

- 완전히 구현되고 검증된 계획
- 이 폴더는 이력 기록 역할을 함

## 명명 규칙

**이슈 트래커 사용 (GitHub / GitLab):**

```
DONE-YYYY-MM-DD-iNNNN-description.md
```

**이슈 트래커 미사용:**

```
DONE-YYYY-MM-DD-description.md
```

날짜는 계획이 완료된 시점을 반영합니다.

## 주요 규칙

- 각 계획에는 `state: "done"`이 포함된 YAML frontmatter가 있어야 함 (형식은 `workplan/README.md` 참고)
- 모든 진행 체크박스가 체크되어 있어야 함
- 완료된 계획은 일반적으로 수정하지 않음
- 전체 참조는 `workplan/README.md` 참고

## 참고

- `backlog/RULES.md` — 대기 중인 계획의 규칙
- `coding/RULES.md` — 진행 중인 계획의 규칙
- `draft/RULES.md` — 초안과 아이디어의 규칙
