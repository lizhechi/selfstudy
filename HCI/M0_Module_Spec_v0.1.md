# M0 Module Spec — UX / HCI Foundation Map v0.1

## 0. 文档性质

本文档是 **User Interaction & HCI Self-Learning Project** 的 M0 阶段教学规格。

它属于项目规范层，负责规定：

- M0 为什么存在
- M0 必须学习什么
- M0 不应提前展开什么
- 教学顺序
- 练习类型
- 完成判据
- 阶段最终产出

本文件应在以下上位文件约束下使用：

1. `Anchor_v0.1.md`
2. `Roadmap_v0.1.md`
3. 本文件 `M0_Module_Spec_v0.1.md`

`M0_Startup_Prompt_v0.1.md`
仅负责初始化当前教学聊天的运行方式，不属于项目知识规范，也不得覆盖以上三份文件。

---

# 1. M0 定位

M0 名称：

> UX / HCI Foundation Map

建议周期：约 1 周。

建议有效学习时间：约 2～4 小时，可根据理解速度延长。

M0 的任务不是系统教授整门用户研究或 HCI，而是建立后续学习必须依赖的“领域地图”。核心目标是解决：当以后出现 UI、UX、用户研究、交互设计、人机交互、可用性、人机工程等术语时，学习者能否知道它们分别在研究什么、彼此是什么关系，以及一个现实问题主要属于哪个层级。

---

# 2. M0 完成后的能力目标

完成 M0 后，学习者应能够：

1. 用自己的话解释 HCI、UX、UI、User Research、Interaction Design、Usability、Accessibility、Human Factors。
2. 区分“界面长什么样”“用户整体体验如何”“为什么用户会这样行为”“系统如何与人发生交互”。
3. 判断一个现实问题主要属于 UI、UX、用户研究、HCI、工程实现中的哪一类。
4. 理解这些领域之间不是互斥关系，而是会发生重叠。
5. 初步理解 HCI 为什么需要计算机科学、心理学、认知科学、设计、人机工程等多个学科共同支撑。
6. 理解用户研究在产品生命周期中的位置。
7. 初步建立“以人为中心”和“以系统实现为中心”两种观察角度。
8. 避免把“好不好看”“好不好用”“用户喜不喜欢”“系统能不能实现”混成一个问题。

目标深度：核心概念达到 **Level 2～3：能够解释，并能在简单现实案例中识别。**

M0 不要求达到独立进行用户研究或 HCI 设计的能力。

---

# 3. 必学知识范围

## 3.1 HCI

**HCI = Human-Computer Interaction = 人机交互。**

M0 必须理解：

- HCI 研究的对象不是“电脑界面”本身，而是人与交互式计算系统之间的关系。
- HCI 同时关注人、系统、任务、环境与交互过程。
- HCI 既包含理论，也包含设计、工程与评估。

M0 暂不深入 Fitts's Law、Hick-Hyman Law、GOMS / KLM、Norman Action Cycle 和实验方法，这些进入后续模块。

## 3.2 UX

**UX = User Experience = 用户体验。**

必须理解 UX 不等于 UI。UX 可以包含使用前预期、学习成本、操作过程、情绪体验、效率、错误恢复、信任、满意度以及使用后的整体感受。

## 3.3 UI

**UI = User Interface = 用户界面。**

UI 是人与系统发生交互时接触到的界面与表达层之一，例如按钮、菜单、图标、页面、文字、动画和状态提示。但 UI 不代表全部交互，也不代表全部用户体验。

## 3.4 User Research

**User Research = 用户研究。**

核心不是“问用户喜欢什么”，而是通过合适方法理解：用户是谁、在什么环境下行动、有什么目标、实际怎样做、遇到什么问题、为什么采取某些行为、哪些需求能被证据支持。

具体访谈、观察、问卷等方法在 M1～M4 深入。

## 3.5 Interaction Design

**Interaction Design = 交互设计。**

关注用户如何通过行为改变系统状态，系统又如何向用户反馈这些变化。例如点击以后发生什么、怎样切换模式、怎样撤销、操作失败时发生什么、系统如何告诉用户当前状态。

## 3.6 Usability

**Usability = 可用性。**

M0 建立基础理解：一个系统是否能够让目标用户有效完成任务、以合理成本完成任务、学会使用并减少严重错误。详细评价框架进入 M8。

## 3.7 Accessibility

**Accessibility = 可访问性 / 无障碍性。**

M0 只要求理解：不同用户在视觉、听觉、运动、认知、设备、环境等方面可能存在不同条件，设计不能默认所有用户都和设计者一样。

## 3.8 Human Factors / Ergonomics

**Human Factors = 人的因素；Ergonomics = 人机工程学 / 工效学。**

关注人的身体、认知与能力限制如何影响系统设计，例如手是否够得到、字能否看清、信息是否能及时理解、操作会不会造成疲劳、控制器布局是否合理。

---

# 4. 必须建立的领域关系

M0 不能只把术语逐个背下来，应建立以下关系：

