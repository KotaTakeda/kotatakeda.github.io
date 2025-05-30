---
layout: post
title: "逆行列の平方根"
date: 2025-05-30 20:00 +0900
dir: /math/
tags: ["データ同化", "線形代数", "固有値分解"]
description: "逆行列の平方根の計算の特殊な場合"
---

## 定理
$v \in \mathbb{R}^n$ に対して，$A = I_n + vv^T$ という形をしているとき，逆行列の平方根は
$$
  A^{-\frac{1}{2}} = I_n - \left(1 - \frac{1}{\sqrt{1 + ||v||^2}}\right) \frac{vv^T}{||v||^2}
$$
と書ける．

詳細は[線形作用素のPDF](/math/pdf/linear_operator.pdf)

## 応用
データ同化の論文[1]を読んでいるときに，これを使っていると思われる変形が出てきた．
観測空間が1次元の場合で，ETKFの変換行列の表示を簡略化するときに必要．

[1] C. González-Tokman and B. R. Hunt, “Ensemble data assimilation for hyperbolic systems,” Physica D: Nonlinear Phenomena, vol. 243, no. 1, pp. 128–142, Jan. 2013, doi: 10.1016/j.physd.2012.10.005.


## 関連
- [Kalman filter関連のPDF](/math/pdf/kalman_filter.pdf)
