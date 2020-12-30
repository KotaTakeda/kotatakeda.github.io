---
layout: post
title: "Random ODE"
date: 2020-12-30 12:06:00  +0900
dir: /math/
tags: 'スペクトル理論'
---

### 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [まとめ](#まとめ)
- [参考](#参考)

### Key word
- Hermite展開，Galerkin法
- 放射能半減，調和振動子

### はじめに
ODEの初期条件や係数が不確実な場合であるRandom ODE[^random_ode]について考えます．
Hermite展開とGalerkin近似による数値解法を紹介します．

### pdf
[詳細はこちら](/math/pdf/chapter12.pdf)
<!-- TODO: pdfに図を加える -->

### まとめ
Random ODEの数値解法と計算結果を示しました．Hermite展開により乱数を発生させずにRandomな現象を扱うことができる．

### 参考
- Timothy John Sullivan. *Introduction to uncertainty quantification*, Springer, 2015

### 注意
[^random_ode]: 用語として確率微分方程式(Stochastic ODE)とは区別されるべきです．
