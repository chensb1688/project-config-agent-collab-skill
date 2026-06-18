---
name: project-config-agent-collab-skill
description: Standardized project init & multi-agent collaboration system. Generates 7 standard docs (ENTRY/PREFLIGHT/work_log/tasks/pitfalls/standards/report), auto-injects PREFLIGHT gate check, and self-configures agent SOUL.md with operation rules. v1.3 adds 'create-if-missing' rule — agent actively creates the 7-file system when entering a project without it. / 项目初始化与多Agent协同规范工具。自动生成7份标配文件体系，自动注入PREFLIGHT打卡锁，v1.3新增'缺则创建'规则。
version: 1.3.0
author: Hermes, Lao Zhao
platforms: [macos, linux, windows]
tags: [project-config, agent-collaboration, documentation, engineering-standards, 项目配置, Agent协同, 工程模板]
---

# Project Config — Agent Collab Skill

> A standardized way to onboard agents and humans into any project.  
> Every project documents itself, so nobody has to ask "what's going on here?"

---

## The 7 Standard Files

```
project-root/
├── ENTRY.md       ← Onboarding — first stop for newcomers
├── PREFLIGHT.md   ← ⚠️ Must-read before touching any code
├── work_log.md    ← Work log — who did what, when
├── tasks.md       ← Task list — todo / in-progress / done
├── pitfalls.md    ← Pitfalls — root cause + fix + prevention
├── standards.md   ← Project-specific operation rules
└── report.md      ← Project overview — progress, headcount, tech debt (optional)
```

### Why

- **ENTRY.md** — what is this project, where are we, where to look
- **PREFLIGHT.md** — hard gate: must be checked before modifying code
- **work_log.md** — progress log without reading chat history
- **tasks.md** — pending, done, and blocked items
- **pitfalls.md** — don't repeat the same mistakes
- **standards.md** — consistent operations across agents
- **report.md** — quick status snapshot (optional for small projects)

---

## Templates

### 1. ENTRY.md

```markdown
# ENTRY.md — Onboarding Guide

> ⚠️ Read PREFLIGHT.md before modifying any code.

## About

{one-line project description}

## Quick Nav

| You Want | See |
|----------|-----|
| Progress | `work_log.md` |
| Tasks | `tasks.md` |
| Pitfalls | `pitfalls.md` |
| Standards | `standards.md` |
| Report | `report.md` |
| Structure | `README.md` |

## Rules

1. Read work_log.md and tasks.md first
2. Update work_log.md after every step
3. Follow standards.md

## Status

| Module | Progress | Status |
|--------|:--------:|:------:|
| {module} | {xx%} | ✅ / 🔄 / ⚠️ |

## Contacts

- {name} — {role}
```

### 2. PREFLIGHT.md

```markdown
# ⚠️ Must-Read Before Action

**Read these files in order:**

| # | File | Why |
|---|------|-----|
| 1 | ENTRY.md | Project overview |
| 2 | work_log.md | Recent progress |
| 3 | tasks.md | Current tasks |
| 4 | standards.md | Operation rules |

**Reply: `✅ PREFLIGHT COMPLETE`**

## After Modifications

- Update work_log.md
- Update tasks.md
- Log new pitfalls in pitfalls.md
```

### 3. work_log.md

```markdown
# Work Log

### {YYYY-MM-DD} | {Author} | {Category}

{what was done}

- ✅ / ⚠️ / ❌ {result}
- **Scope**: {files / modules}
- **Notes**: {blockers, next steps}
```

### 4. tasks.md

```markdown
# Task List

> **If conditions are met, execute directly. Don't wait for approval.**

### Task {N}: {Title}

**Status**: ⏳ Todo / 🔄 In Progress / ✅ Done / ❌ Cancelled
**Priority**: P0(Urgent) / P1(Important) / P2(Normal)

**Description**:
1. {step}
2. {step}

**Acceptance Criteria**:
- [ ] {criterion}

---

## Completed

### Task {N}: {Title}

**Status**: ✅ Done | **Completed**: {YYYY-MM-DD}
- [x] {item}
```

