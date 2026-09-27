# M2 — Token、Context 与生成 — Module Spec v0.1

> 项目：AI Learning Project  
> 模块：M2 — Token、Context 与生成  
> 版本：v0.1  
> 上位文件：
> - `Anchor_v0.3.md`
> - `Roadmap_v0.1.md`
>
> 性质：模块级教学规格  
> 作用：定义 M2 的学习目标、范围、教学方式、必做实验、练习、完成判据与收尾要求。  
> 本文件不得覆盖或修改 Anchor / Roadmap 中的长期原则。

---

## 1. 模块定位

M2 是 AI Learning Project 在完成 M1“AI、机器学习与大模型全景”之后，进入大语言模型基本运行机制的第一个核心模块。

M2 的目标不是深入 Transformer 数学、Embedding 或模型训练工程，而是建立对以下问题的稳定工程级心智模型：

- 模型为什么不是“逐字读取”文本；
- token 是什么，tokenizer 在做什么；
- prompt / completion 在一次生成中分别是什么；
- context window 为什么有限；
- 为什么更多上下文不一定更好；
- 模型为什么可以在相同输入下产生不同输出；
- sampling、temperature、top-p 如何影响生成；
- deterministic 与 probabilistic generation 的区别；
- hallucination 为什么会发生，以及它与“模型在生成”这一事实的关系；
- context 缺失、污染、冲突与长度限制如何影响输出。

M2 应保持：

> **机制理解优先，工程直觉优先，公式细节适度。**

Tokenization、Context 与 Sampling 是本模块主线。

Embedding 在 M3 系统展开；Transformer / Attention、position information、next-token prediction 的更深层结构在 M4 系统展开。

---

## 2. 学习目标

完成 M2 后，学习者应能够：

1. 用自己的语言解释 token 与 tokenizer；
2. 理解 token 不等于“字”“词”或“字符”；
3. 解释为什么不同语言、文本形式和符号会产生不同 tokenization；
4. 理解 prompt / completion 在生成过程中的基本角色；
5. 解释 context window 的作用与限制；
6. 理解上下文中信息的位置、相关性、冲突和噪声会影响模型表现；
7. 解释为什么更多上下文不一定更好；
8. 理解模型生成具有概率性；
9. 解释 temperature、top-p 对输出分布的大致影响；
10. 区分 deterministic 与 probabilistic generation；
11. 理解同一 Prompt 不一定得到完全相同输出；
12. 建立对 hallucination 的基础机制认知；
13. 能设计最小实验观察 tokenization、sampling 和 context failure；
14. 能对常见“上下文越长越好”“temperature 越低越正确”等误区进行诊断。

---

## 3. 前置要求

默认已完成：

> M1 — AI、机器学习与大模型全景

学习者应已经能够：

- 区分模型与产品；
- 区分 Training / Inference / Fine-tuning；
- 理解 LLM 是模型类型，不等于完整 AI 产品；
- 理解模型输出需要验证；
- 理解模型能力与系统能力并不等同；
- 使用 Markdown 完成基础技术记录和实验说明。

M2 不要求：

- Transformer 数学；
- Attention / QKV；
- Embedding；
- 向量检索；
- 概率论系统知识；
- 深度学习框架；
- API 调用经验；
- 本地模型部署经验。

---

## 4. 必须理解的内容

### 4.1 Token

必须理解：

- token 是模型处理文本时使用的离散单位；
- token 不等于自然语言中的“单词”；
- 一个单词可能对应一个 token，也可能拆成多个 token；
- 一个 token 也可能表示词的一部分、标点、空格模式、字符片段或其他编码单元；
- 中文、英文、代码、数字、特殊符号等文本的 tokenization 可能明显不同；
- token 数量与字符数量、单词数量不存在固定一一对应关系。

目标：

> 能解释为什么模型不是简单“一个字一个字”或“一个词一个词”读取文本。

M2 不要求掌握具体 tokenizer 算法实现。

---

### 4.2 Tokenizer

必须理解：

- tokenizer 负责在原始文本与 token 序列之间进行转换；
- 不同模型可能使用不同 tokenizer；
- tokenizer 会直接影响同一段文本被表示为多少 token；
- tokenization 会影响 context 占用、成本和某些文本处理行为；
- 人类看到的字符串边界与模型看到的 token 边界不一定一致。

应通过实际观察建立直觉，而不是只记定义。

---

### 4.3 Prompt / Completion

必须理解：

