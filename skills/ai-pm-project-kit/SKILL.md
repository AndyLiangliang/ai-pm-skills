---
name: ai-pm-project-kit
description: 中文 AI PM 项目启动工作流：从 AI 产品想法 → 方案设计 → Vibe Coding Prompt → 项目骨架。当用户说"我要做一个 AI 产品"、"设计一个 Agent"、"启动 AI 项目"或"/ai-pm-project-kit"时触发。若用户要拆竞品、算值不值得做、做商业可行性，先走 ai-pm-teardown，不要用本 skill 代替拆解。
disable-model-invocation: false
---

# AI PM 项目启动工作流

## 触发识别

当用户表达以下意图时启动本工作流：

- "我要做一个 AI 产品"
- "我想设计一个 Agent"
- "做一个 RAG 项目"
- "启动一个 AI 项目"
- "把 AI 加到 [某个场景]"
- "/ai-pm-project-kit"

## 输入

- 用户的原始想法（可以是一句话、一段描述或一个链接）
- 可选：目标用户、参考产品、技术偏好、相关 wiki 页

## 标准工作流

若用户要拆已有产品、做竞品分析、或先判断「值不值得做」：先调用 `/ai-pm-teardown`，等结论是「值得做 / 条件做」再进入下面 4 步。拆解不是本工作流的第 0 步强制项——用户明确说「直接开工」可以跳过。

严格按顺序执行以下 4 个子 Skill，每步完成后向用户汇报关键产出，并确认是否继续：

### 步骤 1：想法澄清
调用 `/ai-pm-idea-clarify`。
目标：用 AI PM 方法论把模糊想法收敛为产品定位。

### 步骤 2：方案设计
调用 `/ai-pm-solution-design`。
目标：确定模型选型、Agent/RAG 架构、MCP/Skills 设计、评估指标。

### 步骤 3：Prompt 生成
调用 `/ai-pm-prompt-consultant`。
目标：生成可直接交给 Cursor / Claude Code / v0 的 AI 产品专用 Vibe Coding Prompt。

### 步骤 4：项目骨架
调用 `/ai-pm-project-scaffold`。
目标：生成 PRD.md / Tech Design.md / AGENTS.md / 评估计划.md / _PROGRESS.md。

## 可选增强：Obsidian 知识库联动

如果用户提供了 Obsidian 知识库中的相关 wiki 页或 raw 笔记，在步骤 1 前先读取这些页面，把已有知识纳入想法澄清。

读取范围建议：
- `wiki/concepts/` 中相关概念页
- `wiki/synthesis/` 中相关综合页
- `02_周期笔记/` 中相关复盘笔记

## 执行规则

1. **每步确认**：每完成一步，向用户展示"一句话摘要 + 关键产出清单"，并询问"是否继续下一步"或"是否需要在这里调整"。
2. **跳过机制**：如果用户明确说"跳过某步"，则跳过该步骤并在 `_PROGRESS.md` 中记录原因。
3. **回退机制**：如果用户说"回到上一步"，则回到上一步重新执行。
4. **输出位置**：所有文件默认写入当前项目根目录。如果项目根目录不存在，先询问用户创建路径。
5. **中文优先**：所有生成文档的正文使用中文，但技术术语、代码变量、文件路径、API 名称保留英文。

## 异常处理

- **用户想法过模糊**：让 `ai-pm-idea-clarify` 先追问，不强行进入下一步。
- **用户已有 PRD**：跳过 `ai-pm-project-scaffold` 的 PRD 部分，只生成 Tech Design 和 AGENTS.md。
- **用户只想要 Prompt**：只执行步骤 1–3，然后结束。
- **用户只想要方案设计**：只执行步骤 1–2，然后结束。
- **用户其实在问值不值得做**：改走 `ai-pm-teardown` 模式 B，不要在本工作流里编一份假账。

## 输出文件清单

工作流全部完成后，项目根目录应包含：

```text
project-root/
├── docs/
│   ├── PRD.md
│   ├── TECH_DESIGN.md
│   └── EVALUATION_PLAN.md
├── AGENTS.md
└── _PROGRESS.md
```
