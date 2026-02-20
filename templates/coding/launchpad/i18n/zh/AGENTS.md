# AGENTS.md

本项目 AI 代理工作指南。

<!-- 语言：在此定义代理响应和代码使用的语言 -->

## 技术栈

<!-- 在此定义项目的技术栈。示例：
- 框架：
- UI：
- 后端/数据库：
- 编程语言：
-->

## 安装与命令

<!-- 项目基本命令。示例：
```bash
npm install        # 安装依赖
npm run dev        # 开发服务器
npm run build      # 生产构建
npm run lint       # 代码检查
npm run test       # 测试
```
-->

<!-- 所需环境变量：
- 在此列出 `.env` 中需要的变量
-->

## 项目结构

<!-- 描述项目的主要文件夹结构。示例：
```
src/
docs/
tests/
wisdom/
workplan/
```
-->

## 代码约定

<!-- 定义团队约定。示例：
- 缩进：2 个空格
- 命名：变量使用 camelCase，组件使用 PascalCase
- 严格 TypeScript
- 代码使用英文，文档使用中文
-->

## 知识库（wisdom/）

`wisdom/` 文件夹包含项目的技术文档，是理解系统运作方式的权威来源。

基础结构：
- `wisdom/architecture/` — 系统设计方式（决策、模式、结构）
- `wisdom/development/` — 项目开发方式（约定、测试、工作流）
- `wisdom/operations/` — 部署和运维方式（CI/CD、环境、监控）

当项目需要时，可以添加额外文件夹（`database/`、`security/`、`integrations/`）。详见 `wisdom/README.md` 中的标准。

代理在做出影响现有架构或模式的决策之前，应先查阅 `wisdom/`。

## 计划管理（workplan/）

`workplan/` 文件夹管理项目任务的生命周期。

**文件夹：**
- `backlog/` — 待处理计划，已排序并准备执行
- `coding/` — 正在进行的计划
- `done/` — 已完成的计划（历史归档）
- `draft/` — 草稿、想法和架构决策（无工作流或 ID）

**工作流：** `backlog/ -> coding/ -> done/`

**文件命名格式：** `TYPE-YYYY-MM-DD-NNNN-description.md`
- TYPE：`BACKLOG`、`CODING`、`DONE`
- NNNN：永久顺序 ID（在文件夹之间移动时不变）

详见 `workplan/README.md` 获取完整模板和详细规则。

## 认证与角色

<!-- 定义认证和角色系统。示例：
- 认证提供者：
- 角色层级：
- 权限检查的组合式函数/方法：
-->

## Git 工作流

<!-- 定义 Git 工作流。示例：
- 主分支：`main`
- 分支：`feature/`、`fix/`、`hotfix/`、`docs/` + 描述
- 提交：Conventional Commits（`feat:`、`fix:`、`docs:` 等）
- 合并到 main 需要 PR
-->

## 测试

<!-- 定义测试策略。示例：
- 测试框架：
- 需要测试的内容：
- 文件模式：`*.test.ts` 或 `*.spec.ts`
-->

## 受保护区域（禁止修改）

<!-- 列出代理不得修改的文件或文件夹。示例：
| 文件 | 原因 |
|------|------|
| `.env` | 禁止提交 |
| `migrations/`（已应用） | 应创建新的迁移 |
-->

## 已知问题

<!-- 记录已知问题或常见陷阱。示例：
- Bug X：描述和解决方法
- 限制 Y：背景和临时方案
-->

## 详细规范

<!-- 列出 wisdom/ 中参考文档的链接。示例：
| 文档 | 内容 |
|------|------|
| [wisdom/architecture/...](wisdom/architecture/...) | 系统架构 |
| [wisdom/database/...](wisdom/database/...) | 数据库结构和约定 |
-->
