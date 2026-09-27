# AI Learning Roadmap — v0.1

> 状态：Initial Roadmap  
> 版本：v0.1  
> 上位文件：Anchor_v0.3.md  
> 性质：阶段规划文件  
> 作用：定义学习阶段、模块顺序、依赖关系、阶段目标与完成判据。  
> 本文件不承担单模块的详细教学内容；具体课程进入对应 Module Spec。

---

## 1. Roadmap 总原则

本 Roadmap 遵循以下路径：

> 表达与文档基础  
> → AI / LLM 基础认知  
> → Human–AI Communication / Task Specification  
> → Prompt / Structured Output / Tool Use  
> → Agent  
> → Context Engineering  
> → Evaluation  
> → RAG / Retrieval  
> → AI Systems Engineering  
> → AI-Assisted Software Engineering  
> → AI-native ProjectVox 实践

学习不以“把所有理论先学完再实践”为目标。

默认采用：

> 概念理解 → 最小实验 → 独立输出 → Review → 修正 → 迁移

每个阶段允许根据实际掌握情况调整节奏。

---

# Phase 0 — 表达与技术文档基础

## M0 — Markdown 与技术文本基础

### 目标

建立后续所有技术沟通、Prompt、ADR、问题树、实验报告和项目文档的基本表达能力。

### 必须掌握

- 标题层级；
- 无序列表与有序列表；
- 加粗 / 斜体；
- 行内代码；
- fenced code block；
- 引用；
- 分隔线；
- 链接；
- 表格；
- checkbox；
- 转义；
- 常见嵌套；
- GitHub Flavored Markdown 基础；
- 相对路径与文档链接；
- Markdown 在 Git diff 中的表现。

### 应有所涉猎

- Mermaid；
- Markdown lint；
- Markdown 中嵌 HTML；
- README 常见结构；
- 面向 AI 读取的结构化 Markdown。

### 作业

至少完成：

- 一份结构清晰的 Markdown 技术笔记；
- 一份简短 README；
- 一份问题树；
- 一份包含代码块、表格和链接的技术说明；
- 对一份低质量 Markdown 文档进行重构。

### 完成判据

学习者能够：

- 不依赖模板写出结构清晰的 `.md` 文件；
- 正确使用标题、列表、代码块和引用；
- 用 Markdown 表达层级与依赖关系；
- 看懂 Git 中 Markdown 文档的 diff；
- 发现常见结构混乱与格式问题。

---

# Phase 1 — AI / LLM 基础认知

## M1 — AI、机器学习与大模型全景

### 目标

建立“AI 到底是什么”的整体地图，避免只会使用产品但不知道技术层级。

### 核心内容

- AI / ML / Deep Learning / Foundation Model 的关系；
- 训练、推理、微调；
- 模型、数据、算力；
- 生成式 AI；
- LLM 的基本能力与限制；
- 云模型与本地模型；
- 模型版本、能力、成本与延迟。

### 作业

- 自己绘制 AI 技术层级图；
- 用自己的话解释“模型训练”和“模型推理”的区别；
- 对若干常见 AI 术语进行分类。

---

## M2 — Token、Context 与生成

### 目标

理解大模型输入输出的基本运行单位和上下文机制。

### 核心内容

- token；
- tokenizer；
- context window；
- prompt / completion；
- sampling；
- temperature；
- top-p；
- deterministic 与 probabilistic generation；
- hallucination；
- context limitation。

### 必做实验

- 观察不同文本的 tokenization；
- 比较不同 sampling 参数的输出；
- 构造上下文缺失 / 上下文污染实验。

### 完成判据

能够解释：

- 为什么模型不是“逐字理解”；
- 为什么上下文长度有限；
- 为什么同一 Prompt 不一定得到同样答案；
- 为什么更多上下文不一定更好。

---

## M3 — Embedding 与语义表示基础

### 目标

为后续 Retrieval / RAG 建立必要概念。

