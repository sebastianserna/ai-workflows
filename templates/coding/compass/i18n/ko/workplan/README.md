# 계획 관리

> **이 파일은 계획 관리의 신뢰할 수 있는 정보원입니다.** AI 에이전트는 계획을 생성, 이동 또는 수정할 때 이 지침을 따라야 합니다.

## 설정

**이슈 트래커:** none
<!-- 옵션: GitHub | GitLab | none -->
<!-- 활성화: "GitHub" 또는 "GitLab"으로 변경하고 저장소 설정 -->

**저장소:** `사용자명/저장소명`

## 파일 명명 형식

명명 형식은 이슈 트래커 설정 여부에 따라 달라집니다:

**이슈 트래커 사용 (GitHub / GitLab):**

```
TYPE-YYYY-MM-DD-iNNNN-description.md
```

**이슈 트래커 미사용 (none):**

```
TYPE-YYYY-MM-DD-description.md
```

| 세그먼트 | 설명 | 예시 |
|----------|------|------|
| `TYPE` | 상태: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | 현재 상태로의 전환 날짜 | `2026-01-15` |
| `iNNNN` | 이슈 번호, 4자리 제로패딩에 `i` 접두사 (트래커 설정 시에만) | `i0060` |
| `description` | kebab-case 짧은 이름 | `user-auth-setup` |

### 이슈 식별자 (`iNNNN`)

이슈 트래커가 설정된 경우 (GitHub 또는 GitLab), 각 계획은 해당하는 이슈가 **필수**입니다. 이슈 번호가 계획의 고유 식별자가 됩니다:

- `i` 접두사는 이슈 번호를 다른 숫자 세그먼트와 구분합니다
- 4자리 제로패딩: 이슈 #7 → `i0007`, 이슈 #123 → `i0123`
- 식별자는 **영구적**입니다 — 계획이 상태 간 이동해도 변경되지 않습니다
- GitHub/GitLab이 원자적 고유성을 보장하여 협업 환경에서의 충돌 위험을 제거합니다

**이슈 트래커가 "none"인 경우**, 계획에는 식별자 세그먼트가 없습니다. 파일 이름은 단순히 `TYPE-YYYY-MM-DD-description.md`입니다.

### 날짜 규칙

파일 이름의 날짜는 현재 상태로의 전환을 반영합니다:

| 상태 | 파일 이름의 날짜 = |
|------|-------------------|
| BACKLOG | 계획 생성 날짜 |
| CODING | 작업 시작 날짜 |
| DONE | 완료 날짜 |

## 폴더 구조

```
workplan/
├── README.md          # 이 파일 (신뢰할 수 있는 정보원)
├── backlog/           # 대기 중인 계획
│   └── RULES.md
├── coding/            # 진행 중인 작업
│   └── RULES.md
├── done/              # 완료된 계획 (보관)
│   └── RULES.md
└── draft/             # 초안, 아이디어, 결정 (상태 워크플로 없음)
    └── RULES.md
```

각 `RULES.md`에는 폴더별 규칙과 명명 규칙이 포함되어 있습니다:

- `backlog/RULES.md` — 새 계획의 진입점, 이슈 생성 지침
- `coding/RULES.md` — 활성 작업, 전환 및 진행 규칙
- `done/RULES.md` — 보관, 완료 기준
- `draft/RULES.md` — 아이디어 뱅크, 워크플로 없음, 이슈 식별자 없음

## YAML Frontmatter

각 계획 파일은 **1행**에서 YAML frontmatter 블록으로 시작해야 합니다 (시작 `---` 앞에 빈 줄 없음). GitHub은 이를 메타데이터 테이블로 렌더링합니다.

```yaml
---
plan: "설명적인 제목"
state: "backlog"
issue: ""
domain: "general"
backlog: "2026-01-15"
coding: ""
done: ""
---
```

**Frontmatter 필드:**

| 필드 | 설명 | 값 |
|------|------|-----|
| `plan` | 간결한 설명적 제목 | 자유 텍스트 |
| `state` | 현재 상태 (파일 이름 접두사와 일치해야 함) | `backlog`, `coding`, `done`, `draft` |
| `issue` | 이슈 식별자 (`iNNNN`) 또는 비어 있음 | `"i0060"`, `""` |
| `domain` | 기능 도메인 | `general`, 또는 프로젝트별 |
| `backlog` | 계획 생성 날짜 | `"2026-01-15"`, `""` |
| `coding` | 작업 시작 날짜 | `"2026-01-20"`, `""` |
| `done` | 완료 날짜 | `"2026-02-01"`, `""` |

