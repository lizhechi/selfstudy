# M1 — AI、机器学习与大模型全景 — Module Spec v0.1

> 项目：AI Learning Project  
> 模块：M1 — AI、机器学习与大模型全景  
> 版本：v0.1  
> 上位文件：
> - `Anchor_v0.3.md`
> - `Roadmap_v0.1.md`
>
> 性质：模块级教学规格  
> 作用：定义 M1 的学习目标、范围、教学方式、必做练习、完成判据与收尾要求。  
> 本文件不得覆盖或修改 Anchor / Roadmap 中的长期原则。

---

## 1. 模块定位

M1 是 AI Learning Project 进入 AI / LLM 基础认知主线后的第一个正式模块。

目标不是立刻深入 Transformer 数学、训练工程或模型 API，而是先建立一张稳定的“AI 技术全景地图”，使学习者能够区分：

- AI；
- Machine Learning；
- Deep Learning；
- Foundation Model；
- Generative AI；
- Large Language Model；
- 训练；
- 推理；
- 微调；
- 云模型；
- 本地模型。

M1 的核心任务是建立概念层级、技术边界和基本工程判断，避免后续学习中只会使用产品，却无法判断不同术语、技术层级和系统组件之间的关系。

M1 应保持“全景优先、细节适度”的原则。

对于 Token、Context、Embedding、Transformer / Attention 等内容，仅建立必要的前置认知；它们分别在 M2、M3、M4 中系统展开。

---

## 2. 学习目标

完成 M1 后，学习者应能够建立一张基本正确的 AI 技术地图，并用自己的语言解释主要概念之间的关系。

重点能力包括：

1. 区分 AI、Machine Learning、Deep Learning、Foundation Model、Generative AI 与 LLM；
2. 理解“模型、数据、算力”在现代 AI 系统中的基本关系；
3. 区分训练、推理与微调；
4. 理解生成式 AI 与传统分类、回归、检测等机器学习任务在目标形式上的基本差异；
5. 初步理解 LLM 的能力与主要限制；
6. 区分云模型与本地模型的基本特征；
7. 初步理解模型版本、能力、成本、延迟与部署方式之间存在 trade-off；
8. 能对常见 AI 术语进行基本分类，不把产品名、模型名、技术范式和系统能力混为一谈；
9. 能识别常见 AI 直觉误区，并用更准确的技术语言重述。

---

## 3. 前置要求

默认已完成：

> M0 — Markdown 与技术文本基础

学习者应能够：

- 使用 Markdown 记录技术笔记；
- 使用标题与列表表达层级；
- 完成简单技术说明；
- 使用问题树管理分支问题；
- 对自己的理解进行简短书面解释。

M1 不要求：

- 高等数学；
- 线性代数系统知识；
- 概率论系统知识；
- 神经网络训练经验；
- Python 深度学习框架经验；
- GPU / CUDA 知识；
- API 调用经验；
- Transformer 数学推导能力。

---

## 4. 必须理解的内容

### 4.1 AI / ML / Deep Learning 的层级关系

必须理解：

- Artificial Intelligence 是更宽泛的概念；
- Machine Learning 是 AI 的重要实现路径之一；
- Deep Learning 是 Machine Learning 中以多层神经网络为核心的一类方法；
- 并非所有 AI 都是 Machine Learning；
- 并非所有 Machine Learning 都是 Deep Learning。

目标：

> 能画出基本层级关系，并解释为什么这些概念不能互相完全等同。

### 4.2 Foundation Model

必须建立对 Foundation Model 的工程级理解。

重点包括：

- Foundation Model 不是“某一个具体产品”的同义词；
- 它通常通过大规模数据预训练，获得可迁移到多任务的通用能力；
- 下游能力可以通过 Prompt、Tool Use、RAG、Fine-tuning 等方式扩展或适配；
- LLM 是 Foundation Model 的重要类型之一，但 Foundation Model 不只包含语言模型；
- 多模态模型也可属于 Foundation Model 范畴。

