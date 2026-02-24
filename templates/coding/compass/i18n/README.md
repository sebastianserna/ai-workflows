# i18n — Localized templates

This folder contains translated versions of the template files. The root of the repository contains the **English (default)** version.

## Available languages

| Code | Language | Folder |
|------|----------|--------|
| `en` | English | Root (default) |
| `es` | Español (Spanish) | [`i18n/es/`](es/) |
| `fr` | Français (French) | [`i18n/fr/`](fr/) |
| `it` | Italiano (Italian) | [`i18n/it/`](it/) |
| `zh` | 中文 (Chinese) | [`i18n/zh/`](zh/) |
| `ja` | 日本語 (Japanese) | [`i18n/ja/`](ja/) |
| `ko` | 한국어 (Korean) | [`i18n/ko/`](ko/) |
| `pt` | Português (Portuguese-BR) | [`i18n/pt/`](pt/) |
| `de` | Deutsch (German) | [`i18n/de/`](de/) |
| `hi` | हिन्दी (Hindi) | [`i18n/hi/`](hi/) |
| `ru` | Русский (Russian) | [`i18n/ru/`](ru/) |

## How to use a translated version

Each language folder mirrors the root structure. To use a specific language, copy the files from the desired language folder to the root of your project:

```bash
# Example: use the Spanish version
cp -r i18n/es/* .
```

This will overwrite the English template files with the translated versions.

## Structure of each language folder

```
i18n/<lang>/
├── AGENTS.md
├── CLAUDE.md
├── README.md
├── wisdom/
│   ├── README.md
│   ├── architecture/
│   │   ├── AGENTS.md
│   │   └── system-overview.md
│   ├── development/
│   │   ├── AGENTS.md
│   │   └── getting-started.md
│   └── operations/
│       ├── AGENTS.md
│       └── deployment.md
└── workplan/
    ├── README.md
    ├── backlog/
    │   ├── RULES.md
    │   └── BACKLOG-YYYY-MM-DD-0000-example-template.md
    ├── coding/
    │   ├── RULES.md
    │   └── CODING-YYYY-MM-DD-0000-example-template.md
    ├── done/
    │   ├── RULES.md
    │   └── DONE-YYYY-MM-DD-0000-example-template.md
    └── draft/
        ├── RULES.md
        └── DRAFT-YYYY-MM-DD-example-template.md
```

## Contributing a new language

1. Create a new folder with the [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) language code (e.g., `de/` for German)
2. Copy the English root files into the new folder
3. Translate all content, keeping the same file names and structure
4. Add the language to the table above
5. Submit a pull request

### Translation guidelines

- Keep all file names in English (they are part of the system convention)
- Keep technical keywords like `BACKLOG`, `CODING`, `DONE`, `DRAFT` untranslated (they are used as file prefixes)
- Keep `Phase` and `Step` terminology consistent within each language (see table below)
- Translate HTML comments (they serve as guidance for users filling in the template)
- Do not translate code examples or command names
- Header field names (`State`, `Backlog`, `Coding`, `Done`, `Domain`, `Issue`) should be translated to the target language
- Markdown structure (headings, tables, code blocks, checkboxes) must be preserved exactly

## Keeping translations in sync

The English files at the repository root are the **source of truth**. When they change, translations may become outdated.

### When modifying English source files

1. Note which files changed (e.g., `AGENTS.md`, `workplan/README.md`)
2. In the PR description, list the affected files under an **i18n impact** heading so reviewers are aware
3. Translations do not need to be updated in the same PR — but the need should be tracked

### How to track outdated translations

Each language folder may include an optional `SYNC.md` file to record the last sync state:

```markdown
# Translation sync status

| File | Last synced | English commit | Notes |
|------|------------|----------------|-------|
| AGENTS.md | 2026-02-19 | abc1234 | Up to date |
| workplan/README.md | 2026-02-19 | abc1234 | Up to date |
```

This file is optional — it's useful when the project has active contributors maintaining translations. If no `SYNC.md` exists, assume translations match the English version at the time they were added.

### Priority

Not all changes require immediate translation updates. Use this as a guide:

| Change type | Priority |
|-------------|----------|
| New section or file | High — missing content in translations |
| Structural change (renamed sections, reordered fields) | High — may break agent behavior |
| Wording improvement or clarification | Low — translations still functional |
| Comment/example updates | Low — cosmetic only |

### Terminology reference

Use this table to ensure consistency when translating key terms. New languages must define their equivalents before starting.

| English | es | fr | it | zh | ja | ko | pt | de | hi | ru |
|---------|----|----|----|----|----|----|----|----|----|----|
| Phase | Fase | Phase | Fase | 阶段 | フェーズ | 단계 | Fase | Phase | चरण | Фаза |
| Step | Paso | Étape | Passo | 步骤 | ステップ | 스텝 | Passo | Schritt | कदम | Шаг |
| Progress | Progreso | Progression | Avanzamento | 进度 | 進捗 | 진행 | Progresso | Fortschritt | प्रगति | Прогресс |
| Objective | Objetivo | Objectif | Obiettivo | 目标 | 目的 | 목표 | Objetivo | Ziel | उद्देश्य | Цель |
| Implementation | Implementación | Implémentation | Implementazione | 实施 | 実装 | 구현 | Implementação | Umsetzung | कार्यान्वयन | Реализация |
| Verification | Verificación | Vérification | Verifica | 验证 | 検証 | 검증 | Verificação | Überprüfung | सत्यापन | Проверка |
| Risks | Riesgos | Risques | Rischi | 风险 | リスク | 리스크 | Riscos | Risiken | जोखिम | Риски |
| State | Estado | État | Stato | 状态 | 状態 | 상태 | Estado | Status | स्थिति | Статус |
| Domain | Dominio | Domaine | Dominio | 领域 | ドメイン | 도메인 | Domínio | Bereich | डोमेन | Область |
| Knowledge base | Base de conocimiento | Base de connaissances | Base di conoscenza | 知识库 | ナレッジベース | 지식 베이스 | Base de conhecimento | Wissensbasis | ज्ञान आधार | База знаний |
| Source of truth | Fuente de verdad | Source de vérité | Fonte di verità | 权威来源 | 信頼できる情報源 | 신뢰할 수 있는 정보원 | Fonte da verdade | Maßgebliche Quelle | प्रामाणिक स्रोत | Источник истины |
| Draft | Borrador | Brouillon | Bozza | 草稿 | 下書き | 초안 | Rascunho | Entwurf | प्रारूप | Черновик |
