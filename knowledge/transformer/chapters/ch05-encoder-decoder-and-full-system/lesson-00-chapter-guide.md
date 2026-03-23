# 第 5 章 第 0 课：本章导学与主线说明

第 4 章结束时，一个标准 Transformer block 已经成立了。我们已经知道，位置编码、多头 self-attention、前馈网络、残差和归一化怎样围绕 self-attention 这个核心发动机，组成一个可堆叠、可训练的结构单元。现在自然要继续往前走：

如果 block 已经有了，那么很多这样的 block 组合起来，完整 Transformer 系统到底长什么样？

这就是第 5 章要解决的问题。

这一章的任务，不再是讨论 block 内部每个零件做什么，而是把视角提升到“信息流架构”。也就是说，我们要回答：

输入句子怎样先被加工成可读取的上下文表示；输出句子怎样一边生成、一边参考已经生成的部分和输入信息；为什么 Decoder 里必须遮住未来；为什么 cross-attention 不是又一个 self-attention，而是在连接系统的两侧。

这一章会推进四件事。

第一，我们会解释 Encoder 的职责。它不是“把句子简单编码一下”，而是在逐层把输入句子加工成一组富含上下文的表示，供后续读取。

第二，我们会解释 Decoder 的职责。它不是简单重复 Encoder，而是在生成目标序列时，一边利用已经生成的内容，一边对输入侧表示做有条件读取。

第三，我们会说明 mask 为什么必须出现。因为训练和生成都要求模型不能偷看未来，否则“逐步生成”这个任务本身就会失真。

第四，我们会解释 cross-attention 的对象关系，说明它为什么是原始 Encoder-Decoder Transformer 的关键桥梁。

读完这一章之后，你至少应当具备三种稳定能力。

1. 能说明 Encoder 和 Decoder 不只是左右对称的两个壳子，而是承担不同信息流职责。
2. 能解释 mask 的作用不是形式规定，而是保证自回归生成任务成立。
3. 能用自己的话讲清楚 cross-attention 是怎样把目标端当前需求连接到输入端表示上的。

这一章仍然会持续回收课程里的核心句子：

“这只动物没有过马路，因为它太累了。”

但这次它会被放进翻译场景。我们不再只是问“句内哪个词该看哪个词”，而会进一步问：如果要把这句话翻成另一种语言，输入句子如何先在 Encoder 里被加工成一组可读取表示，Decoder 在生成目标句某个词时，又是怎样一边看自己已经写出的部分，一边去输入侧抓最相关的信息。

## 本章课时顺序

请按下面顺序学习，不建议跳读：

- `lesson-00-chapter-guide.md`
- `lesson-01-what-the-encoder-is-really-building.md`
- `lesson-02-what-the-decoder-is-doing-while-generating.md`
- `lesson-03-mask-and-cross-attention-as-system-bridges.md`
- `lesson-04-chapter-wrap-and-full-transformer-system-lock-in.md`

这个顺序对应的推进链很明确：

先看输入侧如何建立可读取表示，再看输出侧如何逐步生成，然后解释遮挡机制与跨侧读取，最后把完整 Encoder-Decoder Transformer 的系统图景锁住。

## 学习提醒

这一章如果某一步让你感觉“只是系统图变复杂了”，先回到两个问题：

- 当前这部分是在加工输入端信息，还是在组织输出端生成？
- 当前这个 attention 是在同一侧内部重读，还是在另一侧上做条件读取？

只要这两个问题抓稳，Encoder、Decoder、self-attention、cross-attention 就不容易混。
