# 人工智能 Transformer 学习入口

这是一套按 SLS 组织的 Transformer 系统学习内容，面向“高中和大学低年级”受众设计。它不是零散笔记，而是一条完整学习路径：先搭整体路线，再按章节和课时逐步展开，最后回收到现代大语言模型与现实系统边界。

如果你是第一次进入这套内容，建议不要直接随机点开某一课，而是先从总纲开始，再按章节顺序推进。这样你能始终知道自己当前处在整条主线的哪个位置，也知道这一章为什么在这里出现。

## 推荐阅读顺序

1. [00-outline.md](f:\projects\prompt-test\knowledge\transformer\00-outline.md)
2. [第 1 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch01-language-sequence-and-transformer-entry)
3. [第 2 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch02-attention-mechanism-entry)
4. [第 3 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch03-self-attention-core)
5. [第 4 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch04-transformer-block-and-structure-completion)
6. [第 5 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch05-encoder-decoder-and-full-system)
7. [第 6 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch06-decoder-only-pretraining-and-generation)
8. [第 7 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch07-strengths-limits-and-system-extensions)

## 三层阅读路线

如果你想最快进入，可以按下面三种方式选路：

- `完整学习`：从 [00-outline.md](f:\projects\prompt-test\knowledge\transformer\00-outline.md) 开始，按 1 到 7 章顺序读。
- `机制导向`：从 [第 2 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch02-attention-mechanism-entry) 开始，依次读到 [第 4 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch04-transformer-block-and-structure-completion)。
- `现代 LLM 导向`：先看 [第 5 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch05-encoder-decoder-and-full-system)，再接 [第 6 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch06-decoder-only-pretraining-and-generation) 和 [第 7 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch07-strengths-limits-and-system-extensions)。

## 课程主线

整套内容围绕一条连续主线展开：

语言理解为什么难；
为什么注意力会变成必要结构；
self-attention 怎样成为核心发动机；
为什么完整 Transformer block 还要补位置、多头、前馈和稳定性结构；
原始 Encoder-Decoder Transformer 怎样组成完整系统；
为什么现代大语言模型走向 Decoder-only 与下一词预测；
为什么今天的 AI 系统又会继续长出 RAG、工具调用、多模态和长上下文优化。

如果把整套内容压成一句话：

Transformer 的本质，是把“上下文里谁该和谁发生关系”变成一个可训练、可并行、可堆叠的系统；现代 LLM 则是在这套系统上，把大量语言和任务模式吸收到统一的条件生成接口里。

## 章节导航

### 第 1 章：语言为什么难，Transformer 为什么值得出现

目录：
[ch01-language-sequence-and-transformer-entry](f:\projects\prompt-test\knowledge\transformer\chapters\ch01-language-sequence-and-transformer-entry)

建议入口：
[lesson-00-chapter-guide.md](f:\projects\prompt-test\knowledge\transformer\chapters\ch01-language-sequence-and-transformer-entry\lesson-00-chapter-guide.md)

这一章解决“问题从哪里来”。重点是顺序、长距离依赖和任务相关关注。

适合直接跳读：
如果你还不清楚“语言处理为什么难到需要 Transformer”，先从这一章进最稳。

关键词：
顺序、长距离依赖、信息瓶颈入口、任务相关关注

### 第 2 章：注意力机制的原型与 query/key/value

目录：
[ch02-attention-mechanism-entry](f:\projects\prompt-test\knowledge\transformer\chapters\ch02-attention-mechanism-entry)

建议入口：
[lesson-00-chapter-guide.md](f:\projects\prompt-test\knowledge\transformer\chapters\ch02-attention-mechanism-entry\lesson-00-chapter-guide.md)

这一章解决“注意力为什么必要，以及它怎样从直觉走到机制骨架”。

适合直接跳读：
如果你已经知道 Transformer 很重要，但说不清 attention 为什么会出现，从这里开始最合适。

关键词：
按需读取、query、key、value、权重、上下文化表示

### 第 3 章：self-attention 的标准形式

目录：
[ch03-self-attention-core](f:\projects\prompt-test\knowledge\transformer\chapters\ch03-self-attention-core)

建议入口：
[lesson-00-chapter-guide.md](f:\projects\prompt-test\knowledge\transformer\chapters\ch03-self-attention-core\lesson-00-chapter-guide.md)

这一章解决“Transformer 的核心发动机到底怎么工作”，包括点积、缩放和矩阵化并行。

适合直接跳读：
如果你最想先搞明白 self-attention 公式到底在表达什么，从这一章进入。

关键词：
self-attention、点积、缩放、矩阵并行、相关性图