### 核心内容

- embedding；
- vector；
- semantic similarity；
- cosine similarity；
- dense representation；
- embedding model 与 generation model 的区别。

### 实验

- 对少量句子计算 embedding；
- 比较相似度；
- 观察语义相近但字面不同的文本。

---

## M4 — Transformer / Attention 工程级理解

### 目标

理解现代大模型的核心结构思想，但不要求默认达到研究级数学深度。

### 核心内容

- sequence；
- attention；
- self-attention；
- Q / K / V 的直觉；
- Transformer block；
- position information；
- pretraining；
- next-token prediction；
- inference。

### 完成判据

能够不用背公式解释：

- attention 在解决什么；
- 为什么 Transformer 适合处理序列；
- LLM 为什么可以表现出复杂能力。

---

# Phase 2 — Human–AI Communication

## M5 — 人机任务表达与上下文设计

### 目标

把自然表达升级为高质量 Human–AI Task Specification。

### 核心内容

- 目标；
- 背景；
- 约束；
- 输入；
- 输出；
- 优先级；
- 验收标准；
- 不确定性；
- 事实 / 假设 / 担忧 / 决策 / 开放问题区分；
- 探索模式与执行模式。

### 重点训练

将：

> “我脑中有很多想法”

转换为：

> “AI 能可靠执行和验证的任务描述”

### 作业

- 把真实聊天输入重构成 Task Specification；
- 对低质量 Prompt 做诊断和改写；
- 给同一任务写“探索版”和“执行版”两种输入；
- 设计验收标准。

---

## M6 — 问题树、分支管理与讨论收敛

### 目标

保留发散能力，同时控制复杂讨论。

### 核心内容

- 主问题；
- 前置问题；
- 阻塞问题；
- 边界问题；
- 延伸问题；
- parking lot；
- discussion stack；
- 分支回收；
- 收敛条件。

### 作业

- 将一个复杂现实问题整理成问题树；
- 在讨论过程中维护主节点和挂起分支；
- 识别“有趣但不阻塞”的问题；
- 完成一次分支回收复盘。

---

## M7 — Prompt Engineering 的科学方法

### 目标

理解 Prompt 的可重复设计方法，而不是积累“神奇提示词”。

### 核心内容

- instruction hierarchy；
- examples / few-shot；
- role / context / constraint；
- decomposition；
- structured prompting；
- prompting failure modes；
- prompt versioning；
- prompt evaluation。

### 必做实验

对同一个任务：

- 改变上下文；
- 改变例子；
- 改变约束；
- 比较输出；
- 记录结果。

---

# Phase 3 — Structured Output 与 Tool Use

## M8 — Structured Output

### 目标

让模型输出可被程序可靠处理的结果。

### 核心内容

- JSON；
- schema；
- validation；
- parsing；
- retry；
- malformed output；
- typed output；
- deterministic interface design。

### 实现

完成一个：

> 自然语言输入 → 结构化输出 → 程序验证

的小项目。

---

## M9 — Tool Calling

### 目标

理解模型如何从“只生成文本”扩展为“调用外部能力”。

### 核心内容

- tool schema；
- argument generation；
- tool result；
- control loop；
- tool error；
- permission；
- idempotency；
- read vs write tools。

### 实现

构建一个具有 2–3 个简单工具的小型 AI assistant。

---

# Phase 4 — Agent Engineering

## M10 — Agent 基础

### 目标

从 tool calling 进入多步任务执行。

### 核心内容

- Agent loop；
- state；
- planning；
- execution；
- observation；
- retry；
- termination；
- failure handling。

### 实现

构建一个能够：

> 接收任务 → 选择工具 → 多步执行 → 判断完成

的最小 Agent。

---

## M11 — Agent 权限、Sandbox 与恢复

### 目标

理解为什么“能执行”不等于“能安全执行”。

### 核心内容