**Frontmatter 규칙:**
- 첫 번째 `---`는 정확히 1행에 위치해야 하며 앞에 빈 줄이 없어야 함
- `state` 값은 파일 이름 접두사와 일치해야 함 (소문자)
- 이슈 트래커가 "none"인 경우 **issue**는 `""`
- 트래커가 활성화된 경우 **issue**에 식별자 포함: `"i0060"`
- 초안은 `issue`와 날짜 필드를 완전히 생략
- 날짜 필드는 각 전환이 발생한 시점을 기록 (`""`은 아직 도달하지 않은 경우)

## 표준 템플릿

### 필수 용어

| 용어 | 사용 | 예시 |
|------|------|------|
| **단계** | 주요 구현 마일스톤 | 단계 1: MVP, 단계 2: 개선 |
| **스텝** | 진행 체크리스트의 구체적인 항목 | `- [ ] SQL 마이그레이션 생성` |

### 섹션 순서

Frontmatter → 진행 → 목표 → 배경 → 구현 → 검증 → 리스크

선택적 섹션은 비워두지 않고 **생략**합니다.

### 템플릿

```markdown
---
plan: "설명적인 제목"
state: "backlog"
issue: ""
domain: "general"
backlog: "YYYY-MM-DD"
coding: ""
done: ""
---

## 진행

### 단계 1: MVP
- [ ] 구체적이고 검증 가능한 스텝
- [ ] 다른 스텝

### 단계 2: 개선 *(해당하는 경우)*
- [ ] 구체적이고 검증 가능한 스텝

## 목표

무엇을 달성하고 싶은지, 왜인지 (1-3 단락).

## 배경 *(선택)*

현재 상태, 전제 조건.

## 구현

### 단계 1: MVP

구현의 기술적 세부사항.

### 단계 2: 개선 *(선택)*

## 검증 *(선택)*

계획이 올바르게 완료되었는지 확인하는 절차.

## 리스크 *(선택)*

복잡한 계획에만 해당.
```

### 규칙

1. **진행은 항상 frontmatter 바로 뒤에**, 끝에 두지 않음
2. 스텝은 단계별로 그룹화 (`### 단계 N: 이름`)
3. 각 스텝은 구체적이고 검증 가능해야 함 (모호하지 않게)
4. 기술적 세부사항은 구현에, 요약은 진행에 기재
5. "단계"와 "스텝"만 사용
6. 선택적 섹션은 비워두지 않고 생략

## 워크플로

### 계획 생성

**이슈 트래커 사용:**

1. 먼저 이슈 생성: `gh issue create` (GitHub) 또는 `glab issue create` (GitLab)
2. 이슈 번호 기록 (예: #60)
3. `backlog/BACKLOG-YYYY-MM-DD-iNNNN-description.md`에 파일 생성 (예: `BACKLOG-2026-01-15-i0060-user-auth-setup.md`)
4. frontmatter의 `issue` 필드에 식별자 기입

**이슈 트래커 미사용:**

1. `backlog/BACKLOG-YYYY-MM-DD-description.md`에 파일 생성

### 작업 시작

1. `backlog/`에서 `coding/CODING-YYYY-MM-DD-...-description.md`로 이동 (날짜 = 오늘, 식별자 변경 없음)
2. frontmatter 업데이트: `state: "coding"`, `coding: "YYYY-MM-DD"`

### 완료

1. `coding/`에서 `done/DONE-YYYY-MM-DD-...-description.md`로 이동 (날짜 = 오늘)
2. frontmatter 업데이트: `state: "done"`, `done: "YYYY-MM-DD"`

### backlog으로 되돌리기

1. `coding/`에서 `backlog/BACKLOG-YYYY-MM-DD-...-description.md`로 이동
2. frontmatter 업데이트: `state: "backlog"`, `coding: ""`

## 상호 참조

**이슈 트래커 사용:** 계획 간 참조에는 이슈 번호 `#N`을 사용합니다. 이는 영구적이며 자동 링크가 지원됩니다:

```markdown
**의존성:** #1, #2

자세한 내용은 #3을 참조.
```

**이슈 트래커 미사용:** 설명적인 이름으로 계획을 참조합니다:

```markdown
**의존성:** user-auth-setup, api-rate-limiting
```

**규칙:** 전체 파일 이름으로 계획을 참조하지 않음 (전환마다 변경됨).

## 초안 (드래프트)

초안은 `draft/`에 `DRAFT-YYYY-MM-DD-description.md` 형식으로 저장됩니다. BACKLOG→CODING→DONE 워크플로를 따르지 않으며 이슈 식별자가 없습니다. 아이디어 뱅크 역할을 합니다: 계획 초안, 기술적 결정, 탐색적 메모. 초안이 충분히 성숙하면 `backlog/`에 정식 계획으로 승격됩니다.
