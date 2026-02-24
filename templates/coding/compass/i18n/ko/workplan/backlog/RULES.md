# 규칙: backlog/

> 작업 대기 중인 계획.

## 이 폴더의 내용

- 정의되었고 시작 준비가 된 계획 (또는 우선순위 결정 대기 중)
- 새 계획은 생성 후 여기에 입력됨

## 명명 규칙

**이슈 트래커 사용 (GitHub / GitLab):**

```
BACKLOG-YYYY-MM-DD-iNNNN-description.md
```

**이슈 트래커 미사용:**

```
BACKLOG-YYYY-MM-DD-description.md
```

날짜는 계획이 생성된 시점을 반영합니다.

## 주요 규칙

- 각 계획에는 `상태: Backlog`이 포함된 표준화된 헤더가 있어야 함
- **이슈 트래커가 설정된 경우**, 먼저 이슈를 생성 (`gh issue create`, `glab issue create` 등)하고 파일 이름에 이슈 번호를 사용 (`iNNNN`)
- 작업 시작 시: `coding/`로 이동, 접두사를 `CODING`으로 변경, 날짜와 헤더 업데이트
- 일시 중지 시 `coding/`에서 여기로 되돌릴 수도 있음
- 전체 참조는 `workplan/README.md` 참고

## 참고

- `coding/RULES.md` — 진행 중인 계획의 규칙
- `done/RULES.md` — 완료된 계획의 규칙
- `draft/RULES.md` — 초안과 아이디어의 규칙
