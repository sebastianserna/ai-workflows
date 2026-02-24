# AGENTS.md

本プロジェクトで作業するAIエージェント向けガイド。

<!-- 言語：エージェントの応答言語とコードの言語をここで定義 -->

## 技術スタック

<!-- プロジェクトの技術スタックをここに定義。例：
- フレームワーク：
- UI：
- バックエンド/DB：
- 言語：
-->

## セットアップとコマンド

<!-- プロジェクトの基本コマンド。例：
```bash
npm install        # 依存関係のインストール
npm run dev        # 開発サーバー
npm run build      # 本番ビルド
npm run lint       # リンター
npm run test       # テスト
```
-->

<!-- 必要な環境変数：
- `.env` に必要な変数をここに記載
-->

## プロジェクト構成

<!-- プロジェクトの主なフォルダ構成を記述。例：
```
src/
docs/
tests/
wisdom/
workplan/
```
-->

## コード規約

- インデント：スペース2つ
- コードは英語、ドキュメントとコメントは日本語

<!-- その他のチーム規約を追加。例：
- 命名：変数はcamelCase、コンポーネントはPascalCase
- TypeScript厳格モード
-->

## ナレッジベース（wisdom/）

`wisdom/` フォルダにはプロジェクトの技術ドキュメントが含まれています。システムの仕組みを理解するための信頼できる情報源です。

基本構成：
- `wisdom/architecture/` — システムの設計方法（決定事項、パターン、構造）
- `wisdom/development/` — プロジェクトでの作業方法（規約、テスト、ワークフロー）
- `wisdom/operations/` — デプロイと運用方法（CI/CD、環境、監視）

プロジェクトの必要に応じて、追加フォルダ（`database/`、`security/`、`integrations/`）を作成できます。基準は `wisdom/README.md` を参照してください。

既存のアーキテクチャやパターンに影響する決定を行う前に、エージェントは `wisdom/` を参照すべきです。

## 計画管理（workplan/）

`workplan/` フォルダはプロジェクトタスクのライフサイクルを管理します。

**フォルダ：**
- `backlog/` — 未着手の計画（優先順位付け済み、作業準備完了）
- `coding/` — 進行中の計画
- `done/` — 完了した計画（履歴アーカイブ）
- `draft/` — 下書き、アイデア、アーキテクチャ決定事項（ワークフローや識別子なし）

**ワークフロー：** `backlog/ -> coding/ -> done/`

**ファイル命名規則：**
- Issueトラッカーあり：`TYPE-YYYY-MM-DD-iNNNN-description.md`
- Issueトラッカーなし：`TYPE-YYYY-MM-DD-description.md`
- TYPE：`BACKLOG`、`CODING`、`DONE`
- iNNNN：GitHub/GitLabのIssue番号（トラッカー設定時）

完全なテンプレートと詳細ルールは `workplan/README.md` を参照してください。

## 認証とロール

<!-- 認証とロールシステムを定義。例：
- 認証プロバイダー：
- ロール階層：
- 権限チェック用のComposable/関数：
-->

## Gitワークフロー

- メインブランチ：`main`（PR必須）
- ブランチ：`feature/`、`fix/`、`hotfix/`、`refactor/`、`chore/`、`docs/` + 英語での説明
- コミット：英語でのConventional Commits（`feat:`、`fix:`、`docs:` など）
- PR：英語でのタイトル（Conventional Commits）、日本語での説明/body
- Issue：日本語でのタイトルと説明
- コミットにAIエージェントの **`Co-Authored-By`を含めない**
- コミットメッセージやPRに **「Generated with Claude Code」リンクを含めない**

<!-- 必要に応じてGitワークフローのルールを追加 -->

## テスト

<!-- テスト戦略を定義。例：
- テストフレームワーク：
- テストが必要なもの：
- ファイルパターン：`*.test.ts` または `*.spec.ts`
-->

## 保護ゾーン（変更禁止）

<!-- エージェントが変更してはいけないファイルやフォルダを記載。例：
| ファイル | 理由 |
|----------|------|
| `.env` | コミット禁止 |
| `migrations/`（適用済み） | 新しいものを作成する |
-->

## 既知の注意点

<!-- 既知の問題や一般的な落とし穴を記録。例：
- バグ X：説明と回避策
- 制限 Y：背景と一時的な解決策
-->

## 詳細仕様

<!-- wisdom/ 内の参考ドキュメントへのリンクを記載。例：
| ドキュメント | 内容 |
|------------|------|
| [wisdom/architecture/...](wisdom/architecture/...) | システムアーキテクチャ |
| [wisdom/database/...](wisdom/database/...) | DBスキーマと規約 |
-->
