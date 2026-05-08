# 第 5 章 第 0 课：本章导学与主线说明

第 4 章结束时，我们刚刚锁定的是一个标准 Transformer block。也就是说，我们已经讲清楚了“基本积木”怎样成立，但还没有正式讲“完整 Transformer 系统”怎样成立。我们已经知道，位置编码、多头 self-attention、前馈网络、残差和归一化怎样围绕 self-attention 这个核心发动机，组成一个可堆叠、可训练的结构单元。现在自然要继续往前走：

如果 block 已经有了，那么很多这样的 block 组合起来，完整 Transformer 系统到底长什么样？

这就是第 5 章要解决的问题。

## 先把你现在最容易混的三层东西连起来

如果你前四章读到这里，脑中其实已经有了 Transformer 的“零件层”，但还没完全看见它的“整机层”。所以在正式讲 Encoder 和 Decoder 之前，要先把这三层对象直接连起来：

第一层，`self-attention` 是核心机制。它回答的是“一个位置怎样按需读取别的位置”。

第二层，`Transformer block` 是标准积木。它把位置编码、多头注意力、前馈网络、残差和归一化组织成一个可堆叠的层。

第三层，`original Encoder-Decoder Transformer` 是完整机器。它不是在 block 外面临时加的外围配件，而是用很多个 block 分成两大侧来搭成的系统：

- Encoder 这一侧负责先处理输入句子；
- Decoder 这一侧负责逐步生成输出句子。

所以第 5 章并不是突然换题，而是在回答：

前面讲清楚的那些 block，真正被怎样搭成一台能训练、能翻译、能生成的 Transformer？

如果把关系压成一句最短的话，就是：

attention 是机制，block 是积木，Encoder/Decoder 是由这些积木搭出来的原始 Transformer 系统内部结构。

## 再先给一眼“原始 Transformer 到底长什么样”

可以先把原始论文里的 Transformer 粗略想成下面这个形状：

输入句子 token
-> 词向量 + 位置信息
-> 多层 Encoder block
-> 得到一排输入侧上下文化表示

目标句前缀 token
-> 词向量 + 位置信息
-> 多层 Decoder block
-> 在每一步先看目标侧前缀，再看 Encoder 输出
-> 预测当前应该生成的下一个目标词

这里最关键的是：

- Encoder 和 Decoder 都不是外围插件，而是原始 Transformer 系统内部的两大主体结构。
- 第 4 章讲的 block，不是讲完就丢掉了，而是正好在这里开始被成批堆起来。
- Decoder 也不是“另一个不相干的新模型”，而是系统里负责生成那一侧的 block 堆叠。

所以你看到 Encoder/Decoder 时，正确感觉不该是“怎么突然多出两个陌生概念”，而应该是：

原来前面讲的单个 block，现在终于开始被搭成一整台机器了。

## 再把“它是怎么训练的”先讲成一条最短主线

如果只看第 4 章，你确实容易只学到“内部原理”，却不知道整机怎么训。原始 Transformer 的训练主线其实很朴素：

1. 给模型一对训练样本：源句和目标句，比如翻译任务里的输入句和正确译文。
2. 源句先走 Encoder，变成一排可读取的上下文化表示。
3. 目标句不会整句直接交给模型当答案，而是右移后作为 Decoder 输入前缀。
4. Decoder 在每个位置都只能看见前面的正确目标词，去预测“下一个目标词应该是什么”。
5. 预测结果和真实目标词逐位置比较，得到 loss。
6. loss 再反向传播 through Decoder、cross-attention、Encoder 和所有 block，把整套系统一起训练起来。

所以训练时，不是“先把 attention 单独训好，再把 Encoder/Decoder 后装上去”，而是：

整台 Encoder-Decoder Transformer 作为一个完整系统一起训练。

你后面看到的 mask、cross-attention、逐步生成，都是为了让这条训练链和推理链成立。

这一章的任务，不再是讨论 block 内部每个零件做什么，而是把视角提升到“信息流架构”。也就是说，我们要回答：

输入句子怎样先被加工成可读取的上下文表示；输出句子怎样一边生成、一边参考已经生成的部分和输入信息；为什么 Decoder 里必须遮住未来；为什么 cross-attention 不是又一个 self-attention，而是在连接系统的两侧。

这一章会推进五件事。

第一，我们会先把原始 Transformer 的整机外形和训练主线讲清楚。也就是说，先回答“它到底长什么样，又是怎样被整机训练起来的”。

第二，我们会解释 Encoder 的职责。它不是“把句子简单编码一下”，而是在逐层把输入句子加工成一组富含上下文的表示，供后续读取。

第三，我们会解释 Decoder 的职责。它不是简单重复 Encoder，而是在生成目标序列时，一边利用已经生成的内容，一边对输入侧表示做有条件读取。

第四，我们会说明 mask 为什么必须出现。因为训练和生成都要求模型不能偷看未来，否则“逐步生成”这个任务本身就会失真。

第五，我们会解释 cross-attention 的对象关系，说明它为什么是原始 Encoder-Decoder Transformer 的关键桥梁。

读完这一章之后，你至少应当具备四种稳定能力。

1. 能先用整机视角说清原始 Transformer 的大致外形，以及它怎样通过“源句 + 目标前缀 -> 预测下一个目标词”的方式训练。
2. 能说明 Encoder 和 Decoder 不只是左右对称的两个壳子，而是承担不同信息流职责。
3. 能解释 mask 的作用不是形式规定，而是保证自回归生成任务成立。
4. 能用自己的话讲清楚 cross-attention 是怎样把目标端当前需求连接到输入端表示上的。

这一章仍然会持续回收课程里的核心句子：

“这只动物没有过马路，因为它太累了。”

但这次它会被放进翻译场景。我们不再只是问“句内哪个词该看哪个词”，而会进一步问：如果要把这句话翻成另一种语言，输入句子如何先在 Encoder 里被加工成一组可读取表示，Decoder 在生成目标句某个词时，又是怎样一边看自己已经写出的部分，一边去输入侧抓最相关的信息。

## 本章课时顺序

请按下面顺序学习，不建议跳读：

- `lesson-00-chapter-guide.md`
- `lesson-01-how-the-original-transformer-fits-together.md`
- `lesson-02-what-the-encoder-is-really-building.md`
- `lesson-03-what-the-decoder-is-doing-while-generating.md`
- `lesson-04-mask-and-cross-attention-as-system-bridges.md`
- `lesson-05-chapter-wrap-and-full-transformer-system-lock-in.md`

这个顺序对应的推进链很明确：

先看整机外形和训练主线，再看输入侧如何建立可读取表示，再看输出侧如何逐步生成，然后解释遮挡机制与跨侧读取，最后把完整 Encoder-Decoder Transformer 的系统图景锁住。

## 学习提醒

这一章如果某一步让你感觉“只是系统图变复杂了”，先回到两个问题：

- 当前这部分是在加工输入端信息，还是在组织输出端生成？
- 当前这个 attention 是在同一侧内部重读，还是在另一侧上做条件读取？

如果还觉得断，可以再加一个总问题反复问自己：

- 我现在看到的是单个 block 的内部机制，还是整个 Encoder-Decoder Transformer 的系统分工？

只要这两个问题抓稳，Encoder、Decoder、self-attention、cross-attention 就不容易混。
