# 규칙: coding/

> 활발하게 작업 중인 계획.

## 이 폴더의 내용

- 현재 진행 중인 계획
- 활발하게 구현되고 있는 계획만 해당

## 명명 규칙

**이슈 트래커 사용 (GitHub / GitLab):**

```
CODING-YYYY-MM-DD-iNNNN-description.md
```

**이슈 트래커 미사용:**

```
CODING-YYYY-MM-DD-description.md
```

날짜는 작업이 시작된 시점을 반영합니다.

## 주요 규칙

- 각 계획에는 `상태: Coding`이 포함된 표준화된 헤더가 있어야 함
- 스텝 완료 시 진행 체크박스를 업데이트
- 완료 시: `done/`으로 이동, 접두사를 `DONE`으로 변경, 날짜와 헤더 업데이트
- 일시 중지 시: `backlog/`로 되돌리기, 접두사를 `BACKLOG`으로 변경, 헤더 업데이트
- 전체 참조는 `workplan/README.md` 참고

## 참고

- `backlog/RULES.md` — 대기 중인 계획의 규칙
- `done/RULES.md` — 완료된 계획의 규칙
- `draft/RULES.md` — 초안과 아이디어의 규칙
