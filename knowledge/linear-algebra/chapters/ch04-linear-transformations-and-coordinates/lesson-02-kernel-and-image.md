# 第 4 章 第 2 课：核与像

## 先用生活话讲一遍（降抽象预热）

任何“输入到输出”的系统都可以问两件事：

1. 哪些输入被系统彻底吞掉，输出成零？
2. 系统最多能产生到哪些输出？

在变换语言里，这两件事就是核和像。

## 本课在本章链条中的位置

第 4 章第 2 课是“结构识别课”：把第 3 章学过的零空间/列空间提升为变换本体结构。

## 这节课先解决什么问题

1. 核与像定义是什么，为什么它们是子空间？
2. 它们如何决定变换是否单射、是否满射？
3. 它们与前面矩阵视角到底如何一一对应？

## 定义

给定线性变换 $T:V\to W$，定义
$$
\ker(T)=\{v\in V:T(v)=0\},
$$
$$
\operatorname{Im}(T)=\{T(v):v\in V\}.
$$

- $\ker(T)$ 称核（kernel）；
- $\operatorname{Im}(T)$ 称像（image，或 range）。

## 为什么二者必是子空间

先看核：

- $T(0)=0$，故 $0\in\ker(T)$；
- 若 $u,v\in\ker(T)$，则 $T(u+v)=T(u)+T(v)=0$；
- 若 $u\in\ker(T)$，则 $T(\alpha u)=\alpha T(u)=0$。

核满足子空间三条件。

像同理：若 $y_1=T(u),y_2=T(v)$，则
$$
y_1+y_2=T(u+v),\quad \alpha y_1=T(\alpha u),
$$
故像也对子空间运算封闭。

## 核心例子走完

设
$$
T:\mathbb R^3\to\mathbb R^2,
\quad
T(x,y,z)=(x+2y-z,\ 2x+4y-2z).
$$

### 1) 求核

解
$$
T(x,y,z)=0
$$
即
$$
\begin{cases}
x+2y-z=0,\\
2x+4y-2z=0.
\end{cases}
$$

第二式冗余，令 $y=s, z=t$，得 $x=-2s+t$，所以
$$
\ker(T)=\operatorname{span}\left\{
\begin{bmatrix}-2\\1\\0\end{bmatrix},
\begin{bmatrix}1\\0\\1\end{bmatrix}
\right\}.
$$

### 2) 求像

$$
T(x,y,z)=x\begin{bmatrix}1\\2\end{bmatrix}
+y\begin{bmatrix}2\\4\end{bmatrix}
+z\begin{bmatrix}-1\\-2\end{bmatrix}.
$$

后三个方向都共线，故
$$
\operatorname{Im}(T)=\operatorname{span}\left\{\begin{bmatrix}1\\2\end{bmatrix}\right\}.
$$

## 结构意义：单射与满射

- $\ker(T)=\{0\}$ 当且仅当 $T$ 单射（injective）。
- $\operatorname{Im}(T)=W$ 当且仅当 $T$ 满射（surjective）。

这两条非常实用：你不必靠图形猜，而是用核与像直接判定映射性质。

## 与矩阵视角回扣

若 $T(x)=Ax$，则
$$
\ker(T)=\mathcal N(A),\qquad \operatorname{Im}(T)=\operatorname{Col}(A).
$$

这句话把第 3 章与第 4 章彻底对接。

## 常见误解与修正

误解一：本课内容只是公式操作。  
修正：本课公式用于表达结构结论，不是替代理解。

误解二：结论只适用于当前例子。  
修正：例子是入口，本课方法应迁移到同类线性系统。

误解三：学到这里可以忽略前后章节联系。  
修正：本课结论依赖前置并服务后续，需放在主线中理解。

## 本节闭环

今天你学会了从变换角度读系统：

核看“被压扁方向”，像看“可达输出范围”。

一句话压缩：

核与像是线性变换最核心的两块结构指纹。

## 与下一课承接

下一课进入基、坐标、换基：

同一个核和像不变，但矩阵表示会因基改变而改变，我们要把这件事讲透。