### 5. pitfalls.md

```markdown
# Pitfalls

> **Not recorded = will happen again.**

### {YYYY-MM-DD} | {Author} | {Problem}

**Problem**: {what happened}
**Root Cause**: {why it happened}
**Fix**: {how it was fixed}
**Prevention**:
- {step}
- {step}
```

### 6. standards.md

```markdown
# Standards

> Rules the project runs on. New agents must read this first.

## {Category}

| Rule | Description |
|------|-------------|
| {rule} | {explanation} |

---

### Mandatory: Backup & Sync

| Principle | Description |
|-----------|-------------|
| Separate drives | Work and backup must be **different physical devices** |
| 3-2-1 rule | 3 copies, 2 media types, 1 offsite |
| Write-only backup | Backup drive is append-only, no edits |

**When to back up:**

| Scenario | Required |
|----------|:--------:|
| After every code/doc change | ✅ |
| Before release/packaging | ✅ |
| Before deleting anything | ✅ |
| Before format/reinstall | ✅ |
| Daily routine | ⏰ |
| Before testing new tools | ✅ |
| Before major upgrade | ✅ |
| Before database operations | ✅ |

---

### Common Categories (fill as needed)

#### Path conventions
- Boot scripts use `SCRIPT_DIR="$(cd "$(dirname "$0")" && pwd)"` or `%~dp0`
- No hardcoded absolute paths

#### Git commit format
- `feat:` — new feature
- `fix:` — bug fix
- `refactor:` — code refactor
- `docs:` — documentation
- `chore:` — maintenance
```

### 7. report.md

```markdown
# {Project Name} — Report

> Generated: {YYYY-MM-DD}
> By: {Author}

## Overview

| Item | Value |
|------|-------|
| Name | {Project Name} |
| Status | Dev / Maintenance / Done |
| Code size | {lines / files} |

## Team

| Role | Person | Load |
|------|--------|:----:|
| {role} | {name} | {xx%} |

## Progress

**Overall: {xx%}**

| Module | Progress | Notes |
|--------|:--------:|-------|
| {module} | {xx%} | {notes} |

## TODOs

| Pri | Item | Owner | ETA |
|-----|------|-------|-----|
| P0 | {item} | {name} | {date} |

## Tech Debt

| Issue | Impact | Fix by |
|-------|--------|--------|
| {issue} | {impact} | {date} |
```

---

## Agent Operation Rules

**Any agent using this skill must follow these rules:**

### Entering a Project

1. Look for the 7 standard files: `ENTRY.md`, `PREFLIGHT.md`, `work_log.md`, `tasks.md`, `pitfalls.md`, `standards.md`, `report.md`
2. If they exist → read `ENTRY.md`, then complete PREFLIGHT check-in
3. If they **don't exist** → **create them immediately** using the templates above
4. If no docs at all → `ls` the directory, then create the 7 files

### During Operations

- **Log every step** → update work_log.md
- **Log every pitfall** → write to pitfalls.md
- **Track tasks** → update tasks.md
- **Follow standards** → adhere to standards.md

### Self-Configuration

When assigned to a project long-term, add this to your `SOUL.md` after the `## My Role` section:

```markdown
## Engineering Operation Rules

Before modifying any project, read its:
1. ENTRY.md
2. work_log.md
3. tasks.md
4. standards.md

> Projects have PREFLIGHT.md as their gate. Check in before you start.
```

---

## Rules Summary

1. Enter any project → find ENTRY.md or README.md first
2. PREFLIGHT.md in project root = hard gate, must check in
3. ENTRY.md must have a warning pointing to PREFLIGHT.md
4. Agents write operation rules into own SOUL.md
5. Main agent also writes into AGENTS.md
6. **Create if missing** — any project without the 7-file system gets created immediately
7. Log every push: work_log.md, pitfalls.md, tasks.md
8. Standards on demand — only when needed
9. README is the outer door
10. report.md is optional for small projects
