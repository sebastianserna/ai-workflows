# 計画管理

> **このファイルは計画管理の信頼できる情報源です。** AIエージェントは計画の作成、移動、変更時にこれらの指示に従ってください。

## 設定

**Issueトラッカー：** none
<!-- オプション：GitHub | GitLab | none -->
<!-- 有効化：「GitHub」または「GitLab」に変更してリポジトリを設定 -->

**リポジトリ：** `ユーザー名/リポジトリ名`

## ファイル命名規則

命名規則はIssueトラッカーの設定に依存します：

**Issueトラッカーあり（GitHub / GitLab）：**

```
TYPE-YYYY-MM-DD-iNNNN-description.md
```

**Issueトラッカーなし（none）：**

```
TYPE-YYYY-MM-DD-description.md
```

| セグメント | 説明 | 例 |
|-----------|------|-----|
| `TYPE` | 状態：`BACKLOG`、`CODING`、`DONE`、`DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | 現在の状態への遷移日 | `2026-01-15` |
| `iNNNN` | Issue番号、4桁ゼロパディングに`i`プレフィックス付き（トラッカー設定時のみ） | `i0060` |
| `description` | kebab-caseの短い名前 | `user-auth-setup` |

### Issue識別子（`iNNNN`）

Issueトラッカーが設定されている場合（GitHubまたはGitLab）、各計画にはそれに対応するIssueが**必須**です。Issue番号が計画の一意の識別子となります：

- `i`プレフィックスはIssue番号を他の数値セグメントと区別します
- 4桁にゼロパディング：Issue #7 → `i0007`、Issue #123 → `i0123`
- 識別子は**永続的**です — 計画が状態間を移動しても変わりません
- GitHub/GitLabがアトミックな一意性を保証し、協業環境での衝突リスクを排除します

**Issueトラッカーが「none」の場合**、計画には識別子セグメントがありません。ファイル名は単に `TYPE-YYYY-MM-DD-description.md` となります。

### 日付ルール

ファイル名の日付は現在の状態への遷移を反映します：

| 状態 | ファイル名の日付 = |
|------|-------------------|
| BACKLOG | 計画の作成日 |
| CODING | 作業開始日 |
| DONE | 完了日 |

## フォルダ構成

```
workplan/
├── README.md          # このファイル（信頼できる情報源）
├── backlog/           # 未着手の計画
│   └── RULES.md
├── coding/            # 進行中の作業
│   └── RULES.md
├── done/              # 完了した計画（アーカイブ）
│   └── RULES.md
└── draft/             # 下書き、アイデア、決定事項（状態ワークフローなし）
    └── RULES.md
```

各 `RULES.md` には、フォルダ固有のルールと命名規則が含まれています：

- `backlog/RULES.md` — 新しい計画のエントリポイント、Issue作成の手順
- `coding/RULES.md` — アクティブな作業、遷移と進捗のルール
- `done/RULES.md` — アーカイブ、完了基準
- `draft/RULES.md` — アイデアバンク、ワークフローなし、Issue識別子なし

## YAML Frontmatter

各計画ファイルは**1行目**にYAML frontmatterブロックで始める必要があります（開始の `---` の前に空行を入れない）。GitHubはこれをメタデータテーブルとしてレンダリングします。

```yaml
---
plan: "説明的なタイトル"
state: "backlog"
issue: ""
domain: "general"
backlog: "2026-01-15"
coding: ""
done: ""
---
```

**Frontmatterフィールド：**

| フィールド | 説明 | 値 |
|-----------|------|-----|
| `plan` | 簡潔な説明的タイトル | 自由テキスト |
| `state` | 現在の状態（ファイル名プレフィックスと一致する必要あり） | `backlog`、`coding`、`done`、`draft` |
| `issue` | Issue識別子（`iNNNN`）または空 | `"i0060"`、`""` |
| `domain` | 機能ドメイン | `general`、またはプロジェクト固有 |
| `backlog` | 計画の作成日 | `"2026-01-15"`、`""` |
| `coding` | 作業開始日 | `"2026-01-20"`、`""` |
| `done` | 完了日 | `"2026-02-01"`、`""` |

**Frontmatterルール：**
- 最初の `---` は正確に1行目に配置し、前に空行を入れない
- `state` の値はファイル名プレフィックスと一致する必要がある（小文字）
- Issueトラッカーが "none" の場合、**issue** は `""`
- トラッカーが有効な場合、**issue** に識別子を含める：`"i0060"`
- 下書きは `issue` と日付フィールドを完全に省略する
- 日付フィールドは各遷移が発生した時点を記録する（`""` はまだ到達していない場合）

## 標準テンプレート

### 必須用語

| 用語 | 使い方 | 例 |
|------|--------|-----|
| **フェーズ** | 主要な実装マイルストーン | フェーズ 1：MVP、フェーズ 2：改善 |
| **ステップ** | 進捗チェックリストの具体的な項目 | `- [ ] SQLマイグレーションを作成` |

### セクション順序

Frontmatter → 進捗 → 目的 → コンテキスト → 実装 → 検証 → リスク

オプションのセクションは空にせず、**省略**します。

### テンプレート

```markdown
---
plan: "説明的なタイトル"
state: "backlog"
issue: ""
domain: "general"
backlog: "YYYY-MM-DD"
coding: ""
done: ""
---

