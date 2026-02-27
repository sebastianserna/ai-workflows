# AGENTS.md

이 프로젝트에서 작업하는 AI 에이전트 가이드.

<!-- 언어: 에이전트 응답 언어와 코드 언어를 여기에 정의 -->

## 기술 스택

<!-- 프로젝트의 기술 스택을 여기에 정의. 예시:
- 프레임워크:
- UI:
- 백엔드/DB:
- 프로그래밍 언어:
-->

## 설정 및 명령어

<!-- 프로젝트 필수 명령어. 예시:
```bash
npm install        # 의존성 설치
npm run dev        # 개발 서버
npm run build      # 프로덕션 빌드
npm run lint       # 린터
npm run test       # 테스트
```
-->

<!-- 필요한 환경 변수:
- `.env`에 필요한 변수를 여기에 기재
-->

## 프로젝트 구조

<!-- 프로젝트의 주요 폴더 구조를 설명. 예시:
```
src/
docs/
tests/
wisdom/
workplan/
```
-->

## 코드 규칙

- 들여쓰기: 공백 2칸
- 코드는 영어, 문서와 주석은 한국어

<!-- 추가 팀 규칙을 정의. 예시:
- 네이밍: 변수는 camelCase, 컴포넌트는 PascalCase
- 엄격한 TypeScript
-->

## 지식 베이스 (wisdom/)

`wisdom/` 폴더는 프로젝트의 기술 문서를 포함합니다. 시스템의 작동 방식을 이해하기 위한 신뢰할 수 있는 정보원입니다.

기본 구조:
- `wisdom/architecture/` — 시스템 설계 방식 (의사결정, 패턴, 구조)
- `wisdom/development/` — 프로젝트 작업 방법 (규칙, 테스트, 워크플로)
- `wisdom/operations/` — 배포 및 운영 방법 (CI/CD, 환경, 모니터링)

프로젝트에 필요한 경우 추가 폴더(`database/`, `security/`, `integrations/`)를 생성할 수 있습니다. 기준은 `wisdom/README.md`를 참조하세요.

기존 아키텍처나 패턴에 영향을 미치는 결정을 내리기 전에 에이전트는 `wisdom/`를 참조해야 합니다.

## 계획 관리 (workplan/)

`workplan/` 폴더는 프로젝트 작업의 생명주기를 관리합니다.

**폴더:**
- `backlog/` — 대기 중인 계획, 우선순위 지정 및 작업 준비 완료
- `coding/` — 진행 중인 계획
- `done/` — 완료된 계획 (이력 보관)
- `draft/` — 초안, 아이디어, 아키텍처 결정 (워크플로나 식별자 없음)

**워크플로:** `(draft/) -> backlog/ -> coding/ -> done/`

**파일 명명 형식:**
- 이슈 트래커 사용: `TYPE-YYYY-MM-DD-iNNNN-description.md`
- 이슈 트래커 미사용: `TYPE-YYYY-MM-DD-description.md`
- TYPE: `BACKLOG`, `CODING`, `DONE`
- iNNNN: GitHub/GitLab 이슈 번호 (트래커 설정 시)

전체 템플릿과 상세 규칙은 `workplan/README.md`를 참조하세요.

## 인증 및 역할

<!-- 인증 및 역할 시스템을 정의. 예시:
- 인증 제공자:
- 역할 계층:
- 권한 확인용 Composable/함수:
-->

## Git 워크플로

- 메인 브랜치: `main` (PR 필수)
- 브랜치: `feature/`, `fix/`, `hotfix/`, `refactor/`, `chore/`, `docs/` + 영어로 설명
- 커밋: 영어로 Conventional Commits (`feat:`, `fix:`, `docs:` 등)
- PR: 영어로 제목 (Conventional Commits), 한국어로 설명/body
- 이슈: 한국어로 제목과 설명
- 커밋에 AI 에이전트의 **`Co-Authored-By`를 포함하지 않음**
- 커밋 메시지나 PR에 **"Generated with Claude Code" 링크를 포함하지 않음**

<!-- 필요에 따라 Git 워크플로 규칙 추가 -->

## 테스트

<!-- 테스트 전략을 정의. 예시:
- 테스트 프레임워크:
- 테스트가 필요한 항목:
- 파일 패턴: `*.test.ts` 또는 `*.spec.ts`
-->

## 보호 영역 (수정 금지)

<!-- 에이전트가 수정해서는 안 되는 파일 또는 폴더를 기재. 예시:
| 파일 | 이유 |
|------|------|
| `.env` | 커밋 금지 |
| `migrations/` (적용됨) | 새로운 것을 생성 |
-->

## 알려진 주의사항

<!-- 알려진 문제나 일반적인 함정을 기록. 예시:
- 버그 X: 설명 및 해결 방법
- 제한 Y: 배경 및 임시 해결책
-->

## 상세 사양

<!-- wisdom/ 내 참고 문서 링크를 기재. 예시:
| 문서 | 내용 |
|------|------|
| [wisdom/architecture/...](wisdom/architecture/...) | 시스템 아키텍처 |
| [wisdom/database/...](wisdom/database/...) | DB 스키마 및 규칙 |
-->
