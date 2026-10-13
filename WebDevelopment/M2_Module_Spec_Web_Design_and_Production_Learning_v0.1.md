# Web Design and Production Learning Project — M2 Module Spec v0.1

> 状态：Initial Module Spec  
> 版本：v0.1  
> 上位文件：`Anchor_Web_Design_and_Production_Learning_Project_v0.1.md`  
> 路线文件：`Roadmap_Web_Design_and_Production_Learning_v0.1.md`  
> 模块：M2 — CSS 规则、引入方式与基础选择器  
> 教材对应：《HTML5+CSS3 网页设计与制作（第2版）》第3章 3.1–3.3  
> 性质：单模块教学规范  
> 作用：规定 M2 的学习目标、知识边界、教学顺序、练习、调试要求、完成判据与移交内容。  
> 本文件不承担整个课程长期路线，也不系统展开 M3 的层叠、继承和优先级。

---

## 1. 模块定位

M2 是正式进入 CSS 学习的第一个核心模块。

M1 已建立：

> HTML 文档骨架  
> → 标签 / 元素 / 属性  
> → 内容结构  
> → 标签嵌套  
> → 图片与链接  
> → 相对路径  
> → 基础 HTML 排错

M2 在此基础上建立：

> HTML 负责结构与语义  
> → CSS 负责表现  
> → CSS 规则由“选择目标 + 设置样式”组成  
> → CSS 可以通过不同方式接入页面  
> → 元素 / class / ID 可以用不同方式选中目标  
> → CSS 不生效时能够进行基础排查

M2 的目标不是让页面迅速“变漂亮”，而是建立稳定的 CSS 基础心智模型，使学习者能够：

> 看懂规则  
> → 写出规则  
> → 知道规则选中了谁  
> → 知道样式从哪里进入页面  
> → 页面无变化时能够定位基础问题

---

## 2. 目标深度

M2 总体目标：

> **L3 — 能解释、调试和迁移**

学习者应逐步达到：

- 能解释 HTML 与 CSS 的职责区别；
- 能解释 CSS 基本规则结构；
- 能区分 selector / property / value；
- 能使用内联、内部、外部三种 CSS 引入方式；
- 能正确连接外部 CSS；
- 能使用元素选择器；
- 能使用 class 选择器；
- 能使用 ID 选择器；
- 能根据页面需求判断选择器类型；
- 能把简单内联样式重构为外部 CSS；
- 能排查常见 CSS 不生效问题；
- 能在简单新任务中独立给已有 HTML 添加基础样式。

不要求：

- 完整层叠算法；
- specificity 计算；
- 继承规则；
- 复杂组合选择器；
- 属性选择器；
- 伪类；
- 伪元素；
- 盒模型；
- Flexbox / Grid；
- JavaScript。

---

## 3. M2 核心心智模型

### 3.1 HTML 与 CSS 分工

HTML：

> 描述内容是什么、结构是什么。

CSS：

> 描述这些内容如何表现。

例如：

```html
<h1>课程标题</h1>
```

HTML 表达：

> 这是一级标题。

CSS：

```css
h1 {
    color: red;
}
```

表达：

> 所有被该规则选中的 `h1` 文字显示为红色。

必须避免形成：

> HTML 标签只是控制外观  
> CSS 只是“换颜色”

这种过度简化认知。

---

### 3.2 CSS 规则 = 选择目标 + 设置表现

基本形式：

```css
h1 {
    color: red;
}
```

拆解为：

```text
h1              → selector / 选择器
color           → property / CSS 属性
red             → value / 属性值
color: red;     → declaration / 声明
{ ... }         → declaration block / 声明块
```

M2 的核心不是死记术语，而是建立：

> **先选中谁，再决定它怎样显示。**

---

### 3.3 HTML attribute 与 CSS property 必须区分

HTML：

```html
<img src="a.png" alt="A">
```

其中：

- `src`
- `alt`

是 HTML attribute。

CSS：

```css
img {
    width: 200px;
}
```

其中：

- `width`

是 CSS property。

两者中文都可能被翻译成“属性”，但技术角色不同：

