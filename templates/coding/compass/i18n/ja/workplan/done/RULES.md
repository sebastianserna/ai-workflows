# ルール：done/

> 完了した計画 — アーカイブと参照。

## このフォルダの内容

- 完全に実装・検証された計画
- このフォルダは履歴記録として機能する

## 命名規則

**Issueトラッカーあり（GitHub / GitLab）：**

```
DONE-YYYY-MM-DD-iNNNN-description.md
```

**Issueトラッカーなし：**

```
DONE-YYYY-MM-DD-description.md
```

日付は計画が完了した日を反映します。

## 主要ルール

- 各計画には `state: "done"` を含むYAML frontmatterが必要（形式は `workplan/README.md` を参照）
- すべての進捗チェックボックスがチェック済みであること
- 完了した計画は原則として変更しない
- 完全なリファレンスは `workplan/README.md` を参照

## 関連項目

- `backlog/RULES.md` — 未着手の計画のルール
- `coding/RULES.md` — 進行中の計画のルール
- `draft/RULES.md` — 下書きとアイデアのルール
