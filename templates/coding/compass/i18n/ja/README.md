# プロジェクト名

プロジェクトの簡単な説明。

## 必要要件

<!-- システム要件を記載：Node.js、Python、Docker など -->

## インストール

```bash
# リポジトリをクローン
git clone <リポジトリURL>
cd <プロジェクト名>

# 依存関係のインストール
# npm install / pip install / etc.

# 環境変数の設定
cp .env.example .env
```

## 開発

```bash
# 開発サーバーの起動
# npm run dev / python manage.py runserver / etc.
```

## プロジェクト構成

```
AGENTS.md               # AIエージェント向けガイド
CLAUDE.md               # Claude Code設定
README.md               # このファイル
wisdom/                 # ナレッジベース（アーキテクチャ、ガイド）
workplan/               # 作業計画管理
├── backlog/            #   未着手の計画
├── coding/             #   進行中
├── done/               #   完了済み
└── draft/              #   下書きとアイデア
```

## AIエージェントとの協働

このプロジェクトはClaude CodeなどのAIエージェントと連携できるよう設定されています：

- **AGENTS.md** — エージェントがプロジェクトを理解するための完全ガイド
- **CLAUDE.md** — Claude Code起動時に自動読み込みされるエントリーポイント
- **wisdom/** — エージェントが意思決定時に参照する技術ドキュメント
- **workplan/** — エージェントが読み書きできるタスク管理システム