- prompt 是模型在当前推理中接收到的输入上下文的一部分；
- completion 是模型在给定当前输入后生成的后续输出；
- 在现代聊天产品中，真实输入通常不只是用户最后一句话，还可能包含：
  - system instruction；
  - developer / application instruction；
  - 历史对话；
  - 工具结果；
  - 检索结果；
  - 文件片段；
  - Memory 或其他上下文；
- 用户看到的输入框并不等于模型实际收到的全部 context。

目标：

> 建立“模型根据当前上下文继续生成”的基本直觉。

---

### 4.4 Context 与 Context Window

必须理解：

- context 是模型当前推理时可利用的信息；
- context window 是模型单次推理中能够处理的 token 总量边界；
- 输入与输出通常共同消耗 context budget；
- context window 有限；
- 超出长度时，系统可能截断、压缩、检索或采用其他策略；
- 模型并不会因为上下文很长就自动稳定利用其中所有信息；
- context window 大不等于长期记忆无限；
- context 与训练进模型参数不是一回事。

M2 不要求深入具体模型的内部 KV cache 或 Attention 计算。

---

### 4.5 Context Relevance 与噪声

必须理解：

- 相关上下文可以提高任务表现；
- 无关信息会增加噪声；
- 陈旧信息可能误导模型；
- 相互冲突的信息会增加错误概率；
- 大量低价值上下文可能掩盖关键约束；
- 重要信息的组织、位置和明确程度会影响模型利用效果。

核心结论：

> **更多上下文不等于更好的上下文。**

---

### 4.6 Context 缺失

必须理解：

当模型缺少完成任务所需的信息时，可能：

- 给出不完整答案；
- 自行补充假设；
- 依靠训练中已有模式猜测；
- 表达不确定性；
- 产生幻觉。

学习者应能区分：

- 模型能力不足；
- 上下文不足；
- 用户任务定义不足；

三者并不相同。

---

### 4.7 Context 污染与冲突

必须理解：

Context failure 可包括：

- 无关信息过多；
- 错误信息被加入上下文；
- 旧版本规范与新版本规范同时存在；
- 多份指令互相冲突；
- 模糊引用导致错误绑定；
- 摘要压缩遗漏关键约束。

M2 只建立机制与观察能力。

Context Engineering 的系统设计在 M13 / M14 深入。

---

### 4.8 Probabilistic Generation

必须理解：

- LLM 的输出生成通常不是简单查表；
- 在每一步生成时，模型会对可能的后续 token 形成概率分布；
- 生成过程可以根据该分布选择后续 token；
- 因此同一 Prompt 可以产生不同输出；
- “概率生成”不等于“完全随机”；
- 输出受模型、上下文、sampling 参数和系统实现共同影响。

M2 不要求推导 softmax 或训练 loss。

---

### 4.9 Temperature

必须建立工程级理解：

- temperature 会影响生成分布的平坦或集中程度；
- 较低 temperature 通常让输出更集中、更稳定；
- 较高 temperature 通常增加多样性和不确定性；
- temperature 不等于“创造力按钮”；
- 低 temperature 不保证事实正确；
- 高 temperature 不等于输出必然混乱。

应通过实际实验观察，而不是只记形容词。

---

### 4.10 Top-p

必须理解：

- top-p 是控制候选 token 范围的一种 sampling 方法；
- 它通常只保留累计概率达到某一阈值的候选集合；
- top-p 与 temperature 都会影响生成，但机制不同；
- 二者不应被理解为完全等价参数。

M2 不要求掌握完整采样算法实现。

---

### 4.11 Deterministic vs Probabilistic Generation

必须理解：

- probabilistic generation 允许输出存在变化；
- deterministic / near-deterministic 设置追求更稳定、可复现的输出；
- 即使设置较稳定，完整系统仍可能因为模型版本、隐藏上下文、工具结果、服务端实现等因素产生差异；
- “相同 Prompt”只有在其他条件也相同的情况下才有可比性。

---

### 4.12 Hallucination

必须建立基础理解：

- hallucination 指模型生成了看似合理但不被事实或给定证据支持的内容；
- 流畅、自信、结构完整不代表事实正确；
- hallucination 与概率生成、训练数据模式、上下文不足、任务模糊、检索错误等因素有关；
- 模型不是在默认执行“事实数据库查询”；
- 检索、工具和更好的上下文可以降低部分 hallucination，但不能自动保证正确；
- 重要输出需要验证。

M2 不深入 Evaluation 方法，该内容在后续模块系统展开。