M1 不要求深入预训练算法、loss function 或 scaling law。

### 4.3 Generative AI

必须理解生成式 AI 的基本定位：

- 根据输入条件生成新内容；
- 输出可以是文本、图像、音频、视频、代码或其他结构；
- 生成式 AI 与分类、回归、检测等传统机器学习任务存在任务形式差异；
- “生成”不代表模型拥有与人类相同的理解机制。

### 4.4 Large Language Model

必须理解：

- LLM 是以语言序列建模为核心的大规模模型；
- LLM 可以表现出问答、总结、翻译、代码、推理辅助等能力；
- LLM 不等于 ChatGPT 等具体产品；
- 一个 AI 产品可能包含模型、系统提示、工具、检索、记忆、权限、UI、后端服务等多个部分；
- 模型能力不等于整个产品能力。

M1 只建立整体理解。

Token、Context、Sampling 在 M2 展开；Transformer / Attention 在 M4 展开。

### 4.5 模型、数据与算力

必须理解现代 AI 系统中的三个基本要素：

- 模型；
- 数据；
- 算力。

重点包括：

- 模型参数来自训练，而不是人工逐条写入知识；
- 训练数据会影响模型学习到的模式与覆盖范围；
- 算力影响训练与推理规模、速度与成本；
- 三者相互约束，不应把模型能力简单归因于其中单一因素。

不要求在 M1 学习具体 GPU 架构或分布式训练。

### 4.6 训练、推理与微调

必须能够区分：

#### Training

模型通过数据和优化过程调整参数。

#### Inference

使用已经训练好的模型，根据输入产生输出。

#### Fine-tuning

在已有模型基础上继续针对特定数据或任务进行训练，使行为发生针对性变化。

学习者必须理解：

- 与 ChatGPT 对话通常属于推理，不是在现场重新训练基础模型；
- 把信息放入上下文，不等于写入模型参数；
- Fine-tuning 不等同于 Prompt；
- 训练与推理在目标、资源消耗和系统行为上不同。

### 4.7 云模型与本地模型

必须建立基本对比框架。

云模型通常涉及：

- 远程服务；
- API / 在线产品；
- 服务商维护基础设施；
- 网络依赖；
- 成本、隐私、延迟、可用性等 trade-off。

本地模型通常涉及：

- 权重在本地设备或自有服务器运行；
- 受本地硬件资源限制；
- 可提高某些数据控制能力；
- 不代表天然更安全、更便宜或更强。

M1 不进行实际本地部署；该内容在 M22 深入。

### 4.8 能力、成本、延迟与版本

必须理解：

- 更强模型通常可能伴随更高成本或延迟，但不是绝对规律；
- 不同模型适合不同任务；
- 同一产品可能使用多个模型或路由策略；
- 模型版本变化可能改变能力、价格、速度和行为；
- 工程上应根据任务需求选择模型，而不是默认“越大越好”。

M1 不要求进行正式 benchmark，但应建立 trade-off 意识。

### 4.9 LLM 的基本能力与限制

能力侧可包括：

- 文本生成；
- 总结；
- 改写；
- 分类；
- 信息提取；
- 代码辅助；
- 多轮交互；
- 在一定条件下完成复杂推理与任务分解。

限制侧至少包括：

- 可能生成错误信息；
- 不能默认把输出当作已验证事实；
- 受输入上下文限制；
- 对模糊任务可能自行补充假设；
- 能力受模型、系统、工具和上下文共同影响；
- 输出质量不等于事实正确性。

Hallucination 与 Context limitation 在 M2 继续深入。

---

## 5. 应有所涉猎的内容

以下内容在 M1 仅建立存在感与定位，不系统展开：

- supervised learning；
- unsupervised learning；
- reinforcement learning；
- neural network 基础；
- parameters / weights；
- pretraining；
- post-training；
- RLHF / RLAIF；
- multimodal model；
- reasoning model；
- mixture of experts；
- quantization；
- API；
- inference serving；
- RAG；
- Agent；
- tool calling；
- model routing。

