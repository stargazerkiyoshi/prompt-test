# 第 7 章 第 0 课：本章导学与全局收束目标

## 先回答“为什么最后一章是分解视角”

你前面学过了：

- 方程怎么解；
- 空间怎么解释；
- 变换怎么表示；
- 近似怎么最优。

最后自然要问：

能不能把一个复杂线性系统拆成标准模块，让解释、计算、近似一次统一？

第 7 章的答案是：

- 对称情形：谱定理；
- 一般情形：SVD（奇异值分解）。

## 本章主问题

1. 对称矩阵为什么可以被正交对角化？
2. 任意矩阵为什么都可写成
$$
A=U\Sigma V^T?
$$
3. 奇异值与主方向如何决定信息保留？
4. 低秩近似为什么是最优压缩？

## 与前面章节承接

第 5 章给了谱方向，第 6 章给了最优近似。第 7 章把两条线合并：

用分解结构直接读系统主方向、稳定性和可压缩性。

## 课时安排

- `lesson-00-chapter-guide.md`
- `lesson-01-spectral-theorem-for-symmetric-matrices.md`
- `lesson-02-svd-structure-and-geometry.md`
- `lesson-03-low-rank-approximation-and-pca-intuition.md`
- `lesson-04-final-wrap-from-equations-to-decompositions.md`
