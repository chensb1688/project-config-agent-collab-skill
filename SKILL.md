---
name: project-config-agent-collab-skill
description: Standardized project init & multi-agent collaboration system. Generates 7 standard docs (ENTRY/PREFLIGHT/work_log/tasks/pitfalls/standards/report), auto-injects PREFLIGHT gate check, and self-configures agent SOUL.md with operation rules. v1.3 adds 'create-if-missing' rule — agent actively creates the 7-file system when entering a project without it. / 项目初始化与多Agent协同规范工具。自动生成7份标配文件体系，自动注入PREFLIGHT打卡锁，v1.3新增'缺则创建'规则。
version: 1.3.0
author: Hermes, Lao Zhao
platforms: [macos, linux, windows]
tags: [project-config, agent-collaboration, documentation, engineering-standards, 项目配置, Agent协同, 工程模板]
---

# SOUL.md 强制守则

## 每个 Agent 的 SOUL.md 必须包含

```markdown
## 工程新建与参与守则

新建项目或参与任何项目时，必须先检查根目录是否存在以下 7 个标配文件：
- ENTRY.md
- work_log.md
- pitfalls.md
- tasks.md
- standards.md
- report.md
- README.md

缺少任何文件 → 立即创建，不得跳过。
```

## 检查方法

进入项目根目录后：

```bash
ls ENTRY.md work_log.md pitfalls.md tasks.md standards.md report.md README.md
```

缺失项立即创建，不等待、不询问。

---

# 7 文件模板

## 1. ENTRY.md — 接入手则

```markdown
# {项目名} — 接入手则

## 项目描述
{一句话描述}

## 快速导航
| 文件 | 用途 |
|------|------|
| work_log.md | 工作记录 |
| tasks.md | 当前任务 |
| pitfalls.md | 踩坑记录 |
| standards.md | 操作规范 |
| report.md | 项目报告 |

## 当前状态
{最近做了什么，待做什么}

## 三条规矩
1. 遇坑必记 — pitfalls.md
2. 做了就记 — work_log.md
3. 数据库不清除不删改
```

## 2. README.md — 工程概述

```markdown
# {项目名}

## 目录结构
{树形目录}

## 架构
{架构描述}

## 快速开始
{启动命令}
```

## 3. work_log.md — 工作记录

```markdown
# {项目名} — 工作记录

## YYYY-MM-DD | 执行人 | 做了什么
- ✅/⚠️/❌ 结果
```

## 4. tasks.md — 任务清单

```markdown
# {项目名} — 任务清单

## 待办
- [ ] 任务

## 进行中
- [ ] 任务

## 已完成
- [x] 任务
```

## 5. pitfalls.md — 踩坑记录

```markdown
# 踩坑记录

> 遇坑不记＝还会再踩。

## 日期 | 执行人 | 标题
**问题**: 现象
**根因**: 为什么
**解决**: 怎么修
**预防**: 如何避免
```

## 6. standards.md — 操作规范

```markdown
# 操作规范

## 路径规范
- 不硬编码绝对路径

## 编码规范
- .bat → ASCII + CRLF + 无BOM
- .sh/.command → UTF-8 + LF

## 磁盘同步
- book 工作，AIWORK 存档

## 备份规范

| 原则 | 说明 |
|------|------|
| 分盘放置 | 工作盘和备份盘是不同物理设备 |
| 3-2-1 原则 | 3 副本、2 介质、1 异地 |
| 只写不改 | 备份盘只写不改 |

| 场景 | 必备份 |
|------|:------:|
| 每次改代码后 | ✅ |
| 发布前 | ✅ |
| 删除任何文件前 | ✅ |
| 格式化前 | ✅ |
| 数据库操作前 | ✅ |
```

## 7. report.md — 项目报告

```markdown
# {项目名} — 报告

## 概况
| 项目 | 内容 |
|------|------|
| 名 | {name} |
| 状态 | 开发/维护/完结 |
| 代码量 | {lines} |

## 进度
**总体**: {xx%}

## 技术债务
- {issue}
```

---

# Agent 操作守则

**使用此 skill 的 Agent 必须遵守：**

### 进入项目

1. 查 7 文件：ENTRY.md / work_log.md / pitfalls.md / tasks.md / standards.md / report.md / README.md
2. 存在 → 读 ENTRY.md，完成 PREFLIGHT 打卡
3. **不存在 → 立即创建**，用上面的模板
4. 无文档体系 → ls 目录，然后创建 7 文件

### 执行中

- **做→记→更新→继续** — 活干了不记=没干完
- **遇坑必记** — 现象+根因+解决+预防
- **一次只改一个版本** — 多 SKU 逐一处理

### Agent 自配置

长期参与一个工程时，在自身 SOUL.md 的 `## 我的角色` 后插入：

```markdown
## 工程新建与参与守则

新建项目或参与任何项目时，必须先检查根目录是否存在以下 7 个标配文件：
- ENTRY.md
- work_log.md
- pitfalls.md
- tasks.md
- standards.md
- report.md
- README.md

缺少任何文件 → 立即创建，不得跳过。
```

---

# 规则总览

1. 进入任何工程 → 先找 ENTRY.md 或 README.md
2. PREFLIGHT.md 是硬锁门，必须打卡
3. ENTRY.md 必须有 ⚠️ 指向 PREFLIGHT.md
4. Agent 把守则写入自身 SOUL.md
5. 主 Agent 同时写入 AGENTS.md
6. **缺则创建** — 无 7 文件体系的工程一律创建
7. 每次推动记录：work_log.md / pitfalls.md / tasks.md
8. 规范按需创建
9. README 是第一道门
10. report.md 小项目可选
