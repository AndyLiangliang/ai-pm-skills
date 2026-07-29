# AI PM 项目启动工作流 — 详细指南

## 工作流总览

```text
用户想法
    ↓
[ai-pm-idea-clarify] 想法澄清
    ↓
[ai-pm-solution-design] 方案设计
    ↓
[ai-pm-prompt-consultant] Prompt 生成
    ↓
[ai-pm-project-scaffold] 项目骨架
```

## 每个阶段的目标

### 阶段 1：想法澄清

- 把模糊想法变成"为谁解决什么问题"
- 输出产品定位、MVP 边界、关键假设
- 使用判断优先协议 + 五层分析链 Layer 1

### 阶段 2：方案设计

- 确定 AI 产品类型（RAG/Agent/嵌入式/多 Agent）
- 完成模型选型（三看一测）
- 设计架构和评估指标

### 阶段 3：Prompt 生成

- 按 WVFSL 组织最终 Prompt
- 把 AI 架构和评估指标嵌入 Prompt
- 输出可直接复制给 Cursor / Claude Code / v0 的 Prompt

### 阶段 4：项目骨架

- 生成 PRD.md / Tech Design.md / AGENTS.md / 评估计划.md
- 生成 _PROGRESS.md 作为检查点

## 何时使用完整工作流

- 从零开始一个 AI 项目
- 只有一个模糊想法，需要系统梳理
- 需要生成可交付的文档包

## 何时只使用子 Skill

| 场景 | 使用 |
|---|---|
| 已有想法，需要验证 | `/ai-pm-idea-clarify` |
| 已有定位，需要技术方案 | `/ai-pm-solution-design` |
| 已有方案，需要编码 Prompt | `/ai-pm-prompt-consultant` |
| 已有方案，需要项目文档 | `/ai-pm-project-scaffold` |

## 与 Obsidian 知识库联动

如果用户有 Obsidian 知识库，主调度可以在步骤 1 前读取相关页面：

- 读取 `00.meta/用户档案.md` 了解用户背景
- 读取 `wiki/concepts/` 中相关概念（如模型选型、Agent 架构）
- 读取 `wiki/synthesis/` 中相关综合页
- 读取 `02_周期笔记/` 中相关复盘笔记

注意：公开 Skill 不能假设用户一定有 Obsidian 知识库，所以这一步是可选增强，不是强制步骤。

## 执行注意事项

1. 每步结束后必须确认用户是否继续。
2. 不要自动覆盖已有文件。
3. 如果用户中途改变方向，允许回退到上一步。
4. 所有输出以中文为主，技术术语保留英文。