---

## 5. 应有所涉猎的内容

以下内容在 M2 仅建立存在感，不系统展开：

- tokenizer 的 BPE / WordPiece / SentencePiece 等具体算法；
- byte-level tokenization；
- special tokens；
- logits；
- softmax；
- greedy decoding；
- beam search；
- repetition penalty；
- seed；
- reasoning token；
- hidden token；
- prompt caching；
- KV cache；
- context compression；
- retrieval-augmented context；
- long-context benchmark；
- prompt injection；
- attention sink / lost in the middle 等更具体研究问题。

这些内容仅在解释实验结果时按需简短出现。

---

## 6. 教学方式

M2 应遵循：

> 概念直觉 → 可观察实验 → 独立解释 → 对比 → 失败案例 → Review → 修正 → 综合迁移

### 6.1 先观察，再抽象

Token、sampling 和 context 都应尽量通过实验建立直觉。

优先：

- 观察不同文本如何 tokenization；
- 比较不同 sampling 设置；
- 人为删除关键信息；
- 人为加入无关或冲突上下文；
- 观察输出发生什么变化。

不要只用定义推进课程。

### 6.2 实验结果不是绝对规律

应持续提醒：

- 一次生成结果不能证明普遍规律；
- 不同模型和产品实现可能不同；
- sampling 结果具有随机性；
- context 实验需要控制变量。

目标是建立：

> 假设 → 改变一个变量 → 观察 → 记录 → 比较 → 结论

的最小实验习惯。

### 6.3 不提前进入 Transformer

解释 token / context / generation 时，可以说明更深层机制存在，但不要系统展开：

- Attention；
- Q / K / V；
- Transformer block；
- position encoding。

这些属于 M4。

### 6.4 不把产品 UI 当作模型机制

可使用 ChatGPT 或其他产品做实验，但必须区分：

- 产品界面显示；
- API 参数；
- 模型本身机制；
- 系统级隐藏处理。

实验结论应避免把某个产品行为误认为所有 LLM 的通用规律。

---

## 7. 必做练习与实验

### Exercise 1 — Token 直觉

给出多组文本，例如：

- 简单英文；
- 中文；
- 中英混合；
- 数字；
- 标点；
- 代码；
- 重复字符串。

学习者先预测 token 数量或拆分趋势，再使用 tokenizer 工具观察结果。

要求：

- 不要求精确预测；
- 重点解释为什么字符数 / 单词数与 token 数不一致。

目标：

> 建立 token ≠ 字符 / 单词 的稳定认知。

---

### Exercise 2 — Tokenization 对比记录

选择至少 5 组不同文本，记录：

- 原文本；
- 字符或单词数量；
- token 数量；
- 观察到的拆分特点；
- 一个出乎预期的例子。

输出一份简短 Markdown 实验记录。

---

### Exercise 3 — Context 缺失实验

设计一个需要特定背景信息才能正确回答的问题。

进行两次测试：

1. 不提供关键上下文；
2. 提供关键上下文。

比较：

- 输出准确性；
- 模型是否补充假设；
- 是否表达不确定性；
- 哪些信息实际改变了回答。

目标：

> 区分“模型不会”与“模型没拿到必要信息”。

---

### Exercise 4 — Context 污染实验

构造同一任务的多种上下文：

- 只保留必要信息；
- 加入大量无关信息；
- 加入一条错误信息；
- 加入互相冲突的信息。

观察输出变化。

要求记录：

- 哪类污染影响最大；
- 模型是否识别冲突；
- 是否存在“更多上下文反而更差”的情况。

---

### Exercise 5 — Sampling 对比实验

对同一个 Prompt，在可控制 sampling 参数的环境中比较不同设置。

至少比较：

- 较低 temperature；
- 较高 temperature；
- 不同 top-p 设置。

每种设置运行多次。

观察：

- 输出重复程度；
- 措辞变化；
- 内容多样性；
- 稳定性；
- 是否出现事实质量变化。

目标：

> 用实验理解“概率生成”，而不是把 temperature 简化成“创造力”。

---

### Exercise 6 — 同 Prompt 多次生成

在尽量保持其他条件不变的情况下，对同一 Prompt 多次生成。

回答：

- 哪些部分稳定；
- 哪些部分变化；
- 为什么不能只凭一次结果判断模型行为；
- 哪些任务更需要稳定输出。

---

### Exercise 7 — Hallucination 诊断

由 ChatGPT 提供若干输出案例。