> HTML attribute：给元素附加信息、配置或行为数据  
> CSS property：描述元素某一方面的表现

M2 收尾前应能基本区分。

---

### 3.4 CSS 选择器是在“描述我要选中谁”

M2 只建立三类基础选择方式：

#### 元素选择器

```css
p {
    color: gray;
}
```

表达：

> 选中所有 `p` 元素。

#### class 选择器

```css
.note {
    color: blue;
}
```

表达：

> 选中所有 `class="note"` 的元素。

#### ID 选择器

```css
#main-title {
    color: red;
}
```

表达：

> 选中 `id="main-title"` 的目标元素。

重点是理解三者的使用语义，而不是提前进入优先级比较。

---

## 4. 教材对应内容

M2 对应第3章 3.1–3.3 的 CSS 基础内容。

应优先覆盖：

- CSS 的作用；
- CSS 基本语法；
- selector；
- property；
- value；
- 内联样式；
- 内部样式；
- 外部样式；
- `<style>`；
- `<link>`；
- 元素选择器；
- class 选择器；
- ID 选择器；
- 基础样式规则；
- 外部 CSS 文件引用；
- 基础 CSS 调试。

若教材在该部分提前混入复杂层叠、组合选择器或其他后续内容，应根据 Roadmap 边界处理：

> 只做当前理解所需的最小解释，系统内容留到后续模块。

---

## 5. 教学顺序

### Step 1 — M1 → M2 接口恢复

只做极短确认：

- HTML 页面可以正常运行；
- `<link>` 可以放在 `<head>`；
- 相对路径逻辑仍然理解；
- 不重新完整教学 HTML。

目标：

> 从“页面结构”自然过渡到“页面表现”。

---

### Step 2 — CSS 是什么

正式解释：

> CSS = Cascading Style Sheets

其中：

- Cascading = 层叠；
- Style = 样式；
- Sheets = 表 / 表单式集合。

M2 此时只需要知道：

> CSS 是用规则描述网页表现的样式语言。

“层叠”机制本身不在 M2 系统展开，留到 M3。

---

### Step 3 — CSS 基本规则结构

学习：

```css
h1 {
    color: red;
}
```

重点理解：

- selector；
- property；
- value；
- declaration；
- declaration block；
- 冒号；
- 分号；
- 花括号。

至少安排：

- 规则拆解；
- 预测；
- 修改属性值；
- 多声明；
- 找语法问题。

---

### Step 4 — 内联样式

示例：

```html
<h1 style="color: red;">标题</h1>
```

学习：

- `style` 属性；
- CSS 写在 HTML 元素上的形式；
- 优点：直观、局部；
- 缺点：结构与表现混在一起，不适合作为正常项目默认方式。

目标：

> 会看、会写、知道为什么不应长期大量使用。

---

### Step 5 — 内部样式

示例：

```html
<head>
    <style>
        h1 {
            color: red;
        }
    </style>
</head>
```

学习：

- `<style>` 的位置；
- CSS 规则仍然是同一套语法；
- 当前页面内部集中管理样式。

目标：

> 理解它与内联样式的组织差异。

---

### Step 6 — 外部样式

推荐结构：

```text
project/
├─ index.html
└─ style.css
```

HTML：

```html
<link rel="stylesheet" href="style.css">
```

CSS：

```css
h1 {
    color: red;
}
```

学习：

- `link`；
- `rel`；
- `stylesheet`；
- `href`；
- 外部 CSS 文件；
- 相对路径。

目标：

> 能独立建立 HTML 与外部 CSS 的连接。

---

### Step 7 — 三种引入方式比较

要求学习者能够说明：

#### 内联

- 写在单个元素上；
- 最局部；
- 不利于维护。

#### 内部

- 写在当前 HTML 的 `<style>` 中；
- 当前页面集中管理。

#### 外部

- 写在独立 `.css` 文件；
- 更适合正常网页项目；
- HTML 与表现分离更清晰；
- 可被多个页面复用。

M2 中应默认鼓励：

> **外部 CSS 作为正常实践主方式。**

---

### Step 8 — 元素选择器

例如：

```css
p {
    color: gray;
}
```

