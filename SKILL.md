---
name: project-config-agent-collab-skill
description: GitHub 项目初始化与多Agent协同规范工具。自动生成7份标配文件体系（ENTRY/PREFLIGHT/work_log/tasks/pitfalls/standards/report），自动注入PREFLIGHT打卡锁。执行初始化的Agent自动在SOUL.md写入工程操作守则，确保每次启动自带提醒。v1.2新增report.md标配、四段式pitfalls、结构化work_log。支持中英双语。 / Standardized project init & multi-agent collaboration system. Generates 7 standard docs (ENTRY/PREFLIGHT/work_log/tasks/pitfalls/standards/report), auto-injects PREFLIGHT gate check, and self-configures agent SOUL.md with operation rules. v1.2 adds report.md as standard, four-part pitfalls format, structured work_log. EN+CN bilingual.
version: 1.2.0
author: Hermes, Lao Zhao
platforms: [macos, linux, windows]
tags: [project-config, agent-collaboration, documentation, engineering-standards, 项目配置, Agent协同, 工程模板]
---

# Project Config — Agent Collab Skill
# 项目配置管理 — Agent 协同技能

> English | [中文](#中文版)

---

## English

Every project must include the following **7 standard files** in its root directory:

```
project-root/
├── ENTRY.md       ← Onboarding — first stop for new agents/contributors
├── PREFLIGHT.md   ← ⚠️ Must-read before touching any code
├── work_log.md    ← Work log — chronological, who did what
├── tasks.md       ← Task list — todo / in-progress / done
├── pitfalls.md    ← Pitfalls — root cause + fix + prevention
├── standards.md   ← Project-specific operation rules
└── report.md      ← Project overview — progress, headcount, tech debt (optional)
```

### Why

When multiple agents (or humans) work on the same project, **the project must document itself**:

- **ENTRY.md** tells newcomers what this project is, where we are, and where to look
- **PREFLIGHT.md** is the hard gate — agents must complete the file check before modifying any code
- **work_log.md** answers "who did what and when" without reading anyone's mind
- **tasks.md** tracks what's pending, what's done, what depends on what
- **pitfalls.md** prevents repeating the same mistakes
- **standards.md** enforces consistent operations
- **report.md** gives a quick status report — progress %, headcount, tech debt (optional, omit for simple projects)

### What's New in v1.2

- **+report.md** — New standard file for project status summaries
- **pitfalls.md** upgraded — Four-part free-text format (Problem → Root Cause → Fix → Prevention), no longer limited by table cells
- **work_log.md** upgraded — Structured logs with title sections + detailed entries, easier to read at a glance
- **standards.md** upgraded — Let projects define their own specific rules; templates only provide framework principles
- **+report.md** — New standard file for project status summaries
- **pitfalls.md** upgraded — Four-part free-text format (Problem → Root Cause → Fix → Prevention), no longer limited by table cells
- **work_log.md** upgraded — Structured logs with title sections + detailed entries, easier to read at a glance
- **standards.md** upgraded — Let projects define their own specific rules; templates only provide framework principles
- **Init steps updated** — report.md generation, new work_log/pitfalls templates

---

## 中文版

每个工程根目录必须包含以下 **7 个标配文件**：

```
工程根目录/
├── ENTRY.md       ← 接入守则：新人/新Agent的第一站
├── PREFLIGHT.md   ← ⚠️ 动手前必读（硬锁门）
├── work_log.md    ← 工作记录：按时间线推进，谁做了什么
├── tasks.md       ← 任务清单：待办/进行中/已完成
├── pitfalls.md    ← 踩坑记录：根因+解决+预防（四段式）
├── standards.md   ← 操作规范：工程专用规则
└── report.md      ← 项目总览：进度/人力/技术债务（可选，简单项目可省略）
```

### 为什么需要

多人/多 Agent 协作的工程，**工程自己必须会说话**：

- **ENTRY.md** 告诉新人：这是什么工程、做到哪了、去哪看
- **PREFLIGHT.md** 是硬锁——agent 动代码前必须先读完 4 份文件
- **work_log.md** 回答"谁什么时间做了什么"，不用翻聊天记录
- **tasks.md** 追踪待办、已完成、依赖关系
- **pitfalls.md** 防止踩过的坑再踩一次
- **standards.md** 统一操作方式，不出乱子
- **report.md** 快速了解项目全局状态（进度的百分比、人力分布、技术债），可选

### v1.2 更新了什么

- **+report.md** — 新增标配，项目全局状态一目了然
- **pitfalls.md 升级** — 四段式自由文本（问题→根因→解决→预防），表格装不下复杂的根因分析
- **work_log.md 升级** — 结构化日志，按天/模块分类加标题，一眼看到重点
- **standards.md 升级** — 只写框架原则，具体规则让项目自己填充
- **+report.md** — 新增标配，项目全局状态一目了然
- **pitfalls.md 升级** — 四段式自由文本（问题→根因→解决→预防），表格装不下复杂的根因分析
- **work_log.md 升级** — 结构化日志，按天/模块分类加标题，一眼看到重点
- **standards.md 升级** — 只写框架原则，具体规则让项目自己填充
- **初始化步骤同步** — 更新生成命令和模板引用

---

# Templates / 模板

## 1. ENTRY.md — 接入守则 / Onboarding Guide

```markdown
# ENTRY.md — 接入守则 / Onboarding Guide

> ⚠️ **动手前先读 PREFLIGHT.md** — Read PREFLIGHT.md before modifying any code.

## 这是什么 / About

{project description / 一句话描述}

## 快速导航 / Quick Nav

| 你想知道 / You Want | 去看哪个文件 / See |
|---------------------|-------------------|
| 🔄 进度 / Progress | `work_log.md` |
| 📋 待办 / Tasks | `tasks.md` |
| 💥 踩坑 / Pitfalls | `pitfalls.md` |
| 📐 规范 / Standards | `standards.md` |
| 📊 概况 / Report | `report.md`（可选） |
| 📖 目录 / Structure | `README.md` |

## 三条规矩 / Rules

1. **先看后动** — Read `work_log.md` and `tasks.md` first
2. **干了就记** — Update `work_log.md` after every step
3. **守规范** — Follow `standards.md`

## 当前状态 / Status

| 模块 / Module | 进度 / Progress | 状态 / Status |
|---------------|:--------------:|:-------------:|
| {module}      | {xx%}          | ✅ / 🔄 / ⚠️  |

## 负责人 / Contacts

- {name} — {role}
```

---

## 2. PREFLIGHT.md — 动手前必读 / Must-Read Before Action

```markdown
# ⚠️ 动手前必读 / Must-Read Before Action

**按顺序读完以下文件 / Read these files in order:**

| # | File | Why |
|---|------|-----|
| 1 | `ENTRY.md` | 工程概况 / Project overview |
| 2 | `work_log.md` | 最近进度 / Recent progress |
| 3 | `tasks.md` | 当前待办 / Current tasks |
| 4 | `standards.md` | 操作红线 / Operation rules |

**读完后回复 / After reading, reply: `✅ PREFLIGHT COMPLETE`**

## 改完要干的事 / After Modifications

- Update `work_log.md` — who, what, result, notes
- Update `tasks.md` — mark done items
- Update related docs (README / ENTRY / etc.)
- Log new pitfalls in `pitfalls.md`
```

---

## 3. work_log.md — 工作记录 / Work Log

```markdown
# 工作记录 / Work Log

> 每次推进后更新 / Update after every push.

## 格式 / Format

### {YYYY-MM-DD} | {Author} | {Category Title}

{detail description of what was done}

- ✅ / ⚠️ / ❌ {Result and key metrics}
- **影响范围**: {files changed / modules impacted}
- **备注**: {dependencies, blockers, next steps}

---

### 示例 / Example

### 2026-06-18 | Hermes | 去混淆：所有混淆文件替换为源代码

**背景：** 之前为了防窥探用 javascript-obfuscator 混淆，生成 server-obfuscated.js 和 config-obfuscated.html。

**操作：**
1. 删除 server/server-obfuscated.js（63KB 混淆）
2. 删除 server/config-obfuscated.html（631KB 混淆）
3. 更新 6 个启动脚本：server-obfuscated.js → server.js

- ✅ 服务正常启动，所有 API 返回正常
- **影响范围**: server/ + 6个启动脚本
```

---

## 4. tasks.md — 任务清单 / Task List

```markdown
# 任务清单 / Task List

> **条件具备直接执行，不等指令。**
> 说明：如果条件成熟，不需要等谁批准，直接动手。

### Task {N}: {Title}

**Status**: ⏳ Todo / 🔄 In Progress / ✅ Done / ❌ Cancelled
**Owner**: {Author}
**Priority**: P0(Urgent) / P1(Important) / P2(Normal)
**Estimate**: {X}h

**Description**:
1. {step 1}
2. {step 2}

**Acceptance Criteria**:
- [ ] {criterion 1}
- [ ] {criterion 2}

**Depends On**: Task {M}

---

## 历史已完成任务 / Completed Tasks

### Task {N}: {Title}

**Status**: ✅ Done | **Owner**: {Author} | **Completed**: {YYYY-MM-DD}

- [x] {completed item 1}
- [x] {completed item 2}
```
---

## 5. pitfalls.md — 踩坑记录 / Pitfalls

```markdown
# 踩坑记录 / Pitfalls

> 所有踩过的坑。**遇坑不记＝还会再踩**。

## 格式 / Format

```
日期 | 执行人 | 问题标题
问题: 具体现象
根因: 为什么会出现（追到调用链级别）
解决: 怎么修好的
预防: 以后怎么做可以避免
```

---

### {YYYY-MM-DD} | {Author} | {Problem Title}

**问题**: {what happened, what the user saw}
**根因**: {why it happened, traced to call-chain level}
**解决**: {how it was fixed, commands/code/process}
**预防**:
- {step 1}
- {step 2}

---

### 示例 / Example

### 2026-06-18 | Hermes | 诊断修复.bat 中文乱码

**问题**: Windows 诊断修复.bat 标题和回显中文全部乱码。

**根因**: 文件原始是 GBK 编码，被错误存为 UTF-8。中文 Windows cmd 原生编码是 GBK (CP936)，但文件声明了 UTF-8 却存放了 GBK 字节。

**解决**: 用 `iconv -f UTF-8 -t GBK` 转为 GBK + `perl` 修复 CRLF 换行。去掉 `chcp 65001`。

**预防**:
- Windows .bat 文件中文用 GBK (CP936) 编码，不依赖 chcp
- 或纯 ASCII 英文，零编码问题
- CRLF 换行必备（`\r\n`）
```

---

## 6. standards.md — 操作规范 / Standards

```markdown
# 操作规范 / Standards

> 工程运行时必须遵守的规则。新 Agent 接入必须先读。

## {Category 1} / {category name}

| 规则 / Rule | 说明 / Description |
|-------------|-------------------|
| {rule}      | {explanation}     |

## {Category 2}

...

---

### 必填规范：备份与同步

> **任何项目必须建立备份规范。不备份=数据丢失是早晚的事。**

#### 基本原则

| 原则 | 说明 |
|------|------|
| 分盘放置 | 工作盘和备份盘必须是**不同的物理设备**，不能在同一块盘的两个分区 |
| 3-2-1 原则 | 至少 3 份副本、2 种不同的介质、1 份异地/脱机 |
| 最小可行 | 最小配置：工作盘 + 备份盘（另一块物理盘） |
| 只写不改 | 备份盘上只做覆盖写入，不做编辑修改 |

#### 什么时候必须备份

| 场景 | 必须备份 | 说明 |
|------|:--------:|------|
| 每次修改代码/文档后 | ✅ | 改完就同步，不累积 |
| 发布/打包新版本前 | ✅ | 发布前做一次完整备份 |
| 删除任何文件前 | ✅ | 先备份再删，删错了能恢复 |
| 格式化/重装系统前 | ✅ | 整盘备份 |
| 例行维护 | ⏰ 每日 | 每天结束时同步一次 |
| 测试新功能/新工具前 | ✅ | 确保有回退点 |
| 别人接手项目前 | ✅ | 完整的移交备份 |
| 大版本升级前 | ✅ | 全量备份当前版本 |
| 数据库直接操作前 | ✅ | 先 cp 备份再改 |

#### 工作流程

```
工作盘（book/主盘）
  │
  ├── 日常开发、修改
  ├── 改完立即：cp -a 同步到备份盘
  └── 重要节点前：完整备份
          │
          ▼
备份盘（AIWORK/从盘）
  ├── 被动副本，只写不改
  ├── 保留最近 N 个版本（按项目需要，至少保留上一个版本）
  └── 备份后抽样 MD5 校验关键文件
```

#### 命名规范

| 场景 | 命名方式 | 示例 |
|------|----------|------|
| 常规同步 | 同名覆盖 | `work/project/` → `backup/project/` |
| 版本备份 | 项目名 + 版本号或日期 | `myapp_v1.2.0/`、`myapp_2026-06-18/` |
| 发布备份 | 项目名 + 版本号 + 状态 | `myapp_v1.2.0_release/` |
| 危险操作前 | 项目名 + before + 操作名 | `myapp_before_cleanup/` |

#### 不遵守的后果

不备份 ≠ 不会出事。以下都是实际发生过的事故：

- 误删重要代码文件，无备份无法恢复
- 格式化 U 盘忘了转移数据，所有工作丢失
- 配置向导误写入占位符覆盖了配置文件
- 数据库直接操作失误导致数据丢失
- ExFAT 小文件写入静默失败，文件存在但实际为空

**备份不是选项，是纪律。**

---

### 适用你的工程的具体规范填写范例

（以下是根据 book 版落地经验总结的常见规范分类，按需选用）

#### 路径规范

| 规则 | 说明 |
|------|------|
| 定位脚本目录 | 启动脚本用 `SCRIPT_DIR="$(cd "$(dirname "$0")" && pwd)"` 或 `%~dp0` |
| 不硬编码路径 | 不写死 `/Volumes/xxx/...`，所有路径取自脚本所在根目录 |

#### 启动流程规范

| 阶段 | 规范 |
|------|------|
| 启动脚本 | `.command` / `.bat` / `.ps1` 同一份逻辑 |
| 兼容性检测 | 系统版本/CPU架构/内存 门槛检测 |
| Node.js | 系统优先 → U盘自带 → 自动下载回退 |
| 防拷校验 | 入口脚本完成，server 内部不再重复 |
| 端口冲突 | 清理僵尸进程，不能重复启动 |

#### git 提交规范（如果用）

- `feat:` — 新功能
- `fix:` — Bug 修复
- `refactor:` — 重构
- `docs:` — 文档
- `chore:` — 维护

#### 磁盘同步规范（项目有外部存储）

| 规则 | 说明 |
|------|------|
| 工作在主盘 | 所有修改在工作盘上进行（如 book） |
| 存档到从盘 | 完成后再同步到存档盘（如 AIWORK） |
| 不在存档盘改 | 存档盘是被动副本，不在上面直接操作 |
| 验证一致性 | 同步后抽样 MD5 关键文件 |
```

---

## 7. report.md — 项目概况 / Project Report

```markdown
# {Project Name} — 项目评估报告

> 报告生成时间：{YYYY-MM-DD}
> 报告人：{Author}

## 一、项目概况

| 项目 | 内容 |
|------|------|
| **项目名** | {Project Name} |
| **定位** | {one-line description} |
| **状态** | 开发中 / 维护中 / 已完结 |
| **代码规模** | {total lines / file count} |

## 二、主要负责人与工作量分布

| 角色 | 人 | 职责 | 工作量占比 |
|------|----|------|-----------|
| {role} | {name} | {duty} | {xx%} |

## 三、已完成的功能

### ✅ {Category}
- {feature}: {description}
- ...

## 四、待办 / 下一步

| 优先级 | 事项 | 负责人 | 预期 |
|--------|------|--------|------|
| P0 | {item} | {owner} | {expected} |

## 五、项目进度

**总体进度：{xx%}**

| 模块 | 进度 | 说明 |
|------|:----:|------|
| {module} | {xx%} | {notes} |

## 六、技术债务 / Technical Debt

| 问题 | 影响 | 建议修复时间 |
|------|------|-------------|
| {issue} | {impact} | {timeline} |
```

---

## 8. README.md — 工程概述 / Project Overview

```markdown
# {Project Name}

{one-line description}

## 适用人群

{target users}

## 目录结构

```
{project-root}/
├── ENTRY.md       ← Onboarding (read this first)
├── PREFLIGHT.md   ← ⚠️ Must-read before coding
├── work_log.md    ← Work log
├── tasks.md       ← Task list
├── pitfalls.md    ← Pitfalls
├── standards.md   ← Standards
├── report.md      ← Project report
├── README.md      ← This file
├── {component}/
└── {component}/
```

## 快速开始

{how to run}
```

---

# Initialization Steps / 初始化步骤

## Step 1: Create Project Directory

```bash
mkdir -p {project-name}/data/{raw,processed,knowledge} {project-name}/src {project-name}/scripts \
  {project-name}/models {project-name}/outputs {project-name}/docs
```

## Step 2: Generate Standard Files

```bash
touch {project-name}/ENTRY.md {project-name}/PREFLIGHT.md {project-name}/work_log.md \
  {project-name}/tasks.md {project-name}/pitfalls.md {project-name}/standards.md \
  {project-name}/report.md {project-name}/README.md
```

## Step 3: Fill Templates

Replace `{placeholders}` with actual content using the templates above.

- **ENTRY.md** → template 1
- **PREFLIGHT.md** → template 2
- **work_log.md** → template 3 (structured format)
- **tasks.md** → template 4
- **pitfalls.md** → template 5 (four-part format)
- **standards.md** → template 6 (pick relevant categories)
- **report.md** → template 7 (optional: skip for simple projects)
- **README.md** → template 8

> If the project has only one agent working on it (single-person), `report.md` is optional.

## Step 4: Create PREFLIGHT.md

Write PREFLIGHT.md into project root. This is the **hard gate** — any agent entering the project reads ENTRY.md first, sees the PREFLIGHT warning, and must complete the 4-file check before touching code.

Use the PREFLIGHT template above.

## Step 5: Add PREFLIGHT Warning to ENTRY.md

Insert this line right below the ENTRY.md title:

```markdown
> ⚠️ **动手前先读 PREFLIGHT.md** — Read PREFLIGHT.md before modifying any code.
```

> PREFLIGHT.md 是强制的。有这个入口警告，任何 Agent 进项目必须完成 4 文件检查才能动代码。
> PREFLIGHT.md is mandatory. This entry warning ensures every agent completes the 4-file check before touching code.

## Step 6: Configure Current Agent's SOUL.md and AGENTS.md

This is the most critical step — **the executing agent writes operational rules into its own config files**, so every future session carries the reminder automatically.

### 6a: Modify SOUL.md

Locate the current agent's `SOUL.md`:
- **Main agent**: `~/.openclaw/workspace/SOUL.md`
- **Other agents**: `~/.openclaw/agents/{agent-name}/agent/SOUL.md`

Insert the following section **right below the `## 我的角色` / `## My Role` section**:

```markdown
## 📐 工程操作守则 / Engineering Operation Rules

**修改工程前必须先读该工程的准入文件 / Before modifying any project, read its:**

1. `ENTRY.md` — 接入守则 / Onboarding guide
2. `work_log.md` — 最近进度 / Recent progress
3. `tasks.md` — 当前待办 / Current tasks
4. `standards.md` — 操作红线 / Operation rules

> 工程根目录有 `PREFLIGHT.md`，那是第一道门。进去之前先打卡。
> Projects have `PREFLIGHT.md` as their gate. Check in before you start.
```

### 6b: Modify AGENTS.md (Main Agent Only)

The main agent's `AGENTS.md` is at `~/.openclaw/workspace/AGENTS.md`. Check if an "Operation Rules" section exists. If not, insert this block before the `## Tools` section:

```markdown
## 🏗️ 操作守则 / Engineering Operation Rules

**Before modifying any project's code/config/docs, you must read:**

1. `ENTRY.md` — Onboarding guide / 接入守则
2. `work_log.md` — Recent progress / 最近进度
3. `tasks.md` — Current tasks / 当前待办
4. `standards.md` — Operation rules / 操作红线

After modifications, update: `work_log.md` + `tasks.md`.

### Other Projects
If they have README.md / ENTRY.md, read them first. Otherwise `ls` the directory.
```

> **Note**: Only the main agent (workspace repo) has AGENTS.md. Other agents like cute/hermes don't need it — modifying SOUL.md is sufficient.

---

# Agent Universal Operation Rules / Agent 通用操作守则

**Any agent that has loaded this skill must follow these rules when working on any project:**

### Entering a New Project — First Things First

Whether it's a new or existing project, main or side project:

1. Look for the 7 standard files: `ENTRY.md`, `PREFLIGHT.md`, `work_log.md`, `tasks.md`, `pitfalls.md`, `standards.md`, `report.md`
2. If they exist: read `ENTRY.md` first (fallback: `README.md`), then complete PREFLIGHT check-in
3. If they **don't exist**: **create them immediately** using the templates in this skill. Every project needs the full 7-file system.
4. If no documentation system at all: `ls` the directory structure first, then create the 7 files.

### During Operations

- **Log every step** — Update `work_log.md`
- **Log every pitfall** — Write to `pitfalls.md`
- **Track tasks** — Mark `tasks.md`
- **Follow standards** — Adhere to `standards.md`

### Long-Term Participation

When assigned to a project long-term:

1. Follow the "Agent Onboarding Flow" section below to update your own `SOUL.md` with project operation rules

---

# Agent Onboarding Flow / Agent 接入流程

When a new agent is assigned to an existing project:

### 1. PREFLIGHT Check-in

Enter project root → read `ENTRY.md` → see the PREFLIGHT warning → complete the 4-file read.

### 2. Modify Own SOUL.md

Locate your agent's `SOUL.md`. Insert the operation rules section **right below the `## 我的角色` / `## My Role` section**:

```markdown
## 📐 工程操作守则 / Engineering Operation Rules

**修改工程前必须先读该工程的准入文件 / Before modifying any project, read its:**

1. `ENTRY.md` — 接入守则 / Onboarding guide
2. `work_log.md` — 最近进度 / Recent progress
3. `tasks.md` — 当前待办 / Current tasks
4. `standards.md` — 操作红线 / Operation rules

> 工程根目录有 `PREFLIGHT.md`，那是第一道门。进去之前先打卡。
> Projects have `PREFLIGHT.md` as their gate. Check in before you start.
```

### 3. Verify

Start a new session and confirm the operation rules are visible in `SOUL.md`.

---

# Rules / 规则

1. **Universal rule #1** — Enter any project → find ENTRY.md or README.md first
2. **Hard gate** — PREFLIGHT.md in project root, any agent must check in before coding
3. **Red flag in ENTRY.md** — Warning at the top, pointing to PREFLIGHT.md（强制必有）
4. **Agent self-config** — Write operation rules into own SOUL.md, loaded on every session start
5. **Main agent extra** — Also write into AGENTS.md
6. **Read first** — ENTRY.md is the first stop for newcomers
7. **Create if missing** — Any project without the 7-file system gets created immediately
8. **Log every push** — Update work_log.md, pitfalls.md, tasks.md
9. **Standards on demand** — Only create standards.md when needed (DB/Git/API conventions)
10. **README = overview** — Keep detailed content in separate files; README is the outer door
11. **report.md as optional** — Generate for projects with multiple people/agents; skip for personal projects

# Reference / 参考案例

- `/Volumes/book/comfy-master-engine/` — ComfyUI 主模型工程，完整示范了这套文件体系 + PREFLIGHT.md + agent 自我配置
  Files: ENTRY.md / PREFLIGHT.md / work_log.md / pitfalls.md / standards.md / SOUL.md / AGENTS.md

- `/Volumes/book/OpenClaw5.20HERMES双系统无敌版源码/` — OpenClaw 双系统版，v1.2 模板的实际落地案例
  包含全部 7 个标配文件 + 完整的踩坑/任务/规范记录