## 進捗

### フェーズ 1：MVP
- [ ] 具体的で検証可能なステップ
- [ ] 別のステップ

### フェーズ 2：改善 *（該当する場合）*
- [ ] 具体的で検証可能なステップ

## 目的

何を達成したいか、なぜか（1〜3段落）。

## コンテキスト *（任意）*

現状、前提条件。

## 実装

### フェーズ 1：MVP

実装の技術的詳細。

### フェーズ 2：改善 *（任意）*

## 検証 *（任意）*

計画が正しく完了したことを検証する手順。

## リスク *（任意）*

複雑な計画のみ。
```

### ルール

1. **進捗は常にfrontmatterの直後**、末尾には置かない
2. ステップはフェーズごとにグループ化（`### フェーズ N：名前`）
3. 各ステップは具体的で検証可能であること（曖昧にしない）
4. 技術的詳細は実装に、概要は進捗に記載
5. 「フェーズ」と「ステップ」のみ使用
6. オプションのセクションは空にせず、省略する

## ワークフロー

### 計画の作成

**Issueトラッカーあり：**

1. まずIssueを作成：`gh issue create`（GitHub）または `glab issue create`（GitLab）
2. Issue番号を記録（例：#60）
3. `backlog/BACKLOG-YYYY-MM-DD-iNNNN-description.md` にファイルを作成（例：`BACKLOG-2026-01-15-i0060-user-auth-setup.md`）
4. frontmatterの `issue` フィールドに識別子を記入

**Issueトラッカーなし：**

1. `backlog/BACKLOG-YYYY-MM-DD-description.md` にファイルを作成

### 作業開始

1. `backlog/` から `coding/CODING-YYYY-MM-DD-...-description.md` に移動（日付 = 今日、識別子変更なし）
2. frontmatterを更新：`state: "coding"`、`coding: "YYYY-MM-DD"`

### 完了

1. `coding/` から `done/DONE-YYYY-MM-DD-...-description.md` に移動（日付 = 今日）
2. frontmatterを更新：`state: "done"`、`done: "YYYY-MM-DD"`

### backlogに戻す

1. `coding/` から `backlog/BACKLOG-YYYY-MM-DD-...-description.md` に移動
2. frontmatterを更新：`state: "backlog"`、`coding: ""`

## 相互参照

**Issueトラッカーあり：** 計画間の参照にはIssue番号 `#N` を使用します。これは永続的で自動リンクが有効です：

```markdown
**依存関係：** #1、#2

詳細は #3 を参照。
```

**Issueトラッカーなし：** 説明的な名前で計画を参照します：

```markdown
**依存関係：** user-auth-setup、api-rate-limiting
```

**ルール：** 完全なファイル名での参照は禁止（遷移ごとに変わるため）。

## 下書き（ドラフト）

下書きは `draft/` に `DRAFT-YYYY-MM-DD-description.md` の形式で保存されます。BACKLOG→CODING→DONEのワークフローには従わず、Issue識別子もありません。アイデアバンクとして機能します：計画の下書き、技術的決定事項、探索的メモ。下書きが十分に成熟したら、`backlog/` に正式な計画として昇格させます。