- least privilege；
- sandbox；
- confirmation boundary；
- destructive action；
- reversible action；
- rollback；
- logs；
- checkpoints；
- recovery。

### 作业

为一个代码 Agent 设计权限模型。

---

## M12 — 单 Agent 与多 Agent 协作

### 目标

理解什么时候需要多个 Agent，什么时候只是增加复杂度。

### 核心内容

- role decomposition；
- delegation；
- shared state；
- conflict；
- coordinator；
- reviewer Agent；
- cost / latency；
- emergent failure。

### 实验

比较：

- 单 Agent 完成任务；
- Planner + Executor；
- Executor + Reviewer。

---

# Phase 5 — Context Engineering

## M13 — Context Engineering 基础

### 目标

理解“给模型什么信息”本身就是系统设计问题。

### 核心内容

- context selection；
- context compression；
- relevance；
- stale context；
- conflicting instructions；
- summary；
- working memory；
- long-term state；
- context budget。

### 作业

重构一个上下文臃肿的长期项目输入。

---

## M14 — 长期项目的 AI 上下文架构

### 目标

将 Context Engineering 应用于真实项目。

### 核心内容

- Anchor；
- spec；
- ADR；
- execution state；
- changelog；
- project memory；
- authoritative source；
- source hierarchy；
- handoff。

### 迁移

直接分析 ProjectVox 当前文档结构。

---

# Phase 6 — Evaluation

## M15 — Evaluation 基础

### 目标

建立“AI 输出必须被验证”的核心工程习惯。

### 核心内容

- test case；
- benchmark；
- expected output；
- pass / fail；
- qualitative evaluation；
- quantitative evaluation；
- regression。

### 作业

为一个已有 Prompt 建立最小 eval set。

---

## M16 — Agent Evaluation

### 目标

评价完整任务执行，而不只是单次文本输出。

### 核心内容

- task success；
- partial success；
- failure taxonomy；
- tool failure；
- unsafe action；
- cost；
- latency；
- retries；
- reproducibility。

### 实现

建立一个简单 Agent benchmark。

---

## M17 — LLM-as-Judge 与人工评测

### 目标

理解自动评测的价值与偏差。

### 核心内容

- judge prompt；
- rubric；
- pairwise evaluation；
- bias；
- calibration；
- human review；
- disagreement。

---

# Phase 7 — Retrieval / RAG

## M18 — Retrieval 基础

### 目标

理解从文档集合中找到相关信息的完整链路。

### 核心内容

- chunking；
- indexing；
- embedding；
- vector search；
- keyword search；
- hybrid search；
- recall；
- precision；
- reranking。

---

## M19 — RAG 最小系统

### 实现目标

构建：

> 文档 → chunk → embedding → retrieval → context → LLM answer → citation

的完整最小 RAG。

---

## M20 — RAG 失败模式与评测

### 核心内容

- chunk 太大 / 太小；
- retrieval miss；
- noisy retrieval；
- stale document；
- wrong citation；
- answer hallucination；
- retrieval evaluation；
- answer evaluation。

---

# Phase 8 — AI Systems Engineering

## M21 — 模型 API 与服务设计

### 核心内容

- API；
- authentication；
- request / response；
- streaming；
- retry；
- rate limit；
- timeout；
- cost tracking；
- model selection。

---

## M22 — Local Models 与 Inference 基础

### 核心内容

- model weights；
- VRAM；
- inference；
- quantization；
- context length；
- throughput；
- latency；
- local vs cloud。

### 目标

能判断什么时候本地模型有意义，而不是机械追求本地部署。

---

## M23 — Caching、Routing 与成本工程

### 核心内容

- prompt caching；
- semantic caching；
- model routing；
- cheap model / strong model；
- fallback；
- batching；
- cost-quality trade-off。

---

## M24 — Observability 与 AI 系统调试

### 核心内容

