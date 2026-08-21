# AI PM Skills for Cursor

一套中文 AI 产品经理专用的 Cursor Agent Skills，覆盖两条链：**先拆清楚值不值得做**，再从想法做到可执行方案。

> **定位**：不是通用 Vibe Coding 项目套件，而是"把领域经验封装成 AI 产品"的专用工作流。

---

## 适用人群

- 想做一个 AI 产品、Agent 或 RAG 应用的人
- 从传统行业转型 AI PM，需要把领域经验产品化的人
- 希望用中文输出 PRD、技术设计和 AGENTS.md 的人

---

## 工作流

```text
已有产品 / 竞品 / 「值不值得做」
    ↓
[ai-pm-teardown] 5W2H Max 拆解（21 格 + UE + 竞争象限）
    ↓ 结论是值得做
用户想法（模糊）
    ↓
[ai-pm-idea-clarify] 想法澄清
    ↓
[ai-pm-solution-design] 方案设计
    ↓
[ai-pm-prompt-consultant] Prompt 生成
    ↓
[ai-pm-project-scaffold] 项目骨架
```

---

## 安装方法

### 方法 1：Cursor 内置导入（推荐）

1. 打开 Cursor → 侧边栏 **Customize**
2. 进入 **Rules** → 点击 **Add Rule**
3. 选择 **Remote Rule (GitHub)**
4. 输入仓库地址：`https://github.com/AndyLiangliang/ai-pm-skills`
5. 选择你想要导入的技能

### 方法 2：手动复制

```bash
git clone https://github.com/AndyLiangliang/ai-pm-skills.git /tmp/ai-pm-skills
cp -r /tmp/ai-pm-skills/skills/* ~/.cursor/skills/
```

---

## 技能清单

| Skill | 触发方式 | 作用 |
|---|---|---|
| `/ai-pm-teardown` | 单独 / 开工前闸门 | 用 5W2H Max 拆产品、拆项目、算可行性与竞争象限 |
| `/ai-pm-project-kit` | 主调度 | 启动完整开工工作流 |
| `/ai-pm-idea-clarify` | 子步骤 / 单独 | 用判断优先 + 五层链澄清 AI 产品想法 |
| `/ai-pm-solution-design` | 子步骤 / 单独 | 模型选型、Agent/RAG 架构、评估指标 |
| `/ai-pm-prompt-consultant` | 子步骤 / 单独 | 生成 AI 产品专用 Vibe Coding Prompt |
| `/ai-pm-project-scaffold` | 子步骤 / 单独 | 生成 PRD / Tech Design / AGENTS.md / 评估计划 / _PROGRESS.md |

---

## 中文触发示例

除了 `/` 命令，也可以用自然语言触发。拆解走 `/ai-pm-teardown`，开工走 `/ai-pm-project-kit`。

拆解链：

- "拆一下这个产品"
- "这个想法值不值得做"
- "帮我做竞品分析"
- "算一下商业可行性"

开工链：

- "我要做一个 AI 产品"
- "设计一个 Agent"
- "做一个 RAG 项目"
- "启动一个 AI 项目"
- "把 AI 加到 [某个场景]"

---

## 核心方法论

本套 Skill 嵌入以下 AI PM 方法论：

- **5W2H Max**：企业 21 格 + 用户校验；🟢可观测 / 🟡可推断 / 🔴不可知
- **可行性链**：首尾两端 → UE → 回本与流量匹配
- **判断优先协议**：已知领域先让用户预判，再让 AI 补充挑战
- **框架前置-五层分析链**：从问题验证 → 行业探索 → 公司诊断 → 产品评估 → 用户行为
- **WVFSL Prompt 框架**：What / Vibe / Stack / Features / Limit
- **模型选型-三看一测**：看榜单 → 看数据 → 看客户 → 实测
- **AI 产品评估三层体系**：在线监控 → 离线评估 → 风险分级
- **AI-Native 创业四阶段生命周期**：想法 → MVP → 发布 → 规模化

---

## 项目结构

```text
AndyLiangliang/ai-pm-skills/
├── README.md
├── .gitignore
└── skills/
    ├── ai-pm-teardown/
    ├── ai-pm-project-kit/
    ├── ai-pm-idea-clarify/
    ├── ai-pm-solution-design/
    ├── ai-pm-prompt-consultant/
    └── ai-pm-project-scaffold/
```

---

## 使用建议

1. 要拆竞品或判断值不值得做：先用 `/ai-pm-teardown`，不要直接开工。
2. 已经确认值得做：安装 `/ai-pm-project-kit`，用完整工作流跑一个真实项目。
3. 如果只想做某一步，可以直接调用对应子 Skill。
4. 如果项目根目录已有 `PRD.md` 等文件，子 Skill 会提示避免覆盖。

---

## 贡献与反馈

如果你在使用过程中发现某个 Skill 的输出不够贴合中文 AI PM 场景，欢迎提 Issue 或 PR。

---

## License

MIT
