---
name: ai-pm-prompt-consultant
description: 为 AI 产品生成可复制的 Vibe Coding Prompt。当用户说"生成 AI 项目 Prompt"、"写 Vibe Prompt"、"把这个 AI 方案变成 Prompt"或作为主调度工作流第三步时触发。
disable-model-invocation: true
---

# AI PM Vibe Coding Prompt 生成

## 任务

基于 `ai-pm-idea-clarify` 和 `ai-pm-solution-design` 的输出，生成一份可直接交给 AI 编码工具（Cursor Composer、Claude Code、v0、Windsurf）的最终 Vibe Coding Prompt。

## 输入

- 产品定位（目标用户、核心问题、差异化）
- MVP 范围（做与不做）
- 技术方案（模型选型、架构、工具层、评估指标）
- 可选：用户指定的视觉风格或参考产品

## 执行流程

1. **按 WVFSL 框架组织 Prompt**
   - **What**：解决什么问题，为谁解决
   - **Vibe**：视觉风格、交互风格、语气调性
   - **Stack**：技术栈（前端、后端、数据库、模型 API）
   - **Features**：MVP 核心功能列表
   - **Limit**：明确不做哪些功能

2. **把 AI 架构信息嵌入 Prompt**
   - 模型选型与使用场景
   - RAG/Agent 架构要点
   - MCP/Skills/Function-Calling 设计
   - 关键评估指标和埋点

3. **从视觉风格库推荐风格**
   如果用户没有指定，推荐 1–3 种视觉风格，并说明理由。

4. **输出最终可复制 Prompt**
   最终 Prompt 必须是完整的一段话，可以直接粘贴使用。

## 输出格式

```markdown
# AI 产品 Vibe Coding Prompt — [产品名]

## 需求理解
[一句话总结]

## 产品定位
- 目标用户：
- 核心问题：
- 差异化：

## MVP 范围
- 做：
- 不做：

## 页面结构
1. ...
2. ...
3. ...

## 功能模块
- 模块 A：...
- 模块 B：...

## 用户流程
触发 → 步骤 → 成功/失败

## AI 能力设计
- 模型选型：
- RAG/Agent 架构：
- MCP/Skills 设计：
- 评估指标：

## 数据结构
- 实体：
- 关键字段：

## 技术栈建议
- 前端：
- 后端：
- 数据库：
- 模型 API：
- 部署：

## UI 风格
[视觉风格关键词 + 参考产品]

## 最终 Vibe Coding Prompt（可复制）
```text
[完整 Prompt，包含 WVFSL 全部要素]
```
```

## 约束

- 最终 Prompt 必须是完整的一段话，可直接粘贴到 Cursor Composer / Claude Code / v0 / Windsurf。
- 必须包含 AI 架构和评估指标，不能只是通用 UI 描述。
- 必须明确写出 MVP 不做哪些功能，避免范围蔓延。
- 中文用户场景下，Prompt 可以保留中文描述，但代码变量名、API 名称、文件路径保留英文。

## 参考

- 完整 WVFSL 模板见 `references/wvfsl-template.md`
- 视觉风格库参考：`wiki/concepts/视觉风格库`（如果用户有 Obsidian 知识库）