- logs；
- traces；
- tool history；
- prompt version；
- model version；
- latency；
- token usage；
- failure trace；
- reproducibility。

---

## M25 — Fine-tuning / LoRA：什么时候值得训练

### 目标

知道什么时候应该微调，什么时候 RAG / Prompt / Tool 已经足够。

### 核心内容

- fine-tuning；
- supervised fine-tuning；
- LoRA；
- dataset；
- overfitting；
- eval；
- training cost；
- deployment trade-off。

---

# Phase 9 — AI-Assisted Software Engineering

## M26 — AI Coding Workflow

### 目标

建立可靠的 AI 代码协作流程。

### 核心内容

- task spec；
- repo context；
- diff；
- test；
- review；
- rollback；
- incremental change；
- commit boundary；
- code ownership。

### 迁移

直接应用于 ProjectVox 的非关键小任务。

---

## M27 — AI Code Review 与 Debugging

### 核心内容

- AI 生成代码常见错误；
- hidden assumption；
- incomplete fix；
- silent regression；
- dependency change；
- performance bug；
- security issue。

### 作业

定期审查故意带缺陷的 AI 代码。

---

## M28 — AI-native Repository Design

### 目标

让项目结构同时适合人类和 Agent 理解。

### 核心内容

- clear module boundary；
- authoritative docs；
- invariant；
- tests；
- local spec；
- machine-readable metadata；
- safe task boundary；
- automated verification。

---

# Phase 10 — 综合实践

## M29 — AI Mini Project

独立完成一个中等规模 AI 系统。

必须至少包含：

- structured output；
- tool use；
- context；
- evaluation；
- logging；
- failure handling。

---

## M30 — AI-native ProjectVox Integration

### 目标

将前述能力有控制地迁移到 ProjectVox。

候选方向：

- ProjectVox 文档检索 Agent；
- ADR / spec assistant；
- code review Agent；
- benchmark assistant；
- issue decomposition；
- automated test assistant；
- safe repository modification workflow。

任何进入 ProjectVox 正式流程的 AI 工作流必须先经过独立验证。

---

# 2. 阶段性闭卷输出

每完成一个 Phase，应进行一次新的、未直接练习过的综合任务。

闭卷输出应至少测试：

- 概念解释；
- 任务分解；
- 方案设计；
- 风险识别；
- 评测设计；
- 独立输出；
- 对陌生约束的迁移能力。

不得只以“模块内容已讲完”判定 Phase 完成。

---

# 3. 与 ProjectVox 的节奏关系

AI Learning Project 与 ProjectVox 并行。

建议原则：

- 不要求每日平均分配时间；
- 某一阶段可短期集中学习；
- AI 项目不得长期阻塞 ProjectVox；
- ProjectVox 中出现真实 AI 工程需求时，可提前调用相关知识；
- 尚未系统学习的高级 AI 工作流不得直接成为 ProjectVox 核心依赖。

---

# 4. 当前优先执行顺序

当前从：

> **M0 — Markdown 与技术文本基础**

开始。

M0 完成后依次进入：

> M1 → M2 → M3 → M4

完成 Phase 1 后，再进入 Human–AI Communication 主线。

不建议现在提前展开 RAG、Agent 多智能体或 Fine-tuning 细节。

---

# 5. Roadmap 升级规则

普通课程顺序微调、练习调整、模型或工具版本变化不要求升级 Roadmap 主版本。

以下情况可考虑升级：

- 阶段依赖发生明显改变；
- 新技术使核心模块顺序失效；
- 学习目标发生长期变化；
- ProjectVox 对 AI 能力的实际需求显著改变；
- 某阶段被证明过深、过浅或缺失关键能力。

---

# 6. v0.1 冻结说明

v0.1 建立首版完整学习路线。

下一步应创建：

> **M0_Module_Spec_v0.1.md**

用于正式启动第一学习模块。

Roadmap 后续不承担 M0 的具体教学内容和逐课安排。
