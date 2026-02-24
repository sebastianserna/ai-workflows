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

## ライセンス

<!-- 選択したライセンスに置き換えてください -->
The MIT License (MIT)

Copyright (c) <年> - <著者>

このリポジトリのソースコードは、Claude、GPT、Geminiなどの高度な言語モデル（LLM）を搭載した人工知能ツールの支援により、部分的または全体的に作成されました。これらのツールの使用は、プロジェクトの著者によって慎重にガイドおよび監督されています。
