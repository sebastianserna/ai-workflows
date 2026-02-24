# 프로젝트 이름

프로젝트에 대한 간략한 설명.

## 요구 사항

<!-- 시스템 요구 사항 기재: Node.js, Python, Docker 등 -->

## 설치

```bash
# 저장소 클론
git clone <저장소-URL>
cd <프로젝트-이름>

# 의존성 설치
# npm install / pip install / etc.

# 환경 변수 설정
cp .env.example .env
```

## 개발

```bash
# 개발 서버 시작
# npm run dev / python manage.py runserver / etc.
```

## 프로젝트 구조

```
AGENTS.md               # AI 에이전트 가이드
CLAUDE.md               # Claude Code 설정
README.md               # 이 파일
wisdom/                 # 지식 베이스 (아키텍처, 가이드)
workplan/               # 작업 계획 관리
├── backlog/            #   대기 중인 계획
├── coding/             #   진행 중
├── done/               #   완료
└── draft/              #   초안 및 아이디어
```

## AI 에이전트와의 협업

이 프로젝트는 Claude Code와 같은 AI 에이전트와 함께 작업할 수 있도록 설정되어 있습니다:

- **AGENTS.md** — 에이전트가 프로젝트를 이해하기 위한 완전한 가이드
- **CLAUDE.md** — Claude Code 시작 시 자동으로 로드되는 진입점
- **wisdom/** — 에이전트가 의사결정 시 참고하는 기술 문서
- **workplan/** — 에이전트가 읽고 업데이트할 수 있는 작업 관리 시스템

## 라이선스

<!-- 선택한 라이선스로 교체하세요 -->
The MIT License (MIT)

Copyright (c) <연도> - <저자>

이 저장소의 소스 코드는 Claude, GPT, Gemini 등의 고급 언어 모델(LLM)을 기반으로 하는 인공지능 도구의 지원을 받아 부분적으로 또는 전체적으로 작성되었습니다. 이러한 도구의 사용은 프로젝트 저자에 의해 신중하게 안내되고 감독되었습니다.
