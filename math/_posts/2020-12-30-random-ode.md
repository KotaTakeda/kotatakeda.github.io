---
layout: post
title: "Random ODE"
description: "初期条件が不確実な(Uncertain)常微分方程式の数値計算例"
date: 2020-12-30 12:06:00  +0900
dir: /math/
tags: ['スペクトル理論', 'UQ']
---

### 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [放射能半減](#放射能半減)
- [pdf](#pdf)
- [まとめ](#まとめ)
- [参考](#参考)

### Key word
- Hermite展開，Galerkin法
- 放射能半減，調和振動子

### はじめに
ODEの初期条件や係数が不確実な場合にはそれを方程式に盛り込む必要があります．
ここでは初期条件や定数係数が確率変数であるODEをRandom ODE[^random_ode]と呼び，それについて考えます．
Hermite展開とGalerkin近似によるRandom ODEの数値解法を紹介します[^stochatic_sol]．
[Hermite展開](/math/2020/11/01/winner-hermite-expansion.html)に基づいています．

### 放射能半減

#### 方程式
$ \lambda, b > 0 $ に対して以下のような単純な放射能半減の微分方程式を考える．

$ \dot{u}(t) = - \lambda u(t), \hspace{1em} u(0) = b $

$ \lambda, b $ が不確実な場合を考え，上記の方程式をRandom ODEとして捉えます．

ここでは $ \lambda, b $ がGaussianに従うとして，
- Hermite展開により確率変数の「成分表示」ができ
- さらにGalerkin productにより確率変数の「成分表示による積」を定義します．

#### 解
展開を有限項で打ち切ることにより数値的に解けます．
数値解のHermite展開係数から解のモーメントを計算することができます．

![Random Radioactive](/assets/img/math/radioactive_random_ode.png)

#### 調和振動子の結果画像
![Random Harmonic Oscillator](/assets/img/math/harmonic_oscillator_random_ode.png)

### pdf
もう一つの例(調和振動子)と詳細な説明は以下のpdfにあります．

[詳細はこちら](/math/pdf/chapter12.pdf)

### まとめ
- Random ODEの数値解法と計算結果を示しました．
- Hermite展開により乱数を発生させずにRandomな現象を扱うことができます．
- Galerkin productにより確率変数の積にも対応できます．

### 参考
- Timothy John Sullivan. *Introduction to uncertainty quantification*, Springer, 2015

### 注意
[^random_ode]: 用語として確率微分方程式(Stochastic ODE)とは区別されるべきです．
[^stochatic_sol]: 確率微分方程式を解くわけではないので確率積分は行わず，したがってdeterministicに解けます．
