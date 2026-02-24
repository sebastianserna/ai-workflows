# 规则：backlog/

> 等待处理的待办计划。

## 放置内容

- 已定义并准备开始的计划（或等待优先级排序）
- 新计划创建后进入此处

## 命名

**使用 Issue 跟踪器（GitHub / GitLab）：**

```
BACKLOG-YYYY-MM-DD-iNNNN-description.md
```

**不使用 Issue 跟踪器：**

```
BACKLOG-YYYY-MM-DD-description.md
```

日期反映计划的创建时间。

## 关键规则

- 每个计划必须有 YAML frontmatter，包含 `state: "backlog"`（参见 `workplan/README.md` 了解格式）
- **如果配置了 Issue 跟踪器**，先创建 Issue（`gh issue create`、`glab issue create` 等），然后在文件名中使用 Issue 编号（`iNNNN`）
- 开始工作：移动到 `coding/`，将前缀重命名为 `CODING`，更新日期和标题
- 计划也可以从 `coding/` 暂停后退回到此处
- 参见 `workplan/README.md` 获取完整参考

## 另请参阅

- `coding/RULES.md` — 进行中计划的规则
- `done/RULES.md` — 已完成计划的规则
- `draft/RULES.md` — 草稿和想法的规则
