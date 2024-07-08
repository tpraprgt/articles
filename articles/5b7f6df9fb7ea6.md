---
title: "機械学習のための微分公式"
emoji: "📈"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["math"]
published: true
---

機械学習の理論で使われる微分公式を紹介します．不備等ありましたら指摘していただきますと幸いです．

## 前提
- ベクトルは常に縦ベクトル表記とします．
- スカラ値 $y$ のベクトル $\bm{x}$ による偏微分は，縦ベクトルで以下のように定義します．

$$
\left( \frac{\partial y}{\partial \bm{x}} \right)_i = \frac{\partial y}{\partial x_i}
$$

- スカラ値 $y$ の行列 $X$ による偏微分は，以下のように定義します．

$$
\left( \frac{\partial y}{\partial X} \right)_{ij} = \frac{\partial y}{\partial x_{ij}}
$$

- ベクトル $\bm{y}$ のベクトル $\bm{x}$ による偏微分は，以下のように定義します．

$$
\left( \frac{\partial \bm{y}}{\partial \bm{x}} \right)_{ij} = \frac{\partial y_i}{\partial x_j}
$$

## ベクトルと行列の絡んだ微分公式
- 内積

$$
\frac{\partial}{\partial \bm{x}} ( \bm{a}^T \bm{x} ) = \frac{\partial}{\partial \bm{x}} ( \bm{x}^T \bm{a} )= \bm{a}
$$

:::details 導出

$$
\frac{\partial}{\partial x_i} ( \bm{a}^T \bm{x} ) = \frac{\partial}{\partial x_i} ( \sum_{i} a_i x_i ) = a_i
$$

:::

- 1次形式

$$
\frac{\partial}{\partial \bm{x}} ( A \bm{x} )= A
$$

:::details 導出

$A$ の行ベクトルを $\bm{a}_i^T$ とすると，

$$
A = [ \bm{a}_1, \bm{a}_2, ..., \bm{a}_n ]^T
$$

より，

$$
\frac{\partial}{\partial x_j} ( A \bm{x} )_i = \frac{\partial}{\partial x_j} ( \bm{a}_i^T \bm{x} ) = A_{ij}
$$

:::

- 2次形式

$$
\frac{\partial}{\partial \bm{x}} ( \bm{x}^T A \bm{x} ) = (A + A^T) \bm{x}
$$

:::details 導出

$$
\frac{\partial}{\partial x_i} ( \bm{x}^T A \bm{x} )
= \frac{\partial}{\partial x_i} ( \sum_{i,j} A_{ij} x_i x_j )
= \frac{\partial}{\partial x_i} ( \sum_{i \neq j} A_{ij} x_i x_j  + \sum_{i} A_{ii} x_i^2) \\
= \sum_{j \neq i} A_{ij} x_j + \sum_{j \neq i} A_{ji} x_j + 2 A_{ii} x_i
= \sum_{j} A_{ij} x_j + \sum_{j} A_{ji} x_j
$$

:::

$$
\frac{\partial}{\partial A} ( \bm{x}^T A \bm{x} ) = \bm{x} \bm{x}^T
$$

:::details 導出

$$
\frac{\partial}{\partial A_{ij}} ( \bm{x}^T A \bm{x} )
= \frac{\partial}{\partial A_{ij}} ( \sum_{i,j} A_{ij} x_i x_j )
= x_i x_j
$$

また，$(\bm{x} \bm{x})_{ij} = x_i x_j$ であることより従う．

:::

## 連鎖律

- ベクトル $\bm{z}$ のベクトル $\bm{x}$ による偏微分

$$
\frac{\partial \bm{z}}{\partial \bm{x}} = \frac{\partial \bm{z}}{\partial \bm{y}} \frac{\partial \bm{y}}{\partial \bm{x}}
$$

- スカラ $z$ のベクトル $\bm{x}$ による偏微分

$$
\frac{\partial z}{\partial \bm{x}} = \left( \frac{\partial \bm{y}}{\partial \bm{x}} \right)^T \frac{\partial z}{\partial \bm{y}}
$$