必须通过多个 `p` 验证：

> 一个元素选择器可以一次选中多个同名元素。

练习：

- 给所有段落统一颜色；
- 给所有一级标题统一样式；
- 判断某条元素选择器会命中哪些元素。

---

### Step 9 — class 选择器

HTML：

```html
<p class="note">第一条说明</p>
<p class="note">第二条说明</p>
```

CSS：

```css
.note {
    color: blue;
}
```

解释：

- `class` = class，类别 / 类；
- `.` 是 CSS 中 class 选择器的标记。

核心理解：

> 多个元素可以属于同一 class。

不要把 class 简化为：

> “给元素起一个唯一名字”。

---

### Step 10 — ID 选择器

HTML：

```html
<h1 id="main-title">学习主页</h1>
```

CSS：

```css
#main-title {
    color: red;
}
```

解释：

- `id` = identifier，标识符；
- `#` 表示 CSS ID 选择器；
- 页面中应建立“一项 ID 对应一个唯一目标”的直觉。

M2 不系统讲：

- ID 与 class 的 specificity；
- 多重冲突规则。

---

### Step 11 — 三类选择器使用判断

训练：

#### 元素选择器

适合：

> 所有同类元素统一处理。

#### class

适合：

> 多个不同或相同元素拥有相同用途 / 样式类别。

#### ID

适合：

> 唯一、明确的单个目标。

例如：

> 所有段落 → `p`  
> 所有“警告” → `.warning`  
> 页面唯一主标题 → `#main-title`

---

### Step 12 — 内联样式重构

给出：

```html
<h1 style="color: red;">标题</h1>
<p style="color: gray;">正文</p>
```

要求迁移为：

HTML：

```html
<h1>标题</h1>
<p>正文</p>
```

CSS：

```css
h1 {
    color: red;
}

p {
    color: gray;
}
```

或根据任务引入 class。

目标：

> 理解结构与表现分离，而不是机械搬代码。

---

### Step 13 — CSS 未生效基础排错

至少覆盖：

- HTML 是否保存；
- CSS 是否保存；
- 浏览器是否刷新；
- `<link>` 是否存在；
- `href` 是否正确；
- CSS 文件名是否一致；
- 文件路径是否正确；
- 选择器是否命中；
- class 是否漏 `.`;
- ID 是否漏 `#`;
- HTML 中 class / id 名称是否与 CSS 一致；
- CSS property 是否拼写错误；
- 冒号 / 分号 / 花括号是否破坏规则。

形成最小排错链：

> 文件是否连接  
> → 选择器是否命中  
> → 规则语法是否成立  
> → 浏览器是否读取最新内容

若问题涉及规则冲突、继承或优先级：

> 标记为 M3 内容。

---

## 6. 英文缩写与命名解释规则

学习者明确要求：

> 出现 HTML / CSS / JS 等英文缩写、标签名、属性名、术语时，应解释完整英文、英文原义与中文含义。

M2 首次出现时至少解释：

- CSS = Cascading Style Sheets；
- selector = 选择器；
- property = 属性；
- value = 值；
- declaration = 声明；
- style = 样式；
- class = 类 / 类别；
- id = identifier，标识符；
- link = 链接 / 关联；
- rel = relationship，关系；
- stylesheet = style sheet，样式表；
- href = hypertext reference；
- color = 颜色；
- background = 背景；
- font = 字体；
- font-size = 字体大小。

已经解释并稳定掌握的词不需每次重复展开。

---

## 7. 与 Markdown 已有知识的衔接

学习者已完成 Markdown 基础学习。

因此：

- 文档结构；
- 标题；
- 链接；
- 图片；
- 相对路径；
- 转义 / 实体；
- 内容与表现的基本区别；

若概念相似，应优先使用 Markdown 类比快速说明。

不要重复大量通用基础。

但应明确：

> CSS 的 selector / property / value / cascade 等机制没有 Markdown 中的直接等价物，需要单独建立心智模型。

---

## 8. 记忆巩固机制

M2 不采用：

> “第一次学过 → 立即闭卷完整默写”

默认流程：

