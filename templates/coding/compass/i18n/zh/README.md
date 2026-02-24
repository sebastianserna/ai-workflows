# 项目名称

项目简要描述。

## 系统要求

<!-- 列出系统要求：Node.js、Python、Docker 等 -->

## 安装

```bash
# 克隆仓库
git clone <仓库地址>
cd <项目名称>

# 安装依赖
# npm install / pip install / etc.

# 配置环境变量
cp .env.example .env
```

## 开发

```bash
# 启动开发服务器
# npm run dev / python manage.py runserver / etc.
```

## 项目结构

```
AGENTS.md               # AI 代理指南
CLAUDE.md               # Claude Code 配置
README.md               # 本文件
wisdom/                 # 知识库（架构、指南）
workplan/               # 工作计划管理
├── backlog/            #   待处理计划
├── coding/             #   进行中
├── done/               #   已完成
└── draft/              #   草稿和想法
```

## 与 AI 代理协作

本项目已配置为与 Claude Code 等 AI 代理协同工作：

- **AGENTS.md** — 帮助代理理解项目的完整指南
- **CLAUDE.md** — 启动 Claude Code 时自动加载的入口文件
- **wisdom/** — 代理在决策时参考的技术文档
- **workplan/** — 代理可以读取和更新的任务管理系统

## 许可证

<!-- 替换为您选择的许可证 -->
The MIT License (MIT)

Copyright (c) <年份> - <作者>

本仓库的源代码部分或全部借助由 Claude、GPT、Gemini 等先进语言模型（LLM）驱动的人工智能工具创建。这些工具的使用由项目作者精心指导和监督。

---

基于 [Coding Compass](https://github.com/sebastianserna/ai-workflows) v1.0.0
