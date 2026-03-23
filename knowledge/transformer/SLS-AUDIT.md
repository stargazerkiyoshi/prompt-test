# Transformer 课程打磨审计与执行计划

## 1. 文档定位

这份文档不是课程正文，而是当前 `knowledge/transformer/` 内容的打磨审计与执行计划。目的不是重写整套课程，而是在现有成稿已经完整可读的前提下，找出最值得继续精修的部位，并给出明确的返工顺序。

## 2. 审计范围

- 审计对象：
  - `knowledge/transformer/00-outline.md`
  - `knowledge/transformer/README.md`
  - `knowledge/transformer/chapters/` 下全部章节文件
- 不含范围：
  - 仓库其他知识主题
  - `sls/` 规范文件本身

## 3. 当前总体判断

### 3.1 总体状态

- 当前这套 `Transformer` 课程已经具备完整的 SLS 学习路径形态：
  - 有总纲
  - 有入口页
  - 有 7 章正文
  - 每章包含导学、展开课时、章节回收
- 目前主要问题已经不是“缺章节”或“缺主线”，而是进入第二阶段的成稿精修：
  - 术语边界还可以更稳
  - 章节互链还可以更强
  - 个别章节还可以补更落地的辅助例子
  - 入口导航仍可增强

### 3.2 SLS 层面判断

- `Core`：`✅`
- `Architecture`：`✅`
- `Teaching Flow`：`✅`
- `Narrative`：`✅`
- `调用层/入口组织`：`△`

说明：

- 主骨架已经稳定。
- 当前最值得继续做的，不是重建课程，而是让课程“更像一套成熟知识产品”。

## 4. 当前主要待打磨项

### 4.1 术语统一

当前课程中有几组表达都能成立，但边界还不够稳，跨章时会让阅读节奏略微发散。

主要包括：

- `可读取记忆` / `表示场` / `可读取表示空间`
- `条件 continuation` / `条件继续生成` / `条件续写`
- `下一个 token` / `下一 token` / `下一词`

问题不在于这些说法本身错误，而在于：

- 不同章节里切换频率较高
- 少数地方英文术语直接裸用，和整体中文叙述风格不完全齐

处理目标：

- 保留必要英文，但以中文主称呼为主
- 统一主术语，再保留少量括号式英文别名

### 4.2 入口导航增强

`README.md` 当前已经可用，但还可以进一步增强三种入口能力：

- 新读者如何顺序进入
- 已有基础者如何按问题跳读
- 每章分别解决什么问题、适合什么阅读目的

处理目标：

- 增加更清晰的阅读路线
- 给每章补“适合直接跳读”定位
- 增加关键词导引

### 4.3 章节互链

当前章节内部承接是有的，但显式跨章链接还偏少。尤其是以下几组关系已经很强，但还可以更明确：

- 第 2 章到第 3 章
- 第 5 章到第 6 章
- 第 6 章到第 7 章

处理目标：

- 在少量关键章节的收束课中补“回看上一章 / 前瞻下一章”的明确落点
- 不追求全量加链接，先做主链打通

### 4.4 辅助例子不足

当前课程已经有贯穿主例子，主线是成立的。但如果继续打磨，最值得补的不是再加很多例子，而是补 1 到 2 个“高区分度”的辅助例子，分别覆盖：

- 翻译对齐
- 幻觉/检索/外部知识边界

处理目标：

- 强化第 5 章和第 7 章的现实落地感
- 不稀释主例子，不引入过多并行主线

## 5. 优先级排序

### 第一优先级：立刻值得做

- 术语统一
- README 导航增强

理由：

- 修改范围小，收益高
- 能显著提升整套课程的整体感和可读性
- 不会破坏现有正文结构

### 第二优先级：随后应做

- 关键章节互链增强
- 第 5 章与第 7 章补辅助例子

理由：

- 会进一步提升课程作为“成体系知识产品”的完成度
- 但比第一优先级更容易引起局部篇幅增长，需要更谨慎

### 第三优先级：可选精修

- 个别长段再压缩
- 局部句式风格进一步压齐
- 为关键公式段补轻量提示框式总结

理由：

- 属于体验优化，而不是结构性收益

## 6. 第一轮执行范围

本轮先做第一优先级内容：

1. 新增本审计文档
2. 增强 `README.md`
3. 统一第 5 至第 7 章中的关键术语口径

本轮刻意不做：

- 大规模重写正文
- 成批新增辅助例子
- 全量跨文件链接

## 7. 第一轮目标文件

- `knowledge/transformer/README.md`
- `knowledge/transformer/chapters/ch05-encoder-decoder-and-full-system/lesson-01-what-the-encoder-is-really-building.md`
- `knowledge/transformer/chapters/ch05-encoder-decoder-and-full-system/lesson-02-what-the-decoder-is-doing-while-generating.md`
- `knowledge/transformer/chapters/ch06-decoder-only-pretraining-and-generation/lesson-03-prompting-and-generation-as-conditional-continuation.md`
- `knowledge/transformer/chapters/ch06-decoder-only-pretraining-and-generation/lesson-04-chapter-wrap-and-modern-llm-entry-lock-in.md`
- `knowledge/transformer/chapters/ch07-strengths-limits-and-system-extensions/lesson-01-where-the-power-really-comes-from.md`
- `knowledge/transformer/chapters/ch07-strengths-limits-and-system-extensions/lesson-02-why-it-can-fail-hallucinate-and-get-expensive.md`
- `knowledge/transformer/chapters/ch07-strengths-limits-and-system-extensions/lesson-03-why-rag-tools-and-multimodality-keep-appearing.md`
- `knowledge/transformer/chapters/ch07-strengths-limits-and-system-extensions/lesson-04-final-wrap-from-transformer-to-modern-ai-systems.md`

## 8. 第一轮完成标准

- 主术语边界更稳，不再频繁切换称呼
- `README.md` 从“可读入口”提升到“更强导航入口”
- 第 5 到第 7 章的语言风格更统一
- 不引入新的结构性冗余

## 9. 当前执行结论

- 这套课程目前已经过了“能不能用”的阶段。
- 当前最值得做的，是把它从“完整成稿”推向“更稳定、可导航、术语更一致的课程成品”。
- 第一轮打磨应以“术语统一 + 导航增强”为主，而不是盲目重写正文。
