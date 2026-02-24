# ルール：backlog/

> 作業待ちの未着手計画。

## このフォルダの内容

- 定義済みで開始準備ができている計画（または優先順位待ち）
- 新しい計画は作成後ここに入る

## 命名規則

**Issueトラッカーあり（GitHub / GitLab）：**

```
BACKLOG-YYYY-MM-DD-iNNNN-description.md
```

**Issueトラッカーなし：**

```
BACKLOG-YYYY-MM-DD-description.md
```

日付は計画が作成された日を反映します。

## 主要ルール

- 各計画には `状態：Backlog` を含む標準ヘッダーが必要
- **Issueトラッカーが設定されている場合**、まずIssueを作成（`gh issue create`、`glab issue create` 等）し、ファイル名にIssue番号を使用（`iNNNN`）
- 作業開始時：`coding/` に移動、プレフィックスを `CODING` に変更、日付とヘッダーを更新
- 計画は一時停止の場合 `coding/` からここに戻すこともできる
- 完全なリファレンスは `workplan/README.md` を参照

## 関連項目

- `coding/RULES.md` — 進行中の計画のルール
- `done/RULES.md` — 完了した計画のルール
- `draft/RULES.md` — 下書きとアイデアのルール