这些内容只在需要解释全景关系时简短出现。

---

## 6. 教学方式

M1 应遵循：

> 概念地图 → 对比 → 例子 → 反例 → 独立解释 → 分类练习 → Review → 修正 → 综合迁移

### 6.1 先建立地图，再深入细节

M1 不应一开始就进入 Transformer 公式、tokenizer 实现或 API。

优先回答：

- 这个概念属于哪一层？
- 与相邻概念是什么关系？
- 它解决什么问题？
- 它不是什么？

### 6.2 强调“区别”而不是只背定义

重要概念应通过成对或成组比较建立理解，例如：

- AI vs ML；
- ML vs Deep Learning；
- Foundation Model vs LLM；
- LLM vs ChatGPT / AI 产品；
- Training vs Inference；
- Prompt vs Fine-tuning；
- Cloud Model vs Local Model。

### 6.3 主动暴露误区

教学中应主动提供：

- 看似正确但有问题的说法；
- 概念混用；
- 产品与模型混淆；
- “对话就是训练模型”等典型误解。

要求学习者判断并修正。

### 6.4 使用真实产品作例子，但不绑定产品

可以使用 ChatGPT、Claude、Gemini、本地模型等作为例子。

但重点必须回到可迁移概念，不把课程变成产品说明书。

### 6.5 不追逐最新模型榜单

M1 可使用当前模型作为案例，但不以最新模型排名、产品营销或 benchmark 榜单作为课程主线。

若涉及快速变化的模型、产品或价格，应视为案例，不升级为稳定项目知识。

---

## 7. 必做练习

### Exercise 1 — AI 技术层级图

学习者独立用 Markdown / 文本树表达至少以下概念：

- AI；
- Machine Learning；
- Deep Learning；
- Foundation Model；
- LLM；
- Generative AI。

要求：

- 不要求唯一树形结构；
- 必须说明哪些是严格包含关系；
- 哪些概念存在交叉而非简单上下级。

目标：

> 防止把所有 AI 术语误认为一条单一线性层级。

### Exercise 2 — 术语分类

由 ChatGPT 提供一组术语，例如：

- ChatGPT；
- GPT 类模型；
- LLM；
- Machine Learning；
- inference；
- fine-tuning；
- RAG；
- API；
- local model。

学习者独立分类：

- 技术领域 / 范式；
- 模型类型；
- 具体模型；
- 产品 / 应用；
- 训练 / 推理过程；
- 系统组件或工程方法。

目标：

> 建立“产品 ≠ 模型 ≠ 技术范式 ≠ 系统组件”的区分。

### Exercise 3 — Training / Inference / Fine-tuning

学习者用自己的语言解释：

- Training 是什么；
- Inference 是什么；
- Fine-tuning 是什么；
- 三者之间的关系；
- 与 ChatGPT 对话时通常发生的是哪一种。

要求：

- 不照抄定义；
- 至少给一个错误理解并进行纠正。

### Exercise 4 — 模型、数据、算力关系

给出若干情境，由学习者判断主要涉及：

- 模型能力；
- 数据覆盖；
- 训练 / 推理算力；
- 系统工程限制；
- 或多因素共同作用。

目标：

> 避免“模型不好 / 数据不好 / 算力不够”成为无差别解释。

### Exercise 5 — 云模型 vs 本地模型

学习者建立一份对比说明，至少包含：

- 部署位置；
- 硬件依赖；
- 网络依赖；
- 数据控制；
- 成本；
- 延迟；
- 维护负担；
- 适用场景。

并解释：

> 为什么“本地模型一定更安全 / 更便宜 / 更快”是不可靠的绝对判断。

### Exercise 6 — AI 输出诊断

ChatGPT 提供若干典型说法，例如：

- “ChatGPT 每次和我聊天都会重新训练模型。”
- “LLM 就等于 AI。”
- “模型越大一定越适合所有任务。”
- “本地模型不会泄露数据，所以一定安全。”
- “能生成正确格式就代表答案正确。”