学习者判断主要问题更接近：

- 缺少上下文；
- 错误上下文；
- 模糊任务；
- 模型生成了未经支持的事实；
- 需要外部验证；
- 无法仅凭当前信息判断。

目标：

> 不把所有错误统一叫作 hallucination。

---

## 8. 综合作业

### M2 Final Assignment — Token、Context 与生成实验说明

学习者独立完成一份 Markdown 实验说明，面向：

> “知道 LLM 是什么，但不了解模型为什么会有上下文限制、为什么同一 Prompt 会变化的人。”

文档必须至少包含：

- token 与 tokenizer 的解释；
- 一组实际 tokenization 观察；
- context / context window 的解释；
- 一次 context 缺失或污染实验；
- probabilistic generation 的解释；
- temperature 与 top-p 的基本区别；
- 一次多次生成或 sampling 对比；
- hallucination 的基础解释；
- 至少两个常见误解及修正；
- 一个清晰总结。

必须区分：

- 实验观察；
- 自己的解释；
- 尚不能确定的结论。

不要求：

- 数学推导；
- Transformer 结构图；
- tokenizer 源码实现。

---

## 9. Review 标准

ChatGPT Review 时重点检查：

### 9.1 Token 心智模型

- 是否把 token 等同于字 / 词；
- 是否理解 tokenizer 的角色；
- 是否能解释 token 数与字符数不固定对应。

### 9.2 Context 心智模型

- 是否把 context 等同于长期记忆；
- 是否把 context 注入等同于训练；
- 是否理解 context window 是有限预算；
- 是否理解更多上下文可能带来噪声和冲突。

### 9.3 Generation 心智模型

- 是否理解输出具有概率性；
- 是否把“概率”误解为完全随机；
- 是否把 temperature 简化成“创造力”；
- 是否能基本区分 temperature 与 top-p。

### 9.4 实验质量

- 是否控制变量；
- 是否运行足够次数；
- 是否把单次结果过度概括成普遍规律；
- 是否记录观察与解释的区别。

### 9.5 Hallucination 认知

- 是否把所有错误都叫 hallucination；
- 是否理解流畅性不等于事实性；
- 是否知道需要外部验证。

### 9.6 技术表达

- 是否使用清晰 Markdown；
- 是否明确区分事实、观察、推论与开放问题；
- 文档是否能被没有当前聊天上下文的人理解。

---

## 10. 完成判据

M2 完成时，学习者应能够：

- 用自己的语言解释 token 与 tokenizer；
- 解释为什么模型不是逐字 / 逐词简单读取；
- 解释 context 与 context window；
- 说明为什么 context 长度有限；
- 说明为什么更多上下文不一定更好；
- 识别 context 缺失、污染和冲突；
- 解释同一 Prompt 为什么可能得到不同答案；
- 解释 probabilistic generation；
- 说明 temperature 与 top-p 的基本作用差异；
- 区分较稳定生成与概率生成；
- 解释 hallucination 的基本含义；
- 完成 tokenization 实验；
- 完成 sampling 对比实验；
- 完成 context 缺失 / 污染实验；
- 完成 M2 Final Assignment。

不要求：

- 推导 softmax；
- 掌握具体 tokenizer 算法；
- 掌握 Transformer 数学；
- 掌握 Attention；
- 掌握 Embedding；
- 自己训练语言模型；
- 掌握所有 decoding 参数。

---

## 11. 收尾要求

完成 M2 后，应进行一次简短复盘：

1. token / tokenizer 是否形成稳定心智模型；
2. context 与 context window 是否能独立解释；
3. 是否能解释“更多上下文不一定更好”；
4. sampling / temperature / top-p 是否能用实验结果说明；
5. 是否能解释同 Prompt 输出变化的原因；
6. 是否能识别常见 hallucination / context failure；
7. 是否满足进入 M3 的完成判据。

若满足，则 M2 收尾，不继续向 Transformer 或 Embedding 深挖。

下一模块：

> **M3 — Embedding 与语义表示基础**

---

## 12. v0.1 冻结说明

M2 Module Spec v0.1 定义首版教学边界。

普通案例、实验文本、工具选择、sampling 参数具体数值与教学顺序微调不升级本文件。

只有以下变化才考虑升级：

- M2 学习目标发生变化；
- 必须理解范围明显改变；
- 必做实验发生长期变化；
- 完成判据改变；
- Roadmap 对 M2 的职责重新定义；
- M2 与 M3 / M4 的边界发生长期变化。