### 第 4 章：完整 Transformer block 为什么这样长成

目录：
[ch04-transformer-block-and-structure-completion](f:\projects\prompt-test\knowledge\transformer\chapters\ch04-transformer-block-and-structure-completion)

建议入口：
[lesson-00-chapter-guide.md](f:\projects\prompt-test\knowledge\transformer\chapters\ch04-transformer-block-and-structure-completion\lesson-00-chapter-guide.md)

这一章解决“为什么只有 self-attention 还不够”，重点是位置编码、多头、前馈、残差和归一化。

适合直接跳读：
如果你已经会背 attention 公式，但不知道完整 Transformer block 为什么长成这样，从这一章进入。

关键词：
位置编码、多头注意力、前馈网络、残差、层归一化

### 第 5 章：Encoder、Decoder、mask 与 cross-attention

目录：
[ch05-encoder-decoder-and-full-system](f:\projects\prompt-test\knowledge\transformer\chapters\ch05-encoder-decoder-and-full-system)

建议入口：
[lesson-00-chapter-guide.md](f:\projects\prompt-test\knowledge\transformer\chapters\ch05-encoder-decoder-and-full-system\lesson-00-chapter-guide.md)

这一章解决“原始 Transformer 作为完整系统怎样工作”。

适合直接跳读：
如果你最关心 Encoder、Decoder、mask 和 cross-attention 的分工，从这一章进入。

关键词：
Encoder、Decoder、mask、cross-attention、翻译系统

### 第 6 章：Decoder-only、预训练、prompt 与生成

目录：
[ch06-decoder-only-pretraining-and-generation](f:\projects\prompt-test\knowledge\transformer\chapters\ch06-decoder-only-pretraining-and-generation)

建议入口：
[lesson-00-chapter-guide.md](f:\projects\prompt-test\knowledge\transformer\chapters\ch06-decoder-only-pretraining-and-generation\lesson-00-chapter-guide.md)

这一章解决“为什么现代大语言模型会走向今天这种形态”。

适合直接跳读：
如果你更关心 GPT、预训练、prompt 和生成，而不是原始论文细节，从这一章进入。

关键词：
Decoder-only、下一词预测、条件续写、prompt、generation

### 第 7 章：为什么强、为什么会错、为什么会扩展成更大系统

目录：
[ch07-strengths-limits-and-system-extensions](f:\projects\prompt-test\knowledge\transformer\chapters\ch07-strengths-limits-and-system-extensions)

建议入口：
[lesson-00-chapter-guide.md](f:\projects\prompt-test\knowledge\transformer\chapters\ch07-strengths-limits-and-system-extensions\lesson-00-chapter-guide.md)

这一章解决“能力、边界与系统扩展为什么来自同一条主线”。

适合直接跳读：
如果你最关心“为什么会幻觉”“为什么会有 RAG 和工具调用”，从这一章进入。

关键词：
幻觉、长上下文、RAG、工具调用、多模态、系统扩展

## 当前文档结构

当前目录结构如下：

- `00-outline.md`：整套课程的大纲与章节递进关系
- `README.md`：当前这个入口页
- `chapters/`：按章节组织的正文

每一章都采用同样的组织方式：

- `lesson-00-chapter-guide.md`：章节导学
- `lesson-01...lesson-03`：本章逐步展开的课时正文
- `lesson-04...`：章节回收与下一章承接

## 如何使用这套内容

如果你想从头系统学，按推荐顺序从 `00-outline.md` 一路读下去最合适。

如果你已经有基础，想查某一部分：

- 想看“为什么需要注意力”，从第 2 章开始。
- 想看“self-attention 公式到底在表达什么”，从第 3 章开始。
- 想看“完整 Transformer block 结构”，从第 4 章开始。
- 想看“原始 Transformer 系统与现代 LLM 的差别”，从第 5、6 章开始。
- 想看“为什么会幻觉、为什么会有 RAG 和工具调用”，从第 7 章开始。

如果你想先看一条最短主线：

1. [第 1 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch01-language-sequence-and-transformer-entry)
2. [第 2 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch02-attention-mechanism-entry)
3. [第 3 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch03-self-attention-core)
4. [第 6 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch06-decoder-only-pretraining-and-generation)
5. [第 7 章](f:\projects\prompt-test\knowledge\transformer\chapters\ch07-strengths-limits-and-system-extensions)

## 一句话收束

如果你只想先记住一句课程总纲，那就记这句：

理解 Transformer，不只是理解一个模型，而是在理解今天 AI 系统为什么能工作、为什么会出错，以及为什么还在继续向外长。
