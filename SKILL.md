---
name: project-config-agent-collab-skill
description: GitHub 项目初始化与多Agent协同规范工具。自动生成ENTRY/PREFLIGHT/work_log/tasks/pitfalls/standards六份标配文件体系，自动注入PREFLIGHT打卡锁。执行初始化的Agent自动在SOUL.md写入工程操作守则，确保每次启动自带提醒。支持中英双语。 / Standardized project init & multi-agent collaboration system. Generates 6 standard docs (ENTRY/PREFLIGHT/work_log/tasks/pitfalls/standards), auto-injects PREFLIGHT gate check, and self-configures agent SOUL.md with operation rules so every session carries the reminder. EN+CN bilingual.
version: 1.1.0
author: Hermes, Lao Zhao
platforms: [macos, linux, windows]
tags: [project-config, agent-collaboration, documentation, engineering-standards, 项目配置, Agent协同, 工程模板]
---

# Project Config — Agent Collab Skill
# 项目配置管理 — Agent 协同技能

> English | [中文](#中文版)

---

## English

Every project must include the following 6 standard files in its root directory:

```
project-root/
├── ENTRY.md       ← Onboarding — first stop for new agents/contributors
├── PREFLIGHT.md   ← ⚠️ Must-read before touching any code
├── work_log.md    ← Work log — chronological, who did what
├── tasks.md       ← Task list — todo / in-progress / done
├── pitfalls.md    ← Pitfalls — all known issues, root cause + fix + prevention
└── standards.md   ← Coding/database/naming conventions
```

### Why

When multiple agents (or humans) work on the same project, **the project must document itself**:

- **ENTRY.md** tells newcomers what this project is, where we are, and where to look
- **PREFLIGHT.md** is the hard gate — agents must read the 4 standard files before modifying any code
- **work_log.md** answers "who did what and when" without reading anyone's mind
- **tasks.md** tracks what's pending, what's done, what depends on what
- **pitfalls.md** prevents repeating the same mistakes
- **standards.md** enforces consistent operations

### How It Works

1. **New project** → run this skill's initialization steps to auto-generate all files
2. **Existing project** → add the files manually, or run the init steps in project root
3. **Agent configures itself** → Step 6 appends operational rules into agent's `SOUL.md`, so every session start the agent sees the rules

---

## 中文版

每个工程根目录必须包含以下 6 个标配文件：

```
工程根目录/
├── ENTRY.md       ← 接入守则：新人/新Agent的第一站
├── PREFLIGHT.md   ← ⚠️ 动手前必读
├── work_log.md    ← 工作记录：按时间线推进，谁做了什么
├── tasks.md       ← 任务清单：待办/进行中/已完成
├── pitfalls.md    ← 踩坑记录：所有踩过的坑，根因+解决+预防
└── standards.md   ← 操作规范：数据库读写、命名、Git 等约定
```

### 为什么需要

多人/多 Agent 协作的工程，**工程自己必须会说话**：

- **ENTRY.md** 告诉新人：这是什么工程、做到哪了、去哪看
- **PREFLIGHT.md** 是硬锁——agent 动代码前必须先读完 4 份文件
- **work_log.md** 回答"谁什么时间做了什么"，不用翻聊天记录
- **tasks.md** 追踪待办、已完成、依赖关系
- **pitfalls.md** 防止踩过的坑再踩一次
- **standards.md** 统一操作方式，不出乱子

### 工作方式

1. **新建工程** → 跑本技能的初始化步骤，自动生成所有文件
2. **已有工程** → 手动补充，或在工程根目录重跑初始化
3. **Agent 自我配置** → Step 6 把操作守则写入 agent 的 `SOUL.md`，每次启动自带提醒

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
| 📖 目录 / Structure | `README.md` |

## 规矩 / Rules

1. **先看后动** — Read `work_log.md` and `tasks.md` first
2. **干了就记** — Update `work_log.md` after every step
3. **守规范** — Follow `standards.md`

## 当前状态 / Status

| Module | Progress | Status |
|--------|:--------:|:------:|
| {module} | {xx%} | ✅ / 🔄 / ⚠️ |

## 负责人 / Contacts

- {name} — {role}
```

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

## 3. work_log.md — 工作记录 / Work Log

```markdown
# 工作记录 / Work Log

> 每次推进后更新 / Update after every push.

## 格式 / Format

```
YYYY-MM-DD HH:MM | Author | What was done | Result | Notes
```

- **Author**: Full name ({Agent1} / {Agent2} / human name)
- **What**: Specific action, no vague descriptions
- **Result**: ✅ Success / ⚠️ Partial / ❌ Failed + key metrics
- **Notes**: Dependencies, blockers, next steps

---

### {YYYY-MM-DD}

#### {HH:MM} | {Author} | {What}
{Detail}
- ✅ / ⚠️ / ❌ {Result}
```

## 4. tasks.md — 任务清单 / Task List

```markdown
# 任务清单 / Task List

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
```

## 5. pitfalls.md — 踩坑记录 / Pitfalls

```markdown
# 踩坑记录 / Pitfalls

## 格式 / Format

```
YYYY-MM-DD | Author | Problem | Root Cause | Fix | Prevention
```

### {YYYY-MM-DD} | {Author} | {Title}

**Problem**: {what happened}
**Root Cause**: {why, to the call-chain level}
**Fix**: {how it was fixed}
**Prevention**:
- {step 1}
- {step 2}
```

## 6. standards.md — 操作规范 / Standards

```markdown
# 操作规范 / Standards

> 新 Agent 接入必须先读 / Must-read before working on this project.

## 数据库操作 / Database Operations (if any)

| Principle | Description |
|-----------|-------------|
| Read-Only | This project reads external DBs, never writes |
| Back Up First | Copy before any modification |

## 命名规范 / Naming Conventions

- Python: snake_case
- JSON: double quotes, indent=2
- MD docs: Title Case

## Git 提交规范 / Commit Convention (if using)

- `feat:` New feature
- `fix:` Bug fix
- `refactor:` Code refactor
- `docs:` Documentation
- `chore:` Maintenance
```

## 7. README.md — 工程概述 / Project Overview

```markdown
# {Project Name}

{one-line description}

## Directory Structure

```
{project-root}/
├── ENTRY.md       ← Onboarding (read this first)
├── PREFLIGHT.md   ← ⚠️ Must-read before coding
├── work_log.md    ← Work log
├── tasks.md       ← Task list
├── pitfalls.md    ← Pitfalls
├── standards.md   ← Standards
├── data/
├── src/
├── scripts/
├── models/
└── README.md      ← This file
```

## Quick Start

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
  {project-name}/tasks.md {project-name}/pitfalls.md {project-name}/standards.md {project-name}/README.md
```

## Step 3: Fill Templates

Replace `{placeholders}` with actual content using the templates above.

## Step 4: Create PREFLIGHT.md

Write PREFLIGHT.md into project root. This is the **hard gate** — any agent entering the project reads ENTRY.md first, sees the PREFLIGHT warning, and must complete the 4-file check before touching code.

Use the PREFLIGHT template above.

## Step 5: Add Warning to ENTRY.md Top

Insert this line right below the ENTRY.md title:

```markdown
> ⚠️ **动手前先读 PREFLIGHT.md** — Read PREFLIGHT.md before modifying any code.
```

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

1. Find `ENTRY.md` and read it (fallback: read `README.md`)
2. If `PREFLIGHT.md` exists in the project root, complete the check-in requirements
3. If no PREFLIGHT.md: default to reading work_log → tasks → standards before touching code
4. If no documentation system at all: `ls` the directory structure first

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
3. **Red flag in ENTRY.md** — Warning at the top, pointing to PREFLIGHT.md
4. **Agent self-config** — Write operation rules into own SOUL.md, loaded on every session start
5. **Main agent extra** — Also write into AGENTS.md
6. **Read first** — ENTRY.md is the first stop for newcomers
7. **Log every push** — Update work_log.md, pitfalls.md, tasks.md
8. **Standards on demand** — Only create standards.md when needed (DB/Git/API conventions)
9. **README = overview** — Keep detailed content in separate files

# Reference / 参考案例

- `/Volumes/book/comfy-master-engine/` — ComfyUI 主模型工程，完整示范了这套文件体系 + PREFLIGHT.md + agent 自我配置
  Files: ENTRY.md / PREFLIGHT.md / work_log.md / pitfalls.md / standards.md / SOUL.md / AGENTS.md