```text
用户研究
    ↓ 提供用户证据

UX / 产品设计
    ↓ 定义体验目标

Interaction Design
    ↓ 设计行为与状态变化

UI Design
    ↓ 形成具体视觉/界面表达

Software / Game Development
    ↓ 实现系统

Usability Evaluation
    ↓ 验证问题

再次进入用户研究 / 设计迭代
```

同时理解：HCI 并不只是其中某一个环节，它可以从更大的角度研究和解释整个人与计算系统的交互过程。

---

# 5. 学科来源地图

M0 应至少知道 HCI 为什么与以下领域相关：

- **Computer Science**：系统能力、算法、软件架构、输入输出、技术限制。
- **Psychology**：人怎样感知、注意、记忆、学习和决策。
- **Cognitive Science**：信息处理、认知表示与行为机制。
- **Design**：信息如何组织、交互如何表达、方案如何形成。
- **Ergonomics / Human Factors**：身体和认知能力边界。
- **Sociology / Communication**：社会情境、群体行为、沟通、协作及技术如何嵌入社会活动。

M0 不要求深入这些学科，只建立地图。

---

# 6. M0 核心辨析

必须能够完成以下辨析：

- **UI ≠ UX**：按钮颜色不好看更偏 UI；用户不知道下一步点哪里主要是 UX / Interaction / HCI 问题。
- **User Research ≠ User Opinion Collection**：用户研究不只是收集“我喜欢这个”，更重要的是理解真实行为及其原因。
- **Interaction Design ≠ Graphic Design**：交互设计关心行为、状态、反馈和流程。
- **HCI ≠ UI Design**：HCI 可以研究鼠标、键盘、触摸、VR、AR、手势、语音、眼动、AI 对话等，即使没有传统 GUI。
- **Usability ≠ Satisfaction**：喜欢不等于高效，高效也不一定等于喜欢。

---

# 7. 推荐教学顺序

1. M0.1 为什么需要这张领域地图
2. M0.2 HCI 是什么
3. M0.3 UX 与 UI
4. M0.4 User Research
5. M0.5 Interaction Design
6. M0.6 Usability / Accessibility / Human Factors
7. M0.7 学科关系
8. M0.8 产品生命周期
9. M0.9 综合辨析
10. M0.10 Final Review

---

# 8. 教学方式要求

M0 不适合长篇连续讲授。推荐循环：

> 小知识点 → 现实案例 → 极短判断题 → 解释 → 下一知识点

每学习约 2～3 个概念，至少插入一次主动判断。允许学习者使用极简回答，如 A/B/C、对/错、UI/UX/HCI、一两句话。只有需要检查推理时，才要求展开。

---

# 9. 练习类型

## 9.1 分类题

判断一个问题主要属于 UI、UX、User Research、Interaction Design、HCI 或 Engineering。

## 9.2 边界判断

例如：“一个功能需要 8 次点击，这一定说明 UX 很差吗？”要求判断是否还缺少信息。

## 9.3 对比题

比较 UI 与 UX、用户研究与可用性测试、HCI 与交互设计。

## 9.4 真实产品拆解

至少选择三个对象：一个日常 APP、一个游戏、一个桌面软件或网页。可使用微信、Steam、浏览器、Visual Studio、熟悉的游戏或 ProjectVox 设计草案。

---

# 10. M0 Final Assignment

选择一个熟悉的数字产品或交互系统，至少写出：

1. 一个 UI 问题
2. 一个 UX 问题
3. 一个 User Research 问题
4. 一个 Interaction Design 问题
5. 一个 HCI 问题
6. 一个工程实现问题

并解释：为什么这些问题虽然可能互相关联，却不能完全当成同一种问题。

建议长度约 500～1000 字。重点是分类逻辑，不是文字量。

---

# 11. 完成判据

满足以下条件即可完成 M0：

- 能解释 HCI、UX、UI、User Research、Interaction Design、Usability、Accessibility、Human Factors。
- 能正确完成大多数基本分类题。
- 能说清用户研究如何影响设计、交互设计如何影响体验、HCI 为什么比单纯 UI 更大。
- 完成 M0 Final Assignment。

---

# 12. 不要求死记的内容

M0 不要求闭卷准确复述所有英文定义、学科历史年份、学者姓名、专业标准全文或所有方法分类。

真正需要记住的是：

> 这些领域分别在解决什么类型的问题。

---

# 13. M0 明确不提前展开的内容

以下内容即使出现，也只做极简预告：正式访谈设计、样本选择、问卷统计、Persona、Journey Map、Kano、Fitts's Law、Hick-Hyman Law、GOMS / KLM、Norman Action Cycle、系统性认知心理学、完整可用性测试、VR / AR 详细设计原则、Human-AI Interaction 深入讨论。

M0 的第一任务是：**先把地图建立起来，再进入地图中的具体区域。**

---

# 14. M0 Completion Summary 要求

完成 M0 后，应生成简短阶段总结，保存为 `M0_Completion_Summary_v0.1.md`，至少记录：

- M0 已完成
- 已掌握的核心概念
- 仍容易混淆的概念
- Final Assignment 情况
- 是否满足进入 M1 条件
- M1 需要特别注意的薄弱点

该 Summary 属于学习记录，不属于项目规范文件。