> 完整参考  
> → 修改现有规则  
> → 根据提示写  
> → 独立写  
> → 在新任务中自然复现

需要区分：

- 概念理解错误；
- 选择器判断错误；
- CSS 规则结构错误；
- 文件连接错误；
- 路径错误；
- 单纯拼写错误；
- 操作问题。

一次漏分号、拼写错单词，不自动判为概念未掌握。

---

## 9. 必做练习

### Exercise 1 — CSS 规则拆解

给出：

```css
h1 {
    color: red;
}
```

指出：

- selector；
- property；
- value；
- declaration。

---

### Exercise 2 — 三种引入方式识别

给出：

- inline；
- internal；
- external；

要求判断分别写在哪里，以及使用边界。

---

### Exercise 3 — 外部 CSS 连接

建立：

```text
project/
├─ index.html
└─ style.css
```

要求学习者独立完成连接并让 `h1` 变色。

---

### Exercise 4 — 元素选择器

HTML 中放多个同类元素，让学习者预测：

```css
p {
    color: gray;
}
```

会命中谁。

---

### Exercise 5 — class

给多个元素添加同一 class，并用：

```css
.note {
    ...
}
```

统一设置。

---

### Exercise 6 — ID

给唯一元素设置 ID，再使用：

```css
#main-title {
    ...
}
```

进行样式设置。

---

### Exercise 7 — 选择器类型判断

例如：

- 所有 `p`；
- 三条“重要提示”；
- 唯一主标题；

让学习者自行选择：

> 元素 / class / ID

---

### Exercise 8 — 内联 → 外部 CSS

给出含 `style=""` 的页面，要求拆出 `style.css`。

---

### Exercise 9 — CSS 未生效排查

故意制造：

- 路径错误；
- class 名不一致；
- `.` / `#` 漏写；
- property 拼写错误；
- CSS 文件未保存。

要求学习者自己定位。

---

## 10. M2 阶段小作业

### 任务

完成一个：

> **学习介绍页基础样式化**

HTML 可以沿用 M1 的小型页面。

至少包含：

- 一级标题；
- 二级标题；
- 多个段落；
- 图片或链接；
- 一个具有 class 的元素；
- 一个具有 ID 的元素。

CSS 必须：

- 使用独立 `style.css`；
- 正确通过 `<link>` 连接；
- 至少一个元素选择器；
- 至少一个 class 选择器；
- 至少一个 ID 选择器；
- 至少设置几项基础表现；
- 不使用复杂布局作为完成条件。

### 验收重点

- HTML / CSS 是否真正分离；
- 外部 CSS 是否连接正确；
- 选择器是否合理；
- 是否理解 `.class` 和 `#id`；
- 是否能说明每条规则选中了谁；
- CSS 无效时能否自己排查。

页面是否“漂亮”不作为核心评分标准。

---

## 11. 高频错误模式

M2 重点记录：

- CSS 文件未连接；
- `<link>` 路径错误；
- HTML / CSS 文件没保存；
- class 选择器漏 `.`;
- ID 选择器漏 `#`;
- HTML 名称与 CSS 选择器名称不一致；
- 把 `class` 当成唯一名称；
- 大量元素都用 ID；
- 把 HTML attribute 和 CSS property 混淆；
- `property = value` 与 `property: value` 混淆；
- 忘记花括号；
- 冒号 / 分号位置错误；
- 把 `src` / `href` 用错；
- 页面无变化时直接重写代码，而不是排查连接链。

---

## 12. 不应在 M2 系统展开的内容

以下内容如果被提问，可做当前理解所需的最小解释：

- cascade；
- inheritance；
- specificity；
- source order；
- 后代 / 子代 / 兄弟选择器；
- 属性选择器；
- 伪类；
- 伪元素；
- Box Model；
- display；
- position；
- float；
- Flexbox；
- Grid；
- JavaScript。

对应：

- 层叠 / 继承 / 优先级 → M3；
- 复杂选择器 → M4；
- 盒模型 → M5 / M6；
- 布局 → M10+；
- JavaScript → M14。

---

## 13. Review 规则

M2 Review 按以下优先级：

