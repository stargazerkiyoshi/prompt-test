# 第 3 章 第 2 课：四个基本子空间

## 先用生活话讲一遍（降抽象预热）

同一个矩阵 $A$，其实同时在讲四件不同的事：

- 它能把输入“送到哪里”（输出可达范围）；
- 它有哪些输入会被“压成零”（信息丢失方向）；
- 它的约束本身在什么空间里组织；
- 哪些向量与所有约束都正交。

这四件事不是并列知识点，而是一张完整结构图。今天就是把这张图搭出来。

## 本课在本章链条中的位置

第 3 章第 2 课解决“对象扩展”：在第 1 课子空间与基的基础上，明确线性系统里最核心的四个子空间。

没有这一步，后面的秩-零度定理会像公式；有了这一步，定理会变成你已经看过的关系压缩。

## 这节课先解决什么问题

今天聚焦三个问题：

1. 四个基本子空间分别是什么，来自矩阵哪一侧？
2. 它们如何解释第 2 章的解现象（可达、无解、自由变量）？
3. 它们之间有哪些关键关系（尤其是正交关系）？

## 从一个具体矩阵进入

取
$$
A=
\begin{bmatrix}
1&2&-1\\
2&4&-2
\end{bmatrix}
\in\mathbb R^{2\times 3}.
$$

这是我们前面反复见过的结构：第二行是第一行两倍，所以约束有冗余。

### 1) 列空间 $\operatorname{Col}(A)$

列空间定义为 $A$ 的列向量张成：
$$
\operatorname{Col}(A)=\operatorname{span}\left\{
\begin{bmatrix}1\\2\end{bmatrix},
\begin{bmatrix}2\\4\end{bmatrix},
\begin{bmatrix}-1\\-2\end{bmatrix}
\right\}
=\operatorname{span}\left\{\begin{bmatrix}1\\2\end{bmatrix}\right\}.
$$

它在 $\mathbb R^2$ 中，是一条直线。

语义：$Ax=b$ 中能被命中的 $b$ 全都在这条线里。也就是“输出可达集合”。

### 2) 零空间 $\mathcal N(A)$

零空间定义为
$$
\mathcal N(A)=\{x\in\mathbb R^3:Ax=0\}.
$$

解
$$
x_1+2x_2-x_3=0
$$
得
$$
x_1=-2s+t,\quad x_2=s,\quad x_3=t,
$$
所以
$$
\mathcal N(A)=\operatorname{span}\left\{
\begin{bmatrix}-2\\1\\0\end{bmatrix},
\begin{bmatrix}1\\0\\1\end{bmatrix}
\right\}.
$$

它在 $\mathbb R^3$ 中是二维平面。

语义：这些输入方向会被 $A$ 完全“压扁成零输出”，对应系统的信息丢失方向。

### 3) 行空间 $\operatorname{Row}(A)$

行空间是 $A$ 的行向量张成，属于 $\mathbb R^3$：
$$
\operatorname{Row}(A)=\operatorname{span}\{(1,2,-1),(2,4,-2)\}
=\operatorname{span}\{(1,2,-1)\}.
$$

语义：它是“约束方程的方向集合”。第 2 章做行变换时，本质上就是在改写这个约束空间的基表示。

### 4) 左零空间 $\mathcal N(A^T)$

定义为
$$
\mathcal N(A^T)=\{y\in\mathbb R^2:A^Ty=0\}.
$$

这里
$$
A^T=
\begin{bmatrix}
1&2\\
2&4\\
-1&-2
\end{bmatrix},
$$
解得
$$
y_1+2y_2=0\Rightarrow y=(-2,1)^T\cdot t.
$$

所以
$$
\mathcal N(A^T)=\operatorname{span}\left\{\begin{bmatrix}-2\\1\end{bmatrix}\right\}.
$$

语义：它是与列空间正交的方向集，反映“输出空间里被列空间漏掉的方向”。

## 关键关系：两组正交补

四个基本子空间最关键的结构关系是：

$$
\operatorname{Row}(A)=\mathcal N(A)^\perp\subseteq\mathbb R^n,
$$
$$
\operatorname{Col}(A)=\mathcal N(A^T)^\perp\subseteq\mathbb R^m.
$$

也就是说：

- 行空间与零空间互为正交补（在输入空间里）；
- 列空间与左零空间互为正交补（在输出空间里）。

这两组关系会把第 2 章“有无解”的判定解释得更深：

- 当 $b\notin\operatorname{Col}(A)$ 时无解；
- 等价地，$b$ 在左零空间方向上存在不可兼容分量。

## 把第 2 章结论统一回四空间视角

第 2 章里你见到的现象，现在可以统一翻译：

1. “无解”

是因为目标 $b$ 不在列空间里。

2. “无穷多解”

是因为存在非零零空间，解可写成
$$
x=x_p+z,\quad z\in\mathcal N(A).
$$

3. “自由变量个数”

等于零空间维数，也就是输入空间中“被压扁方向”的数量。

这就是为什么第 3 章看起来更抽象，但其实是在解释你已经会算的东西。

## 常见误解与修正

误解一：四个子空间是四套独立内容。

修正：它们是同一矩阵的一体四面，彼此有维数与正交关系。

误解二：列空间和行空间一定在同一个空间比较。

修正：一般不在同一环境。$\operatorname{Col}(A)\subseteq\mathbb R^m$，$\operatorname{Row}(A)\subseteq\mathbb R^n$。

误解三：左零空间不重要。

修正：它直接刻画“为什么某些 $b$ 不可达”，是无解机制的几何解释核心。

## 本节闭环

今天我们把第 2 章的计算现象统一装进“四个基本子空间”框架：

- 列空间看可达输出；
- 零空间看输入丢失；
- 行空间看约束骨架；
- 左零空间看不可达方向。

一句话压缩本课：

一个矩阵的行为，必须同时从四个子空间看，单看一个面都会失真。

## 与下一课的承接

下一课进入秩-零度定理，把今天的空间关系压成最关键的维数关系：
$$
\operatorname{rank}(A)+\operatorname{nullity}(A)=n.
$$

你会看到这不是新公式，而是今天这张结构图的计数版本。

## 与下一课承接

下一课将在本课结果基础上推进更高一层问题：保持当前结构不变，提升表达密度与可迁移性。

## 一个快速示例

本课可用一个低维线性系统做快速验证：先按本课方法处理，再对照结论检查是否满足结构预期。
