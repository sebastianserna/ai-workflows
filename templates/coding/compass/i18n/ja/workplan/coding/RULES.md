# ルール：coding/

> アクティブに作業中の計画。

## このフォルダの内容

- 現在進行中の計画
- アクティブに実装されている計画のみ

## 命名規則

**Issueトラッカーあり（GitHub / GitLab）：**

```
CODING-YYYY-MM-DD-iNNNN-description.md
```

**Issueトラッカーなし：**

```
CODING-YYYY-MM-DD-description.md
```

日付は作業開始日を反映します。

## 主要ルール

- 各計画には `state: "coding"` を含むYAML frontmatterが必要（形式は `workplan/README.md` を参照）
- ステップの完了に伴い進捗チェックボックスを更新
- 完了時：`done/` に移動、プレフィックスを `DONE` に変更、日付とfrontmatterを更新
- 一時停止時：`backlog/` に戻し、プレフィックスを `BACKLOG` に変更、frontmatterを更新
- 完全なリファレンスは `workplan/README.md` を参照

## 関連項目

- `backlog/RULES.md` — 未着手の計画のルール
- `done/RULES.md` — 完了した計画のルール
- `draft/RULES.md` — 下書きとアイデアのルール