学习者逐条判断：

- 正确；
- 部分正确；
- 错误；
- 为什么。

---

## 8. 综合作业

### M1 Final Assignment — AI 技术全景说明

学习者在不直接照抄课程模板的情况下，独立完成一份：

> **面向“会使用 AI 产品，但没有系统 AI 技术背景的人”的 AI 技术全景说明**

文档必须至少覆盖：

- AI / ML / Deep Learning 的关系；
- Foundation Model；
- Generative AI；
- LLM；
- 模型与产品的区别；
- 模型、数据、算力；
- Training / Inference / Fine-tuning；
- Cloud Model / Local Model；
- 能力、成本、延迟之间的基本 trade-off；
- LLM 至少三项能力与三项限制。

必须包含：

- 一张学习者自行组织的概念层级图或关系图；
- 至少两个容易混淆概念的对比；
- 至少一个“常见误解 → 修正解释”；
- 一个清晰的总结。

主题结构由学习者自行设计，不提供完整模板。

---

## 9. Review 标准

ChatGPT Review 时重点检查：

### 9.1 概念正确性

- 是否混淆 AI / ML / Deep Learning；
- 是否把 Foundation Model 与 LLM 完全等同；
- 是否把模型与产品等同；
- 是否混淆 Training / Inference / Fine-tuning；
- 是否对云模型 / 本地模型做绝对化判断。

### 9.2 层级关系

- 是否能区分包含关系、交叉关系与关联关系；
- 是否把并非严格上下级的概念硬塞进线性树；
- 是否能解释为什么这样组织。

### 9.3 解释能力

- 是否能用自己的语言解释概念；
- 是否只是复述定义；
- 是否能给出例子和反例；
- 是否能说明一个概念“不是什么”。

### 9.4 工程判断

- 是否意识到能力、成本、延迟、部署存在 trade-off；
- 是否避免“越大越好”“本地一定好”“云端一定强”等绝对化判断；
- 是否能区分模型能力与完整 AI 系统能力。

### 9.5 技术表达

- 是否使用 M0 中掌握的结构化 Markdown；
- 是否明确区分事实、解释与开放问题；
- 文档是否能被没有当前聊天上下文的人读懂。

---

## 10. 完成判据

M1 完成时，学习者应能够：

- 用自己的语言解释 AI / ML / Deep Learning；
- 区分 Foundation Model、Generative AI 与 LLM；
- 区分模型、具体产品与完整 AI 系统；
- 正确解释 Training / Inference / Fine-tuning；
- 解释模型、数据与算力之间的基本关系；
- 对云模型和本地模型做非绝对化比较；
- 初步说明 LLM 的能力与限制；
- 识别至少数种典型 AI 概念混用；
- 独立绘制并解释 AI 技术全景图；
- 完成 M1 Final Assignment。

不要求：

- 推导神经网络公式；
- 掌握 Transformer 数学；
- 掌握 tokenizer 细节；
- 掌握 embeddings；
- 掌握模型 API；
- 实际训练大模型；
- 部署本地模型；
- 精确掌握最新模型排名。

---

## 11. 收尾要求

完成 M1 后，应进行一次简短复盘：

1. AI 技术层级是否已经形成稳定心智模型；
2. 哪些术语仍容易混淆；
3. Training / Inference / Fine-tuning 是否能独立解释；
4. 是否能区分模型与产品；
5. 是否能解释云 / 本地模型的主要 trade-off；
6. 是否满足进入 M2 的完成判据。

若满足，则 M1 收尾，不继续扩展。

下一模块：

> **M2 — Token、Context 与生成**

---

## 12. v0.1 冻结说明

M1 Module Spec v0.1 定义首版教学边界。

普通示例、案例、练习题目、教学顺序微调不升级本文件。

只有以下变化才考虑升级：

- M1 学习目标发生变化；
- 必须理解范围明显改变；
- 完成判据改变；
- Roadmap 对 M1 的职责重新定义；
- M1 与 M2 / M3 / M4 的边界发生长期变化。