1. HTML 是否正确连接 CSS；
2. selector 是否命中目标；
3. 选择器类型是否合理；
4. CSS 规则结构是否正确；
5. property / value 是否合理；
6. 路径是否正确；
7. 语法与拼写；
8. 格式与缩进；
9. 页面是否美观。

必须明确区分：

- HTML 结构问题；
- CSS 连接问题；
- selector 问题；
- property / value 问题；
- 路径问题；
- 输入错误；
- M3 才处理的层叠问题。

---

## 14. 完成判据

M2 完成时，学习者应能：

- 用自己的话解释 CSS 的作用；
- 区分 HTML 结构职责与 CSS 表现职责；
- 读懂并写出基本 CSS rule；
- 区分 selector / property / value；
- 使用内联样式；
- 使用内部样式；
- 使用外部样式；
- 独立连接 `style.css`；
- 使用元素选择器；
- 使用 class 选择器；
- 使用 ID 选择器；
- 根据需求选择基本合适的选择器；
- 区分 HTML attribute 与 CSS property；
- 把简单内联样式重构为外部 CSS；
- CSS 不生效时能按基础检查链排查；
- 在参考逐渐减少的情况下完成一个基础 HTML + CSS 页面。

---

## 15. M2 Completion Check

### Part A — 概念

用自己的话解释：

- CSS；
- HTML 与 CSS 的分工；
- selector；
- property；
- value；
- class；
- id；
- HTML attribute 与 CSS property 的区别。

---

### Part B — 规则结构

给出：

```css
.note {
    color: red;
    font-size: 18px;
}
```

要求指出：

- selector；
- property；
- value；
- declaration；
- declaration block；
- 该规则会匹配什么 HTML。

---

### Part C — 三种 CSS 引入方式

要求判断：

- inline；
- internal；
- external；

分别写在哪里，以及正常项目中为何通常优先 external。

---

### Part D — 选择器

给一段 HTML，要求分别：

- 用元素选择器选全部同类元素；
- 用 class 选择一组元素；
- 用 ID 选择一个唯一目标。

---

### Part E — 实际操作

从一个基础 HTML 页面开始：

- 建立 `style.css`；
- 正确连接；
- 写元素 / class / ID 选择器；
- 修改基础样式；
- 浏览器验证。

---

### Part F — 调试

故意制造至少 2 种问题：

- CSS 路径错误；
- selector 名称错误；
- `.` / `#` 错误；
- property 拼写错误；
- 基础语法错误。

要求学习者自己定位并修正。

---

## 16. M2 完成后的移交

M2 完成后进入：

> **M3 — 文本样式、层叠、继承与优先级**

移交时记录：

- CSS 规则结构是否稳定；
- HTML / CSS 职责是否仍混淆；
- 三种引入方式是否理解；
- 外部 CSS 连接是否稳定；
- 元素选择器掌握状态；
- class 选择器掌握状态；
- ID 选择器掌握状态；
- 是否仍混淆 HTML attribute 与 CSS property；
- CSS 基础排错能力；
- 是否存在稳定拼写问题；
- M2 小作业结果；
- 需要在 M3 中继续复现的弱项。

---

## 17. M2 与 M3 的边界

M2 必须建立：

> CSS 能选中目标并设置表现。

但不要因为出现两条规则同时命中一个元素，就在 M2 中系统讲完：

> 为什么最终是这一条生效。

这个问题属于 M3 的：

- cascade；
- inheritance；
- specificity；
- source order。

M2 若遇到相关现象，可以标记：

> “这是 M3 要正式解决的问题。”

避免提前把 M2 的基础选择机制和 M3 的冲突决策机制混在一起。

---

## 18. v0.1 冻结说明

M2 v0.1 当前聚焦：

> CSS 基本规则  
> → 三种引入方式  
> → 元素 / class / ID 选择器  
> → 外部 CSS  
> → 基础调试

当前不把：

- 层叠算法；
- 继承；
- specificity；
- 复杂选择器；
- 盒模型；

纳入 M2 主体。

后续若老师课堂内容或考试范围明显改变 M2 实际深度，再考虑升级本 Module Spec。
