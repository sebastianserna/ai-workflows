# 计划管理

> **本文件是计划管理的权威来源。** AI 代理在创建、移动或修改计划时必须遵循以下说明。

## 配置

**Issue 跟踪器：** 无
<!-- 选项：GitHub | GitLab | 无 -->
<!-- 启用方式：改为 "GitHub" 或 "GitLab" 并配置仓库 -->

**仓库：** `用户名/仓库名`

## 文件命名格式

命名格式取决于是否配置了 Issue 跟踪器：

**使用 Issue 跟踪器（GitHub / GitLab）：**

```
TYPE-YYYY-MM-DD-iNNNN-description.md
```

**不使用 Issue 跟踪器（无）：**

```
TYPE-YYYY-MM-DD-description.md
```

| 字段 | 描述 | 示例 |
|------|------|------|
| `TYPE` | 状态：`BACKLOG`、`CODING`、`DONE`、`DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | 转换到当前状态的日期 | `2026-01-15` |
| `iNNNN` | Issue 编号，4 位补零加 `i` 前缀（仅在配置跟踪器时使用） | `i0060` |
| `description` | kebab-case 短名称 | `user-auth-setup` |

### Issue 标识符（`iNNNN`）

当配置了 Issue 跟踪器（GitHub 或 GitLab）时，每个计划**必须**有一个对应的 Issue。Issue 编号成为计划的唯一标识符：

- `i` 前缀用于区分 Issue 编号与其他数字字段
- 补零至 4 位：Issue #7 → `i0007`，Issue #123 → `i0123`
- 标识符是**永久的** — 即使计划在状态之间移动也不会改变
- GitHub/GitLab 保证原子唯一性，消除协作环境中的冲突风险

**当 Issue 跟踪器设为"无"时**，计划没有标识符字段。文件名格式为 `TYPE-YYYY-MM-DD-description.md`。

### 日期规则

文件名中的日期反映转换到当前状态的时间：

| 状态 | 文件名中的日期 = |
|------|------------------|
| BACKLOG | 计划创建日期 |
| CODING | 工作开始日期 |
| DONE | 完成日期 |

## 文件夹结构

```
workplan/
├── README.md          # 本文件（权威来源）
├── backlog/           # 待处理计划
├── coding/            # 进行中的工作
├── done/              # 已完成计划（归档）
└── draft/             # 草稿、想法和决策（无状态工作流）
```

## 标准化标题

```markdown
# 计划：描述性标题

**状态：** Backlog | Coding | Done
**Backlog：** 2026-01-15
**Coding：** —
**Done：** —
**领域：** 通用
**Issue：** —
```

**标题规则：**
- 状态必须与文件名前缀匹配
- 日期记录每次转换发生的时间（`—` 表示不适用）
- 如果 Issue 跟踪器配置为"无"，**Issue** 为 `—`
- 当跟踪器处于活动状态时，**Issue** 链接到 Issue：`[#60](https://github.com/user/repo/issues/60)`

## 标准模板

### 必须使用的术语

| 术语 | 用途 | 示例 |
|------|------|------|
| **阶段** | 主要实施里程碑 | 阶段 1：MVP，阶段 2：改进 |
| **步骤** | 进度检查清单中的具体项 | `- [ ] 创建 SQL 迁移` |

### 章节顺序

标题 → 进度 → 目标 → 背景 → 实施 → 验证 → 风险

可选章节应**省略**，不要留空。

### 模板

```markdown
# 计划：描述性标题

**状态：** Backlog
**Backlog：** YYYY-MM-DD
**Coding：** —
**Done：** —
**领域：** 通用
**Issue：** —

## 进度

### 阶段 1：MVP
- [ ] 具体、可验证的步骤
- [ ] 另一个步骤

### 阶段 2：改进 *（如适用）*
- [ ] 具体、可验证的步骤

## 目标

想要实现什么以及为什么（1-3 段）。

## 背景 *（可选）*

当前状态、前提条件。

## 实施

### 阶段 1：MVP

实施的技术细节。

### 阶段 2：改进 *（可选）*

## 验证 *（可选）*

验证计划正确完成的步骤。

## 风险 *（可选）*

仅用于复杂计划。
```

### 规则

1. **进度始终在标题之后**，绝不放在末尾
2. 步骤按阶段分组（`### 阶段 N：名称`）
3. 每个步骤必须具体且可验证（不要笼统）
4. 技术细节放在实施中，摘要放在进度中
5. 只使用"阶段"和"步骤"
6. 可选章节应省略，不要留空

## 工作流

### 创建计划

**使用 Issue 跟踪器：**

1. 首先创建 Issue：`gh issue create`（GitHub）或 `glab issue create`（GitLab）
2. 记录 Issue 编号（例如 #60）
3. 在 `backlog/BACKLOG-YYYY-MM-DD-iNNNN-description.md` 中创建文件（例如 `BACKLOG-2026-01-15-i0060-user-auth-setup.md`）
4. 在 `Issue` 标题字段中填写链接

**不使用 Issue 跟踪器：**

1. 在 `backlog/BACKLOG-YYYY-MM-DD-description.md` 中创建文件

### 开始工作

1. 从 `backlog/` 移动到 `coding/CODING-YYYY-MM-DD-...-description.md`（日期 = 今天，标识符不变）
2. 更新标题：`状态：Coding`，`Coding：YYYY-MM-DD`

### 完成

1. 从 `coding/` 移动到 `done/DONE-YYYY-MM-DD-...-description.md`（日期 = 今天）
2. 更新标题：`状态：Done`，`Done：YYYY-MM-DD`

### 退回到 backlog

1. 从 `coding/` 移动到 `backlog/BACKLOG-YYYY-MM-DD-...-description.md`
2. 更新标题：`状态：Backlog`

## 交叉引用

**使用 Issue 跟踪器：** 计划之间使用 Issue 编号 `#N` 相互引用，该编号是永久的并支持自动链接：

```markdown
**依赖：** #1、#2

详见 #3。
```

**不使用 Issue 跟踪器：** 使用描述性名称引用计划：

```markdown
**依赖：** user-auth-setup、api-rate-limiting
```

**规则：** 绝不使用完整文件名引用计划（每次转换都会改变）。

## 草稿

草稿存放在 `draft/` 中，格式为 `DRAFT-YYYY-MM-DD-description.md`。不遵循 BACKLOG→CODING→DONE 工作流，没有 Issue 标识符。作为想法库使用：计划草稿、技术决策、探索性笔记。当草稿足够成熟时，提升到 `backlog/` 成为正式计划。
